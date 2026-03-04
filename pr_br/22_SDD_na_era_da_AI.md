# SDD: A Arte de Especificar no Mundo do AI

> **TL;DR:** No mundo pós-LLM, quem sabe especificar bem entrega 10x mais rápido. Specification Driven Development não é burocracia — é superpoder.

---

## O problema que todo dev conhece

Você já recebeu aquela tarefa assim:

> "Cria uma tela de login."

Só isso. Sem detalhe, sem regra, sem exemplo. Você vai lá, codifica o que acha que é certo, aí vem o feedback:

> "Não era bem isso. Precisava bloquear após 5 tentativas, aceitar só e-mail corporativo, e ainda logar tudo no Datadog."

Retrabalho. Frustração. Reunião de alinhamento que deveria ter acontecido antes.

**SDD existe pra acabar com isso.**

---

## O que é Specification Driven Development?

É simples: **você escreve a especificação primeiro.** O código, os testes e a documentação derivam dela. A spec é a fonte da verdade — não o código, não o Confluence desatualizado, não a memória do dev sênior.

```
Abordagem tradicional:
Código → Documentação (que nunca ninguém escreve 😅)

SDD:
Especificação → Código → Testes → todos alinhados ✅
```

Parece óbvio, né? Mas a maioria dos times ainda não faz isso de forma consistente.

---

## Por que isso explodiu com AI?

Porque **LLMs são excepcionalmente bons em transformar spec em código.**

Antes do ChatGPT e afins, escrever spec parecia burocracia — você gastava tempo documentando quando podia estar codando. Agora a lógica inverteu:

```
Antes do LLM:  spec era burocracia, ninguém queria escrever
Depois do LLM: spec virou o trabalho principal do dev
```

Uma spec bem escrita hoje vira implementação em minutos. O dev que sabe especificar bem **entrega 10x mais rápido** — e com muito menos bug.

---

## Na prática: como é uma boa spec?

### Para uma função

```python
# ❌ Isso é prompt vago — resultado imprevisível
"cria uma função que valida email"

# ✅ Isso é spec — resultado previsível e testável
"""
FUNÇÃO: validar_email(email: str) -> dict

DESCRIÇÃO:
  Valida se um endereço de email é válido e seguro para uso.

ENTRADA:
  - email: string com o endereço a validar

SAÍDA (dict):
  - valido: bool
  - motivo: str (explica o porquê, se inválido)
  - dominio: str (domínio extraído, se válido)

REGRAS:
  - Deve conter exatamente um @
  - Domínio deve ter pelo menos um ponto
  - Não aceitar emails temporários (mailinator, guerrillamail, etc.)
  - Não aceitar strings vazias ou None

EXEMPLOS:
  validar_email("daniel@gmail.com")
  → {"valido": True, "motivo": None, "dominio": "gmail.com"}

  validar_email("nao-é-um-email")
  → {"valido": False, "motivo": "Falta o @", "dominio": None}

  validar_email("fake@mailinator.com")
  → {"valido": False, "motivo": "Domínio temporário não permitido", "dominio": None}
"""
```

Essa spec entregue pro LLM gera código **correto, testável e documentado** de primeira.

---

### Para uma feature completa

```markdown
## FEATURE: Autenticação JWT

### Contexto
API REST em FastAPI. Usuários precisam se autenticar
para acessar endpoints protegidos.

### Endpoints

POST /auth/login
  - Input:  { email: string, senha: string }
  - Output sucesso (200): { token: string, expira_em: int }
  - Output erro    (401): { erro: "Credenciais inválidas" }
  - Token expira em 24h

POST /auth/refresh
  - Header: Authorization: Bearer <token>
  - Output sucesso (200): { token: string, expira_em: int }
  - Output erro    (401): token expirado ou inválido

### Regras de negócio
  - Senha: mínimo 8 caracteres
  - Máximo 5 tentativas de login → bloqueia por 15 minutos
  - Logar todas as tentativas (sucesso e falha)

### Fora do escopo
  - Cadastro de usuários (feature separada)
  - OAuth / login social
```

Essa spec alimenta o LLM e ele gera: código, testes unitários, testes de integração e documentação — **tudo alinhado com as regras de negócio**.

---

## SDD + TDD + AI = combo imbatível

SDD casa perfeitamente com TDD quando você tem LLM no processo:

