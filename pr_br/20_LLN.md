# LLMs para Devs: O que você precisa saber (sem enrolação)

> **TL;DR:** LLMs são modelos estatísticos gigantes que preveem tokens. Entender como eles funcionam por baixo do capô vai te fazer um dev muito melhor na hora de integrá-los.

---

## O que é um LLM, de verdade?

Esqueça a magia. Um **Large Language Model** é, na essência, uma função matemática absurdamente grande que recebe texto e devolve texto.

Por baixo do capô, ele opera com **tokens** — fragmentos de palavras. A frase `"Hello, world!"` vira algo como `[15496, 11, 995, 0]`. O modelo nunca lê letras, ele lê números.

O processo é:

```
texto de entrada → tokenização → embeddings → transformer layers → logits → sampling → token de saída
```

Repete isso token por token até terminar a resposta.

---

## Arquitetura: Transformer (rápido e direto)

Todo LLM moderno usa **Transformer** como base (paper original: *Attention is All You Need*, 2017 — vale a leitura).

Os pilares:

- **Self-Attention**: cada token "olha" para todos os outros e decide o quanto cada um importa pra ele. É o que dá contexto.
- **Feed-Forward Layers**: processa cada token individualmente depois da atenção.
- **Positional Encoding**: como o modelo sabe a ordem das palavras (ele processa tudo em paralelo, não sequencialmente).
- **Layer Normalization + Residual Connections**: estabilidade no treinamento.

Você empilha isso N vezes (GPT-4 tem ~96 camadas) e treina em escala absurda.

---

## Os modelos que você vai usar no dia a dia

### 🟢 OpenAI (GPT)

| Modelo | Quando usar |
|---|---|
| `gpt-4o` | Uso geral, multimodal (texto + imagem + áudio) |
| `gpt-4.1` | Foco em código, melhor raciocínio técnico |
| `o3` / `o4-mini` | Problemas que exigem raciocínio profundo (CoT interno) |

```python
from openai import OpenAI

client = OpenAI(api_key="sk-...")
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Explique ponteiros em C"}]
)
print(response.choices[0].message.content)
```

---

### 🔵 Google (Gemini)

| Modelo | Quando usar |
|---|---|
| `gemini-2.0-flash` | Rápido, barato, bom pra tarefas simples |
| `gemini-2.5-pro` | Tasks complexas, contexto longo (1M tokens!) |
| `gemini-2.5-flash` | Equilíbrio custo/performance |

Destaque: **contexto de 1 milhão de tokens** no Pro. Isso é um codebase inteiro dentro do prompt.

```python
import google.generativeai as genai

genai.configure(api_key="AIza...")
model = genai.GenerativeModel("gemini-2.5-pro")
response = model.generate_content("Revise esse código inteiro")
```

---

### 🟠 Anthropic (Claude)

| Modelo | Quando usar |
|---|---|
| `claude-haiku-4-5` | Rápido e barato, ideal pra pipelines de alto volume |
| `claude-sonnet-4-6` | Uso geral, ótimo equilíbrio (o que você tá usando agora 👋) |
| `claude-opus-4-6` | Tasks pesadas, raciocínio complexo, análises longas |

```python
import anthropic

client = anthropic.Anthropic(api_key="sk-ant-...")
message = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Refatore essa função"}]
)
print(message.content[0].text)
```

---

## Conceitos que você PRECISA dominar

### 1. Tokens e contexto

Cada modelo tem um **context window** — o limite de tokens que ele consegue processar de uma vez (entrada + saída).

- `gpt-4o`: 128k tokens ≈ ~96k palavras
- `gemini-2.5-pro`: 1M tokens ≈ codebase gigante
- `claude-sonnet-4-6`: 200k tokens

**Regra prática:** 1 token ≈ 0.75 palavras em inglês. Em português, um pouco mais.

Tokens custam dinheiro. Prompts gordos = bill gordo.

---

### 2. Temperature e Sampling

Controla o quão "criativo" (ou aleatório) o modelo é.

```python
# Determinístico: sempre a mesma resposta
response = client.chat.completions.create(
    model="gpt-4o",
    temperature=0.0,  # Sem aleatoriedade
    messages=[...]
)

# Criativo: respostas variadas
response = client.chat.completions.create(
    model="gpt-4o",
    temperature=0.9,  # Alta variação
    messages=[...]
)
```

**Quando usar o quê:**
- `temperature=0` → Extração de dados, SQL, código determinístico
- `temperature=0.3–0.7` → Assistentes, respostas gerais
- `temperature=0.8+` → Geração criativa, brainstorm

---

### 3. System Prompt

É o "contrato" com o modelo. Tudo que você colocar aqui define o comportamento base.

```python
messages = [
    {
        "role": "system",
        "content": """Você é um code reviewer sênior.
        - Sempre aponte problemas de segurança primeiro
        - Use exemplos de código nas sugestões
        - Seja direto, sem elogios desnecessários"""
    },
    {
        "role": "user",
        "content": "Revise esse endpoint de login"
    }
]
```

