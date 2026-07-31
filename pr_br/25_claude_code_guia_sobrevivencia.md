# 🆘 Claude Code - Guia de Sobrevivência

> Um guia rápido com comandos, atalhos e recursos que realmente existem no Claude Code para uso diário no desenvolvimento.

---

## 🚀 COMEÇAR AQUI

### ❌ Primeiro acesso em um projeto?
```bash
# 1. Inicialize o projeto
/init
# Cria CLAUDE.md para Claude entender melhor o projeto
# Faça isso UMA VEZ por repositório
```

---

### ❌ Não entendo esse código?
```bash
# 1. Referencie o arquivo
@src/arquivo.ts
# 2. Peça explicação em mensagem normal (não existe comando /explain)
# "Explique passo a passo essa função"
# "Como funciona este método?"
# 3. Se quiser focar em uma parte
# "Explique as linhas 20-50 deste arquivo"
```

---

### ❌ Código tá uma bagunça?
```bash
# 1. Peça refatoração
# Mensagem: "Refatore este código para ser mais legível"
# 2. Revisar mudanças
/review
# 3. Se tá muito ruim, voltar
# Esc + Esc (abre o histórico de mensagens/checkpoints)
```

---

### ❌ Tenho um bug e não consigo achar?
```bash
# 1. Referencie os arquivos suspeitos
@src/buggy-file.ts
# 2. Descreva o problema
# "Encontre o bug: quando o usuário clica em X, acontece Y"
# 3. Revisar solução
/review
```

---

### ❌ Preciso revisar segurança?
```bash
# 1. Análise de segurança
/security-review
# Procura por:
# - SQL Injection
# - XSS
# - Secrets expostos
# - Problemas de autenticação
# - Más práticas de segurança
```

---

### ❌ Novo projeto, não sei por onde começar?
```bash
# 1. Inicialize
/init
# 2. Referencie arquivos principais
@README.md
@package.json
@src/
# 3. Peça ao Claude
# "Explique a estrutura deste projeto"
# "Qual é a arquitetura utilizada?"
# 4. Guardar contexto
/memory
# Edita o CLAUDE.md — salve o que aprendeu
```

---

### ❌ Refatoração é arriscada?
```bash
# 1. Antes de começar
/review
# 2. Execute os testes
! npm test
# 3. Peça refatoração mantendo funcionalidade
# "Refatore para usar padrão XYZ, testes devem passar"
# 4. Revisar novamente
/review
# 5. Testar
! npm test
# 6. Se quebrou, voltar
# Esc + Esc (histórico) ou ! git checkout -- .
```

---

## 🔍 EXPLORAÇÃO & CONTEXTO

### Qual é o padrão deste projeto?
```bash
# 1. Referencie arquivos principais
@src/
@package.json
@README.md
# 2. Peça ao Claude
# "Qual é o padrão de arquitetura?"
# "Como os componentes estão organizados?"
# 3. Guardar aprendizado
/memory
# Edita o CLAUDE.md com o padrão identificado
```

---

### Como essa função funciona?
```bash
# 1. Referencie o arquivo
@src/arquivo.ts
# 2. Peça explicação em mensagem normal
# "Explique passo a passo como essa função funciona"
# "Qual é o propósito dessa classe?"
```

---

### Que mudanças foram feitas?
```bash
# 1. Ver diferenças via git
! git diff
# 2. Ou revisar com o Claude
/review
# /review analisa e comenta; ! git diff mostra o diff cru
```

---

### Adicionar contexto permanente
```bash
# Abre o CLAUDE.md para edição
/memory
# Exemplos do que colocar lá:
# Stack: Node 18 + TypeScript + React 18
# Padrão: Usar composition over inheritance
# Restrição: Sem console.log em produção
```

---

### Sessão ficou muito longa / lenta?
```bash
# 1. Ver quanto do contexto já foi usado
/context
# 2. Compactar o histórico (resume o que já foi dito, libera espaço)
/compact
# 3. Se não precisa mais do histórico, limpar de vez
/clear
```

---

### Quero rodar algo em background e continuar trabalhando
```bash
# Manda a sessão/tarefa atual pra rodar em background
/bg
# Lista o que está rodando em paralelo (subagents, tarefas em background)
/tasks
```

---

### Preciso voltar numa sessão anterior
```bash
# Abre um seletor com as sessões recentes
/resume
# Ou já direto pra uma sessão específica
/resume <nome-ou-id-da-sessão>
```

---

### Quero trocar de modelo (mais rápido/barato ou mais potente)
```bash
/model
# Abre o seletor de modelo (ex: alternar para um modelo mais leve
# em tarefas simples e economizar uso)
```

---

### Quanto já usei do meu limite?
```bash
/usage
# Mostra % usado da sua cota (sessão de 5h e limite semanal)
# e quando o limite reseta
```

---

### Preciso conectar/gerenciar um MCP
```bash
/mcp
# Lista, conecta e gerencia servidores MCP disponíveis na sessão
```

---

## 🧪 TESTES & VALIDAÇÃO