```
1. Você escreve a spec
         ↓
2. LLM gera os testes a partir da spec
         ↓
3. LLM gera o código pra passar nos testes
         ↓
4. Você revisa e valida
         ↓
5. Spec, código e testes sempre sincronizados 🎯
```

Da spec de autenticação acima, o LLM gera automaticamente:

```python
def test_login_sucesso():
    response = client.post("/auth/login", json={
        "email": "daniel@gmail.com",
        "senha": "senha123"
    })
    assert response.status_code == 200
    assert "token" in response.json()


def test_login_credenciais_invalidas():
    response = client.post("/auth/login", json={
        "email": "daniel@gmail.com",
        "senha": "errada"
    })
    assert response.status_code == 401
    assert response.json()["erro"] == "Credenciais inválidas"


def test_bloqueio_apos_5_tentativas():
    for _ in range(5):
        client.post("/auth/login", json={
            "email": "daniel@gmail.com",
            "senha": "errada"
        })

    response = client.post("/auth/login", json={
        "email": "daniel@gmail.com",
        "senha": "certa123"
    })
    assert response.status_code == 429  # Too Many Requests — bloqueado ✅
```

Sem spec detalhada, esses edge cases nunca virariam teste. Com spec, são automáticos.

---

## A estrutura de uma boa spec

Independente do tamanho da task, uma spec completa tem:

```markdown
## NOME DA FEATURE / FUNÇÃO

### Contexto
Por que isso existe? Qual problema resolve?

### Comportamento esperado
O que faz, passo a passo.

### Inputs e Outputs
Tipos, formatos, exemplos concretos.

### Regras de negócio
Validações, restrições, edge cases.

### Exemplos
Casos felizes + casos de erro.

### Fora do escopo
O que explicitamente NÃO faz (evita scope creep).
```

A seção **"Fora do escopo"** é subestimada e é uma das mais importantes. Ela evita que o LLM — e o time — scope creep sem perceber.

---

## SDD no fluxo do time moderno

Com AI no processo, o fluxo de um time eficiente hoje é:

```
PO / Dev Sênior   →  escreve a spec
       ↓
LLM               →  gera código + testes
       ↓
Dev               →  revisa, ajusta, valida
       ↓
CI/CD             →  roda os testes (gerados da spec)
       ↓
Produção 🚀
```

O dev para de ser **digitador de código** e vira **arquiteto de especificações**. É uma mudança de mentalidade — e os times que fizeram essa transição estão entregando muito mais.

---

## O erro mais comum: confundir spec com comentário

```python
# ❌ Isso NÃO é spec — é comentário vago
# valida o usuário
def validar_usuario(user):
    ...

# ✅ Spec de verdade define comportamento, não implementação
# Veja o exemplo completo de validar_email acima ☝️
```

Spec fala **o quê** e **por quê**.  
Código fala **como**.

São camadas diferentes. Misturar as duas é onde a maioria erra.

---

## Benefícios reais no dia a dia

**Menos retrabalho** — alinhamento acontece na spec, antes do código existir.

**AI gera código melhor** — LLM com spec detalhada erra muito menos e alucina menos.

**Testes naturais** — spec bem escrita já define os casos de teste automaticamente.

**Onboarding mais rápido** — dev novo lê a spec e entende o sistema sem precisar perguntar tudo.

**Documentação viva** — a spec IS a documentação. Sem doc desatualizado.

**Estimativas mais precisas** — spec detalhada = você sabe o tamanho real da task antes de codar.

---

## Quando a spec é grande demais?

Se sua spec ficou enorme, é sinal de que a feature é grande demais — não que a spec está errada.

Quebre em partes menores. Spec menor → entrega menor → feedback mais rápido → menos retrabalho.

```
❌ Spec de 10 páginas pra feature gigante
✅ 5 specs de 2 páginas pra 5 features menores
```

---

## Conclusão

SDD não é processo chato de empresa grande. É uma **habilidade técnica** que diferencia devs na era do AI.

Quem sabe especificar bem:
- Usa LLMs com muito mais eficiência
- Entrega código mais correto de primeira
- Reduz drasticamente o retrabalho
- Comunica melhor com o time e com stakeholders

No fim, o dev que vai se destacar não é o que digita código mais rápido — é o que **pensa e especifica melhor**.

E aí, sua próxima task começa com uma spec? 🎯

---

*Escrito com ajuda do Claude Sonnet 4.6 — que, claro, foi alimentado com uma spec bem escrita antes de gerar este artigo.*
