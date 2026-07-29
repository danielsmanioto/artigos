# 🆘 Claude Code - Guia de Sobrevivência

> SOS: Situações de Crise + Soluções Rápidas com Claude Code

---

## 🚨 EMERGÊNCIAS

### ❌ Não entendo esse código

```bash
# 1. Quick check
/explain src/arquivo.ts

# 2. Mais específico (linhas)
/explain src/arquivo.ts:20-50

# 3. Ainda não entendeu?
# Mensagem normal: "Explique passo a passo essa função"

# 4. Se tá muito complicado
# Mensagem: "Refatore este código para ser mais legível"
```

---

### ❌ Código tá uma bagunça

```bash
# 1. Analisar completamente
/analyze

# 2. Se tá muito confuso
# Mensagem: "Por favor, refatore e organize este código"

# 3. Revisar depois
/code-review

# 4. Se tá tudo errado, desfazer
# Ctrl+Z (undo) ou volta o arquivo anterior
```

---

### ❌ Preciso fazer código mas não sei como

```bash
# 1. Procurar padrão similar
/find "*.tsx"  # Procura componentes React
/grep "useEffect"  # Procura hooks

# 2. Entender padrão
/explain src/componente_similar.tsx

# 3. Pedir ajuda ao Claude
# Mensagem: "Crie um componente similar a este, mas para XYZ"

# 4. Revisar resultado
/code-review
```

---

### ❌ Tá lento demais, preciso de velocidade

```bash
# Ativar modo rápido
/fast

# Agora Claude responde mais rápido
# Use para:
✓ Tarefas simples
✓ Exploração rápida
✓ Respostas rápidas

# Desativar depois:
/fast (toggle)
```

---

### ❌ Tenho um bug e não consigo achar

```bash
# 1. Procurar por pistas
/grep "erro"
/grep "null"
/grep "undefined"

# 2. Entender arquivo suspeito
/explain src/buggy-file.ts

# 3. Pedir ao Claude:
# Mensagem: "Encontre o bug neste código"

# 4. Revisar solução
/code-review
```

---

### ❌ Preciso revisar segurança

```bash
# 1. Análise de segurança
/security-review

# 2. Procurar por problemas comuns
/grep "password"
/grep "token"
/grep "secret"
/grep "API_KEY"

# 3. Se encontrou algo:
# Mensagem: "Como resolver este problema de segurança?"
```

---

### ❌ Código muito grande, não sei por onde começa

```bash
# 1. Analisar projeto
/analyze

# 2. Explorar estrutura
/find .

# 3. Entender arquivo principal
/explain src/index.ts

# 4. Explorar componentes
/find "src/**/*.tsx"

# 5. Guardar contexto
/remember Stack: [seu stack aqui]
```

---

### ❌ Preciso fazer refatoração mas com cuidado

```bash
# 1. Entender código atual
/explain src/old-file.ts

# 2. Pedir refatoração detalhada
# Mensagem: "Refatore este arquivo para usar padrão XYZ, mantendo mesma funcionalidade"

# 3. Revisar mudanças
/code-review

# 4. Se tudo bem, testar
! npm test
```

---

### ❌ Não sei que tecnologia usar

```bash
# 1. Guardar contexto
/remember Stack atual: [tecnologias existentes]

# 2. Pedir sugestão
# Mensagem: "Para fazer XYZ, qual tecnologia usar? Considerando nosso stack"

# 3. Claude sugere algo
# Você aprova ou quer alternativa
```

---

## 🔍 INVESTIGAÇÃO

### Qual é o padrão deste projeto?

```bash
# 1. Explorar estrutura
/find .

# 2. Ver padrões de nomeclatura
/grep "export"
/grep "import"

# 3. Entender um arquivo exemplo
/explain src/componente_principal.tsx

# 4. Guardar padrão
/remember Padrão: [descrição do padrão encontrado]
```

---

### Como essa função funciona?

```bash
# 1. Explicar função
/explain src/arquivo.ts

# 2. Se muito grande, especificar:
/explain src/arquivo.ts:10-30

# 3. Ver onde é usada
/grep "nome_da_funcao"

# 4. Entender chamadas
# Procure cada chamada com /explain
```

---

### Qual é melhor prática para fazer isso?

```bash
# 1. Procurar exemplos no projeto
/grep "padrão"
/find "*.exemplo.*"

# 2. Entender exemplo
/explain src/exemplo.ts

# 3. Guardar aprendizado
/remember Melhor prática: [descrição]
```

