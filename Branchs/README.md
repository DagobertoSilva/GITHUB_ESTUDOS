# Git e GitHub: Trabalhando com Branches em Equipe

# Introdução

Quando trabalhamos em equipe, várias pessoas podem modificar o mesmo projeto simultaneamente.

Se todos alterassem diretamente os arquivos da branch principal, seria muito fácil:

- sobrescrever código de outros desenvolvedores;
- introduzir erros no sistema;
- dificultar a organização do projeto;
- causar conflitos constantes.

Para resolver esse problema utilizamos:

```txt
Branches
```

As branches permitem que cada desenvolvedor trabalhe de forma isolada, sem afetar o código principal do projeto.

---

# O que é uma Branch?

Uma branch é uma linha paralela de desenvolvimento.

Imagine que o projeto principal está funcionando corretamente e está na branch:

```txt
main
```

Você foi responsável por criar a tela de Login.

Em vez de alterar diretamente a `main`, você cria uma branch própria:

```txt
feature/tela-login
```

Representação:

```txt
main
  |
  |--------------------
                       \
                        feature/tela-login
```

Agora todas as alterações ficarão isoladas nessa branch.

---

# Por Que Utilizar Branches?

As branches oferecem diversas vantagens:

- Permitem trabalhar em equipe
- Evitam alterações diretas na branch principal
- Facilitam testes
- Melhoram a organização do projeto
- Permitem revisão de código
- Reduzem riscos de erros

---

# Fluxo de Trabalho Profissional

A maioria das empresas utiliza um fluxo semelhante ao seguinte:

```txt
main
   ↓
Criar branch
   ↓
Desenvolver
   ↓
Commit
   ↓
Push
   ↓
Pull Request
   ↓
Code Review
   ↓
Merge
   ↓
main
```

---

# Passo 1 — Clonar o Projeto

Primeiro precisamos baixar o projeto do GitHub.

```bash
git clone https://github.com/empresa/projeto.git
```

Entrando na pasta:

```bash
cd projeto
```

---

# O Que Acontece?

O Git cria uma cópia completa do projeto em sua máquina.

Representação:

```txt
GitHub
   ↓
Computador Local
```

---

# Passo 2 — Verificar a Branch Atual

Para verificar em qual branch estamos:

```bash
git branch
```

Saída:

```txt
* main
```

O símbolo:

```txt
*
```

indica a branch atual.

---

# Passo 3 — Atualizar a Branch Main

Antes de iniciar qualquer tarefa:

```bash
git pull origin main
```

Isso garante que você esteja trabalhando com a versão mais recente do projeto.

---

# Entendendo o Comando

```bash
git pull origin main
```

Significa:

| Parte | Significado |
|---------|---------|
| git | programa Git |
| pull | baixar alterações |
| origin | repositório remoto |
| main | branch principal |

---

# Passo 4 — Criar uma Branch

Agora podemos criar nossa funcionalidade.

Exemplo:

```bash
git checkout -b feature/tela-login
```

ou

```bash
git switch -c feature/tela-login
```

---

# O Que Significa?

```txt
feature/
```

indica:

```txt
nova funcionalidade
```

---

# Estrutura Após Criar a Branch

```txt
main
   \
    feature/tela-login
```

Agora você trabalha sem afetar a branch principal.

---

# Verificando as Branches

```bash
git branch
```

Saída:

```txt
main
* feature/tela-login
```

Observe que o símbolo:

```txt
*
```

agora está na nova branch.

---

# Trabalhando na Branch

Suponha que você esteja criando:

```txt
Tela de Login
```

Estrutura:

```txt
src/
 └── pages/
      └── Login.jsx
```

Você desenvolve normalmente.

---

# Salvando Alterações

Após modificar os arquivos:

```bash
git add .
```

---

# O Que Faz o git add?

Adiciona os arquivos para a área de preparação.

Representação:

```txt
Arquivos Alterados
        ↓
     git add
        ↓
 Staging Area
```

---

# Criando um Commit

Após adicionar:

```bash
git commit -m "Cria tela de login"
```

---

# O Que é um Commit?

Um commit é um ponto de salvamento do projeto.

Representação:

```txt
Commit 1
    ↓
Commit 2
    ↓
Commit 3
```

Cada commit representa uma mudança realizada.

---

# Boas Mensagens de Commit

Exemplos:

```bash
git commit -m "Cria tela de login"
```

```bash
git commit -m "Implementa formulário de cadastro"
```

```bash
git commit -m "Corrige erro na navbar"
```

Evite:

```bash
git commit -m "teste"
```

```bash
git commit -m "aaaa"
```

---

# Enviando para o GitHub

Primeira vez:

```bash
git push -u origin feature/tela-login
```

---

# O Que Faz o -u?

Configura a branch remota.

Depois disso basta:

```bash
git push
```

---

# Como Ver Todas as Branches

## Branches Locais

```bash
git branch
```

---

## Branches Remotas

```bash
git branch -r
```

---

## Todas as Branches

```bash
git branch -a
```

---

# Mudando de Branch

