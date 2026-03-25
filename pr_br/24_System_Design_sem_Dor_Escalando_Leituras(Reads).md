# 🚀 System Design sem Dor: Escalando Leituras (Reads)

Se você já caiu naquele cenário clássico onde sua aplicação começa a sofrer porque *todo mundo só quer ler dados*, mas quase ninguém escreve… parabéns, você chegou num dos problemas mais comuns de **system design moderno**.

Hoje vamos falar de um tema que aparece em praticamente qualquer sistema real:

## 📖 1. Scaling Reads (Escalar Leituras)

### 🤔 O Problema

Em muitos sistemas, o padrão é mais ou menos assim:

* 95% das operações são **leitura**
* 5% são **escrita**

Exemplos clássicos:

* Feed de rede social
* Perfil de usuário
* Catálogo de produtos
* Encurtador de URL

Ou seja: **todo mundo lê o tempo todo**, mas poucos escrevem.

👉 Resultado: seu banco começa a sofrer… e escalar só “na força bruta” (vertical) não resolve.

---

## 🛠️ Soluções Clássicas (e que realmente funcionam)

### ⚡ 1. Cache (Redis / Memcached)

A ideia aqui é simples e poderosa:

> “Se já pediram isso antes, por que buscar de novo?”

Você guarda o resultado em memória (super rápida) e evita bater no banco toda hora.

#### 🔥 Benefícios:

* Redução brutal de latência
* Menos carga no banco
* Respostas muito mais rápidas

#### ⚠️ Problemas:

* Cache pode ficar **desatualizado**
* Invalidação de cache é um dos problemas mais chatos da computação 😅

#### 💡 Dica prática:

Comece simples:

* TTL (tempo de expiração)
* Cache de leitura (read-through ou lazy loading)

---

### 🪞 2. Read Replicas

Aqui a ideia é escalar horizontalmente o banco:

* 1 banco principal (**write**)
* N réplicas (**read**)

Fluxo:

* Escritas vão para o **master**
* Leituras são distribuídas entre as **réplicas**

#### 🔥 Benefícios:

* Escala leituras facilmente
* Mantém consistência razoável

#### ⚠️ Problemas:

* **Eventual consistency** (replicação não é instantânea)
* Pode ler dado “antigo” por alguns milissegundos/segundos

#### 💡 Quando usar:

* Sistemas com MUITA leitura
* Quando pequenos delays de consistência são aceitáveis

---

### 🌍 3. CDN (CloudFront / Cloudflare)

Agora você joga o jogo em outro nível:

> “E se o dado nem precisasse chegar até minha aplicação?”

A CDN cacheia conteúdo **próximo do usuário** (edge).

#### 🔥 Benefícios:

* Latência global baixíssima
* Reduz carga na aplicação
* Escala praticamente infinita

#### ⚠️ Problemas:

* Cache distribuído (invalidação fica mais complexa)
* Não serve pra tudo (principalmente dados dinâmicos muito voláteis)

#### 💡 Use para:

* Imagens
* Assets (JS, CSS)
* APIs cacheáveis
* Conteúdo público

---

## ⚖️ Trade-offs (a parte que ninguém pode ignorar)

Quando você escala leitura, inevitavelmente entra nesse mundo:

### 🧨 Eventual Consistency

Você aceita que:

> “Nem todo mundo vai ver o dado mais atualizado imediatamente.”

E tá tudo bem… dependendo do sistema.

---

### 🧩 Cache Invalidation

A pergunta maldita:

> “Quando eu atualizo ou apago o cache?”

Estratégias comuns:

* TTL (expiração)
* Write-through
* Cache busting
* Versionamento de chave

---

## 🧠 Quando usar tudo isso?

Você provavelmente precisa dessas estratégias se estiver construindo:

* 📱 Feed de rede social
* 🔗 URL shortener
* 👤 Perfil de usuário
* 🛒 Catálogo de produtos
* 📊 Dashboards com muitas consultas

---

## 🧱 Resumo Mental (pra levar pra vida)

Se leituras estão explodindo:

1. **Primeiro:** adiciona cache
2. **Depois:** cria read replicas
3. **Por fim:** usa CDN quando fizer sentido

👉 E sempre aceite: **consistência perfeita custa caro**

---

## 🚀 Conclusão

Escalar leitura não é só sobre performance.

É sobre tomar decisões conscientes:

* Onde posso aceitar inconsistência?
* O que pode ser cacheado?
* O que realmente precisa ser real-time?

No fim das contas, system design é isso:

> Trocar complexidade por escala — de forma inteligente.

---