### Testes estão falhando
```bash
# 1. Rodar testes
! npm test
# 2. Ver qual falhou
# Ler mensagem de erro
# 3. Pedir ajuda
# Mensagem: "Por que este teste está falhando? [erro aqui]"
# 4. Revisar solução
/review
```

---

### Preciso escrever testes
```bash
# 1. Entender o que testar
@src/funcao.ts
# "Explique o que esta função faz"
# 2. Pedir testes ao Claude
# Mensagem: "Escreva testes abrangentes para esta função"
# 3. Revisar testes
/review
# 4. Rodar
! npm test
```

---

### Cobertura de testes baixa
```bash
# 1. Identificar áreas sem teste
# Mensagem: "Qual parte deste código não tem testes?"
# 2. Pedir testes para os gaps
# Mensagem: "Escreva testes para as partes não cobertas"
# 3. Revisar e rodar
/review
! npm test
```

---

## 📝 DOCUMENTAÇÃO

### Código não tem documentação
```bash
# 1. Pedir documentação
# Mensagem: "Adicione JSDoc/comentários a este código"
# 2. Revisar
/review
# 3. Se quer mais detalhado
# Mensagem: "Adicione exemplos de uso na documentação"
```

---

### Preciso entender o projeto
```bash
# 1. Referencie os arquivos principais
@README.md
@package.json
@src/
# 2. Peça um resumo
# Mensagem: "Explique a estrutura e arquitetura deste projeto"
# 3. Guardar compreensão
/memory
# Salva o entendimento no CLAUDE.md pra próxima sessão já vir com o contexto
```

---

## ⚡ CLAUDE CODE ESPECÍFICO

### Não lembro um comando
```bash
# Opção 1: Ver ajuda
/help
# Opção 2: Digite "/" sozinho pra ver a lista completa de comandos
/
# Opção 3: Procurar no seu guia
# Abra: guia-sobrevivencia-claude-code.md
```

---

### Preciso de contexto para Claude lembrar depois
```bash
# Edita o CLAUDE.md do projeto (não existe /remember — é /memory)
/memory
# Exemplos:
# Stack: Node 18 + TypeScript + React 18
# Padrão: Usar composition over inheritance
# Restrição: Sem console.log em produção
# Claude lê o CLAUDE.md automaticamente nas próximas sessões
```

---

### Estou explorando novo projeto
```bash
# 1. Inicializa
/init
# 2. Referencia arquivos
@README.md
@package.json
@src/
# 3. Entender entry point
@src/index.ts
# "Explique o que este arquivo faz"
# 4. Guardar stack
/memory
# 5. Explorar componentes principais
@src/components/
```

---

### Preciso refatorar mas sem quebrar
```bash
# 1. Entender código
@src/arquivo.ts
# "Explique este arquivo"
# 2. Pedir refatoração "safe"
# Mensagem: "Refatore para ser mais modular, mantendo testes passando"
# 3. Revisar mudanças
/review
# 4. Testar
! npm test
# 5. Se quebrou, voltar
# Esc + Esc (histórico/checkpoints)
```

---

### Integração com ferramentas
```bash
# "!" no início roda comando de shell direto
! npm test
! npm run build
! npm run lint
! npm run <seu-comando>
! ls
! pwd
! git status
```

---

## 🎯 CHECKLIST RÁPIDO

### Antes de Commit
```
☐ ! npm test          Testes passam?
☐ ! npm run lint      Lint tá ok?
☐ /review             Claude aprova?
☐ /security-review    Sem riscos?
☐ Tudo pronto!
```

### Antes de Push
```
☐ /review             Review final
☐ /security-review    Security check
☐ ! npm test           Todos testes passam
☐ ! npm audit           Sem vulnerabilidades
☐ Pronto para push!
```

### Antes de Deploy
```
☐ /review             Review completo
☐ /security-review    Security review final
☐ ! npm test           Todos os testes
☐ ! npm run build      Build funciona
☐ ! npm audit           Sem vulnerabilidades
☐ Deploy com confiança!
```

---

## 💡 ATALHOS ÚTEIS

### Criar aliases bash/zsh
```bash
# Npm (não dá pra criar alias pra slash command do Claude Code,
# eles só funcionam dentro da sessão do Claude Code)
alias t='npm test'
alias b='npm run build'
alias l='npm run lint'
alias a='npm audit'
```

---

## 🔧 COMANDOS MAIS USADOS

| Situação | Comando |
|----------|---------|
| Iniciar projeto | `/init` |
| Revisar mudanças | `/review` |
| Revisar segurança | `/security-review` |
| Editar memória do projeto | `/memory` |
| Ver uso/contexto | `/context` |
| Compactar histórico | `/compact` |
| Limpar histórico | `/clear` |
| Ver limite de uso | `/usage` |
| Trocar de modelo | `/model` |
| Gerenciar MCP | `/mcp` |
| Rodar em background | `/bg` |
| Ver tarefas em andamento | `/tasks` |
| Retomar sessão | `/resume` |
| Rodar comando de shell | `! npm test` |
| Ver ajuda | `/help` |