---

### Que mudanças foram feitas?

```bash
# Mensagem ao Claude:
# "Resuma as mudanças que você fez neste código"

# Ou:
/code-review  # Mostra mudanças e análise
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
/code-review
```

---

### Preciso escrever testes

```bash
# 1. Entender o que testar
/explain src/funcao.ts

# 2. Pedir testes ao Claude
# Mensagem: "Escreva testes abrangentes para esta função"

# 3. Revisar testes
/code-review

# 4. Rodar
! npm test
```

---

### Cobertura de testes baixa

```bash
# 1. Identificar áreas sem teste
# Mensagem: "Qual parte deste código não tem testes?"

# 2. Claude sugere
/analyze  # Pode mostrar gaps

# 3. Pedir testes para gaps
# Mensagem: "Escreva testes para as partes não cobertas"

# 4. Adicionar testes
# Claude adiciona
```

---

## 📝 DOCUMENTAÇÃO

### Código não tem documentação

```bash
# 1. Pedir documentação
# Mensagem: "Adicione JSDoc/comentários a este código"

# 2. Revisar
/code-review

# 3. Se quer mais detalhado
# Mensagem: "Adicione exemplos de uso na documentação"
```

---

### Preciso entender o projeto

```bash
# 1. Análise completa
/analyze

# 2. Explorar estrutura
/find .

# 3. Guardar compreensão
/remember Projeto: [descrição do que entendi]

# 4. Ler documentação existente
/find "*.md"
/explain README.md
```

---

## ⚡ CLAUDE CODE ESPECÍFICO

### Não lembro um comando

```bash
# Opção 1: Ver ajuda
/help

# Opção 2: Procurar no cheat sheet
# Abra: cheat_sheet.md

# Opção 3: Procurar no guia completo
# Abra: comandos_claude_code.md
```

---

### Preciso de contexto para Claude

```bash
# Guardar informação importante
/remember [informação importante]

# Exemplos:
/remember Stack: Node 18 + TypeScript + React 18
/remember Padrão: Usar composition over inheritance
/remember Restrição: Sem console.log em produção

# Claude referencia automaticamente depois
```

---

### Estou explorando novo projeto

```bash
# 1. Análise rápida
/analyze

# 2. Explorar arquivos
/find .
/find "src/**/*.ts"

# 3. Entender entry point
/explain src/index.ts

# 4. Guardar stack
/remember Stack: [tecnologias encontradas]

# 5. Explorar componentes principais
/find "src/components"
/explain src/components/Main.tsx
```

---

### Preciso refatorar mas sem quebrar

```bash
# 1. Entender código
/explain src/arquivo.ts

# 2. Pedir refatoração "safe"
# Mensagem: "Refatore para ser mais modular, mantendo testes passando"

# 3. Revisar mudanças
/code-review

# 4. Testar
! npm test

# 5. Se quebrou, voltar
# Ctrl+Z (undo)
```

---

### Integração com ferramentas

```bash
# 1. Executar testes
! npm test

# 2. Build
! npm run build

# 3. Lint
! npm run lint

# 4. Custom commands
! npm run <seu-comando>

# 5. Shell commands
! ls
! pwd
! echo "algo"
```

---

## 🎯 CHECKLIST RÁPIDO

### Antes de Commit
```
☐ ! npm test          Testes passam?
☐ ! npm run lint      Lint tá ok?
☐ /code-review        Claude aprova?
☐ /security-review    Sem riscos?
☐ Tudo pronto!
```

### Antes de Push
```
☐ /code-review        Review final
☐ /security-review    Security check
☐ ! npm test          Todos testes passam
☐ ! npm audit         Sem vulnerabilidades
☐ Pronto para push!
```

### Antes de Deploy
```
☐ /code-review        Review completo
☐ /security-review    Security review final
☐ ! npm test          Todos os testes
☐ ! npm run build     Build funciona
☐ ! npm audit         Sem vulnerabilidades
☐ Deploy com confiança!
```

---

## 💡 ATALHOS ÚTEIS

### Criar aliases bash/zsh

```bash
# Claude Code
alias cc='/code-review'
alias cs='/security-review'
alias ce='/explain'
alias cg='/grep'
alias cf='/find'
alias ca='/analyze'
alias cr='/remember'

# Npm
alias t='npm test'
alias b='npm run build'
alias l='npm run lint'
alias a='npm audit'
```