Para voltar para a main:

```bash
git switch main
```

ou

```bash
git checkout main
```

---

# Voltando Para Sua Branch

```bash
git switch feature/tela-login
```

---

# Cenário Real de Equipe

Imagine:

Você está desenvolvendo a tela de Login.

Enquanto isso:

Outro colega altera a branch principal.

Representação:

```txt
main
  |
  |---- alteração colega
```

Enquanto isso:

```txt
feature/tela-login
  |
  |---- sua alteração
```

Agora sua branch está desatualizada.

---

# Atualizando Sua Branch

## Passo 1

Ir para a main.

```bash
git checkout main
```

---

## Passo 2

Atualizar a main.

```bash
git pull origin main
```

---

## Passo 3

Voltar para sua branch.

```bash
git checkout feature/tela-login
```

---

## Passo 4

Fazer merge.

```bash
git merge main
```

---

# Resultado

Antes:

```txt
main
  |
  |---- alteração colega

feature/tela-login
  |
  |---- sua alteração
```

Depois:

```txt
feature/tela-login
  |
  |---- alteração colega
  |
  |---- sua alteração
```

Sua branch agora possui as alterações mais recentes.

---

# O Que é Pull Request (PR)?

Quando a funcionalidade estiver pronta:

```txt
feature/tela-login
```

Você cria um:

```txt
Pull Request
```

Representação:

```txt
feature/tela-login
         ↓
       PR
         ↓
       main
```

---

# Como Criar um Pull Request

Após:

```bash
git push
```

Acesse o GitHub.

Geralmente aparecerá:

```txt
Compare & Pull Request
```

Clique e crie o PR.

---

# O Que Acontece Depois?

Outro desenvolvedor ou líder do projeto pode:

- revisar seu código;
- solicitar alterações;
- aprovar;
- comentar melhorias.

Esse processo é chamado:

```txt
Code Review
```

---

# Merge Pull Request

Após aprovação:

```txt
Merge Pull Request
```

Sua funcionalidade entra na branch principal.

Representação:

```txt
main
  |
  |---- tela login
```

---

# Convenção de Nomes de Branches

## Funcionalidades

```txt
feature/login
feature/dashboard
feature/cadastro
feature/perfil
```

---

## Correções

```txt
fix/login
fix/navbar
fix/api
```

---

## Correções Urgentes

```txt
hotfix/erro-producao
hotfix/login
```

---

## Refatoração

```txt
refactor/api
refactor/dashboard
```

---

# Comandos Mais Utilizados

## Atualizar Projeto

```bash
git pull
```

---

## Ver Status

```bash
git status
```

---

## Ver Branches

```bash
git branch
```

---

## Criar Branch

```bash
git checkout -b nome-da-branch
```

---

## Trocar de Branch

```bash
git switch nome-da-branch
```

---

## Adicionar Arquivos

```bash
git add .
```

---

## Criar Commit

```bash
git commit -m "mensagem"
```

---

## Enviar Alterações

```bash
git push
```

---

# Exemplo Real

Suponha que você ficou responsável por:

- Tela de Login
- Tela de Cadastro
- Dashboard

O ideal seria criar:

```txt
feature/login
feature/cadastro
feature/dashboard
```

Representação:

```txt
main
 ├── feature/login
 ├── feature/cadastro
 └── feature/dashboard
```

Cada funcionalidade fica isolada.

---

# Fluxo Completo Recomendado

Quando começar o dia:

```bash
git checkout main
git pull origin main
```

Criar a tarefa:

```bash
git checkout -b feature/tela-login
```

Desenvolver.

Salvar:

```bash
git add .
git commit -m "Cria layout da tela de login"
```

Enviar:

```bash
git push -u origin feature/tela-login
```

Abrir Pull Request.

Após aprovação:

```bash
git checkout main
git pull
```

Criar a próxima branch.

---

# Resumo Geral

| Comando | Função |
|----------|----------|
| git clone | Clonar repositório |
| git branch | Listar branches |
| git checkout -b | Criar branch |
| git switch | Trocar branch |
| git add . | Adicionar arquivos |
| git commit | Criar commit |
| git push | Enviar alterações |
| git pull | Atualizar projeto |
| git merge | Mesclar branches |

---

# Exercícios

## Exercício 1

Clone um repositório qualquer do GitHub.

---

## Exercício 2

Crie uma branch chamada:

```txt
feature/home
```

---

## Exercício 3

Crie uma branch chamada:

```txt
feature/dashboard
```

Faça uma alteração fictícia e um commit.

---

## Exercício 4

Liste todas as branches locais e remotas.

---

## Exercício 5

Troque entre duas branches diferentes utilizando:

```bash
git switch
```

---

## Exercício 6

Atualize sua branch utilizando alterações da main.

---

## Exercício 7

Simule um Pull Request.

---

## Exercício 8

Realize o fluxo completo:

1. Atualizar a main
2. Criar branch
3. Fazer alterações
4. Fazer commit
5. Fazer push
6. Criar Pull Request
7. Fazer merge
8. Voltar para a main