---

## 🆘 ÚLTIMOS RECURSOS

### Não entendo o que Claude fez
```bash
# 1. Revisar código
/review
# 2. Pedir explicação
# Mensagem: "Por que você fez desta forma?"
# 3. Entender alternativas
# Mensagem: "Qual seria outra forma de fazer?"
```

---

### Código gerado tá muito diferente do esperado
```bash
# 1. Voltar
# Esc + Esc (abre o histórico e permite voltar a um ponto anterior)
# 2. Pedir com mais detalhes
# Mensagem: "Faça isto mas mantendo a estrutura atual"
# 3. Revisar resultado
/review
```

---

### Claude tá gerando código ruim
```bash
# 1. Revisar
/review
# 2. Pedir correção
# Mensagem: "Corrija estes problemas: [listar]"
# 3. Ou começar de novo
# Mensagem: "Ignore o código anterior, refaça do zero"
```

---

## 📝 SUA SITUAÇÃO NÃO TÁ AQUI?
```bash
# 1. Procure no seu guia completo (se tiver um mais detalhado)
# 2. Use Claude mesmo!
# Mensagem: "Como faço para [sua situação]?"
# 3. Procure na documentação oficial
# code.claude.com/docs
# 4. Procure online
# Stack Overflow, GitHub Issues
```

---

## ⏱️ TEMPO DE RESOLUÇÃO (estimativa)

| Problema | Tempo | Dificuldade |
|----------|-------|------------|
| Não entendo código | 2 min | ⭐ Fácil |
| Revisar código | 3 min | ⭐ Fácil |
| Encontrar padrão | 5 min | ⭐⭐ Normal |
| Refatorar seguro | 10 min | ⭐⭐ Normal |
| Encontrar bug | 15 min | ⭐⭐⭐ Difícil |
| Redesenhar arquitetura | 30 min | ⭐⭐⭐ Difícil |

---

## 🎯 REGRA DE OURO
```
1. PARAR - Não piore a situação
2. AVALIAR - /review, referenciar arquivos com @, perguntar
3. PLANEJAR - Qual é a melhor solução?
4. AGIR - Peça ao Claude
5. REVISAR - /review a solução
6. TESTAR - ! npm test
7. CONFIRMAR - Funcionou?
8. RELAX - Respire fundo, foi!
```

---

## 🚀 LEMBRE-SE
```
✅ Sempre revise antes (/review)
✅ Use /security-review para dados sensíveis
✅ Teste antes de commit (! npm test)
✅ Guarde contexto com /memory
✅ Sessão longa? /context pra ver, /compact pra economizar
✅ Perdido? Digite "/" sozinho pra ver todos os comandos
✅ Quando em dúvida, pergunte em linguagem natural
✅ Quando desespero, use /review
✅ Quando muito desespero, use /help
```

---

## 📞 HOTLINE DE EMERGÊNCIA
```
Problema                        Solução Rápida
───────────────────────────────────────────────────
Não entendo código              @arquivo + "explique este código"
Preciso revisar                 /review
Código tá errado                /review depois corrigir
Não sei como fazer              Perguntar em linguagem natural
Sessão lenta / contexto cheio   /context → /compact
Quero rodar em paralelo         /bg → /tasks
Perdi o fio da sessão           /resume
Preciso de ajuda                /help
Qual é o padrão?                @src/ + "qual é o padrão daqui?"
Preciso refatorar               @arquivo + pedir refactor + /review
Segurança?                      /security-review
Quanto já usei?                 /usage
Nada funcionando                😱 → /review → pedindo ajuda
```

---

## 🎓 WORKFLOW RECOMENDADO

### Dia Normal
```
1. Editar código
2. /review
3. ! npm test
4. Se tudo ok, commit
5. Se erro, pedir explicação + corrigir
```

### Novo Feature
```
1. @src/ (referenciar projeto, entender padrão existente)
2. Pedir: "Crie novo feature baseado neste padrão"
3. /review
4. ! npm test
```

### Refatoração
```
1. @arquivo (entender o atual)
2. Pedir: "Refatore para XYZ"
3. /review
4. ! npm test
5. Se quebrou, pedir explicação do erro
6. Corrigir
```

### Review de PR
```
1. /review (análise local das mudanças)
2. /security-review
3. Feedback ao autor
```

### Sessão longa que não acaba
```
1. /context (ver quanto sobrou)
2. /compact (resumir e liberar espaço)
3. Se travou mesmo, /clear e recomeçar com /memory já salvo
```

---

## 💪 VOCÊ CONSEGUE!

Lembre-se:
- Claude Code é seu parceiro
- Use os comandos certos
- Sempre revise antes
- Testes são seus amigos
- Quando tudo falha: `/help`

---

*Última atualização: julho de 2026*

**Quando tudo falha:** Leia este guia de novo, mais lentamente. 🧘
**Quando nada funciona:** Use `/review` + pedir ajuda em linguagem natural. ❤️
**Quando desespero total:** Peça ajuda ao Claude! 💬

---

**Happy Coding with Claude Code! 🚀**