---

## 🔧 COMANDOS MAIS USADOS

| Situação | Comando |
|----------|---------|
| Entender código | `/explain src/file.ts` |
| Revisar mudanças | `/code-review` |
| Revisar segurança | `/security-review` |
| Buscar padrão | `/grep "padrão"` |
| Buscar arquivo | `/find "*.tsx"` |
| Análise completa | `/analyze` |
| Guardar contexto | `/remember [info]` |
| Testes | `! npm test` |
| Build | `! npm run build` |
| Lint | `! npm run lint` |

---

## 🆘 ÚLTIMOS RECURSOS

### Não entendo o que Claude fez

```bash
# 1. Revisar código
/code-review

# 2. Pedir explicação
# Mensagem: "Por que você fez desta forma?"

# 3. Entender alternativas
# Mensagem: "Qual seria outra forma de fazer?"
```

---

### Código gerado tá muito diferente

```bash
# 1. Voltar
# Ctrl+Z (undo)

# 2. Pedir com mais detalhes
# Mensagem: "Faça isto mas mantendo a estrutura atual"

# 3. Revisar resultado
/code-review
```

---

### Claude tá gerando código ruim

```bash
# 1. Análise
/analyze

# 2. Revisar
/code-review

# 3. Pedir correção
# Mensagem: "Corrija estes problemas: [listar]"

# 4. Ou começar de novo
# Mensagem: "Ignore o código anterior, refaça do zero"
```

---

## 📝 SUA SITUAÇÃO NÃO TÁ AQUI?

```bash
# 1. Procure no guia completo
# Arquivo: comandos_claude_code.md

# 2. Use Claude mesmo!
# Mensagem: "Como faço para [sua situação]?"

# 3. Procure online
# Stack Overflow, GitHub Issues
```

---

## ⏱️ TEMPO DE RESOLUÇÃO

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
2. AVALIAR - /analyze, /code-review, /explain
3. PLANEJAR - Qual é a melhor solução?
4. AGIR - Peça ao Claude
5. REVISAR - /code-review a solução
6. TESTAR - ! npm test
7. CONFIRMAR - Funcionou?
8. RELAX - Respire fundo, foi!
```

---

## 🚀 LEMBRE-SE

```
✅ Sempre revise antes (/code-review)
✅ Use /security-review para dados sensíveis
✅ Teste antes de commit (! npm test)
✅ Guarde contexto com /remember
✅ Quando em dúvida, use /explain
✅ Quando confuso, use /analyze
✅ Quando desespero, use /code-review
✅ Quando muito desespero, use /help
```

---

## 📞 HOTLINE DE EMERGÊNCIA

```
Problema                        Solução Rápida
───────────────────────────────────────────────────
Não entendo código              /explain src/file.ts
Preciso revisar                 /code-review
Código tá errado                /code-review depois corrigir
Não sei como fazer              /explain similar + pedir novo
Tá muito lento                  /fast (ativar modo rápido)
Tá tudo quebrado                /analyze + /code-review
Preciso de ajuda                /help
Qual é o padrão?                /grep "padrão" + /explain
Preciso refatorar               /explain + pedir refactor + /code-review
Segurança?                      /security-review
Nada funcionando                😱 → /analyze → /code-review → pedindo ajuda
```

---

## 🎓 WORKFLOW RECOMENDADO

### Dia Normal
```
1. /remember [task do dia]
2. Editar código
3. /code-review
4. ! npm test
5. Se tudo ok, commit
6. Se erro, /explain + corrigir
```

### Novo Feature
```
1. /remember [descrição do feature]
2. /analyze (entender projeto)
3. /find (procurar padrão similar)
4. /explain (entender padrão)
5. Pedir: "Crie novo feature baseado nisto"
6. /code-review
7. ! npm test
```

### Refatoração
```
1. /explain (entender atual)
2. Pedir: "Refatore para XYZ"
3. /code-review
4. ! npm test
5. Se quebrou, /explain erro
6. Corrigir
```

### Review de PR
```
1. /review <URL> (se GitHub)
2. /code-review (análise local)
3. /security-review
4. Feedback ao autor
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

*Última atualização: 2024*

**Quando tudo falha:** Leia este guia de novo, mais lentamente. 🧘
**Quando nada funciona:** Use `/analyze` + `/code-review`. ❤️
**Quando desespero total:** Peça ajuda ao Claude! 💬

---

**Happy Coding with Claude Code! 🚀**