**Dicas:**
- Seja específico sobre o formato da saída
- Dê exemplos (few-shot) quando precisar de consistência
- Defina o que o modelo NÃO deve fazer

---

### 4. RAG (Retrieval-Augmented Generation)

O modelo não tem memória entre chamadas e tem conhecimento limitado ao treinamento. A solução é **injetar contexto relevante no prompt**.

```
Query do usuário
      ↓
Busca semântica no seu banco de dados (vectorDB)
      ↓
Recupera chunks relevantes
      ↓
Monta prompt: contexto + query
      ↓
LLM responde com base nos seus dados
```

Ferramentas populares: **LangChain**, **LlamaIndex**, **Haystack**

Bancos de vetores: **Pinecone**, **Weaviate**, **pgvector** (no Postgres!)

---

### 5. Function Calling / Tool Use

Permite que o modelo "chame funções" do seu sistema. Na prática, ele retorna JSON estruturado que você executa.

```python
tools = [
    {
        "type": "function",
        "function": {
            "name": "buscar_usuario",
            "description": "Busca dados de um usuário pelo ID",
            "parameters": {
                "type": "object",
                "properties": {
                    "user_id": {"type": "string"}
                },
                "required": ["user_id"]
            }
        }
    }
]

response = client.chat.completions.create(
    model="gpt-4o",
    tools=tools,
    messages=[{"role": "user", "content": "Me mostra os dados do usuário 42"}]
)

# Se o modelo quiser chamar a função:
# response.choices[0].message.tool_calls[0].function.name == "buscar_usuario"
```

Isso é a base de **AI Agents** — modelos que decidem quais ações tomar.

---

## Boas práticas de engenharia

### Não faça isso ❌

```python
# Prompt vago = resultado imprevisível
prompt = f"Analisa isso: {user_input}"
```

### Faça isso ✅

```python
# Prompt estruturado = resultado consistente
prompt = f"""Analise o seguinte código Python e retorne um JSON com:
- "bugs": lista de bugs encontrados
- "severity": "low" | "medium" | "high"  
- "suggestion": como corrigir

Código:
```python
{user_input}
```

Retorne APENAS o JSON, sem texto adicional."""
```

---

### Custo: fique de olho

| Modelo | Input (por 1M tokens) | Output (por 1M tokens) |
|---|---|---|
| GPT-4o | ~$2.50 | ~$10.00 |
| Claude Sonnet 4.6 | ~$3.00 | ~$15.00 |
| Gemini 2.0 Flash | ~$0.10 | ~$0.40 |
| GPT-4o mini | ~$0.15 | ~$0.60 |

**Dica:** Use modelos baratos (Flash, mini, Haiku) pra triagem e classificação. Modelos caros só quando realmente necessário.

---

### Streaming: UX muito melhor

```python
# Sem streaming: usuário espera tudo carregar
response = client.chat.completions.create(model="gpt-4o", messages=[...])

# Com streaming: resposta aparece token por token
stream = client.chat.completions.create(
    model="gpt-4o",
    messages=[...],
    stream=True
)

for chunk in stream:
    if chunk.choices[0].delta.content:
        print(chunk.choices[0].delta.content, end="", flush=True)
```

---

## Stack recomendada pra começar

```
Orquestração:    LangChain | LlamaIndex
Vector DB:       pgvector (já tem Postgres? usa esse) | Pinecone
Embeddings:      text-embedding-3-small (OpenAI) | muito mais barato que o large
Observabilidade: LangSmith | Langfuse | Helicone
Deploy:          FastAPI + qualquer cloud
```

---

## Erros comuns de dev iniciante em LLM

1. **Não versionar os prompts** → trata prompt como código, bota no git
2. **Ignorar rate limits** → implemente retry com exponential backoff
3. **Não logar as chamadas** → você vai precisar debugar, garanto
4. **Temperature=1 em tudo** → código + dados estruturados precisam de temperature baixa
5. **Context window infinito** → tem limite e custa caro, chunking é essencial
6. **Não validar output** → o modelo pode retornar JSON malformado, sempre valide

---

## Próximos passos

- 📖 **Papers essenciais:** Attention is All You Need (2017), GPT-3 (2020), Constitutional AI (2022)
- 🛠️ **Hands-on:** Anthropic Cookbook, OpenAI Cookbook (ambos no GitHub)
- 🎓 **Cursos:** fast.ai, DeepLearning.AI (Andrew Ng tem cursos específicos de LLM)
- 🔬 **Experimente:** Hugging Face tem modelos open-source pra rodar local (Llama, Mistral, Qwen)

---

*Escrito com ajuda do Claude Sonnet 4.6 — porque usar LLM pra falar de LLM é muito meta.*
