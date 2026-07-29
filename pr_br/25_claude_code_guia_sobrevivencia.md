# 🆘 Claude Code - Guia de Sobrevivência

> Um guia rápido com comandos, atalhos e recursos que realmente funcionam no Claude Code para uso diário no desenvolvimento.

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

# 2. Peça explicação em mensagem normal
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
# Esc + Esc (abre checkpoints)
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

### ❌ Novo projeto, não sei por onde começa?

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
# Salve o que aprendeu
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
# Esc + Esc (checkpoints)

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
# Salve o padrão identificado
```

---

### Como essa função funciona?

```bash
# 1. Referencie o arquivo
@src/arquivo.ts

# 2. Peça explicação
# "Explique passo a passo como essa função funciona"
# "Qual é o propósito dessa classe?"
```

---

### Que mudanças foram feitas?

```bash
# 1. Ver diferenças
/diff

# 2. Ou revisar
/review

# Ambos mostram tudo que foi modificado
```

---

### Adicionar contexto permanente

```bash
# Guardar informações importantes
/memory

# Exemplos:
# Stack: Node 18 + TypeScript + React 18
# Padrão: Usar composition over inheritance
# Restrição: Sem console.log em produção
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
