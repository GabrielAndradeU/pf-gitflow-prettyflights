# Comandos Git - Guia de Referência

## 1. Configuração Inicial

### 1.1. `git config`
**Explicação:** Configura opções do Git em nível local, global ou de sistema. Permite definir nome de usuário, email, editor padrão e outras preferências.

**Exemplos:**
```bash
# Configurar nome de usuário globalmente
git config --global user.name "João Silva"

# Configurar email para o repositório atual
git config user.email "joao.silva@prettyflights.com"
```

### 1.2. `git init`
**Explicação:** Inicializa um novo repositório Git em um diretório, criando a estrutura `.git` necessária para versionamento.

**Exemplos:**
```bash
# Inicializar repositório no diretório atual
git init

# Inicializar repositório em um novo diretório
git init totem-checkin
```

## 2. Operações Básicas

### 2.3. `git add`
**Explicação:** Adiciona arquivos modificados à área de staging (preparação) para serem incluídos no próximo commit.

**Exemplos:**
```bash
# Adicionar arquivo específico
git add src/CheckinService.java

# Adicionar todos os arquivos modificados
git add .
```

### 2.4. `git commit`
**Explicação:** Registra as mudanças da área de staging no histórico do repositório com uma mensagem descritiva.

**Exemplos:**
```bash
# Commit com mensagem inline
git commit -m "feat: adicionar validação de passaporte"

# Commit abrindo editor para mensagem detalhada
git commit
```

### 2.5. `git status`
**Explicação:** Exibe o estado atual do working directory e da staging area, mostrando arquivos modificados, adicionados ou não rastreados.

**Exemplos:**
```bash
# Ver status completo
git status

# Ver status de forma resumida
git status -s
```

### 2.6. `git log`
**Explicação:** Mostra o histórico de commits do repositório, incluindo autor, data e mensagem.

**Exemplos:**
```bash
# Ver histórico completo
git log

# Ver histórico de forma resumida (uma linha por commit)
git log --oneline --graph --all
```

## 3. Branches e Merge

### 3.7. `git branch`
**Explicação:** Lista, cria ou deleta branches. Sem argumentos, lista todas as branches locais.

**Exemplos:**
```bash
# Listar todas as branches
git branch

# Criar nova branch
git branch feature/validacao-documento
```

### 3.8. `git checkout`
**Explicação:** Alterna entre branches ou restaura arquivos do working tree.

**Exemplos:**
```bash
# Mudar para branch existente
git checkout develop

# Criar e mudar para nova branch
git checkout -b feature/impressao-boarding-pass
```

### 3.9. `git switch`
**Explicação:** Comando moderno para alternar entre branches (alternativa mais clara ao checkout para essa finalidade).

**Exemplos:**
```bash
# Mudar para branch existente
git switch main

# Criar e mudar para nova branch
git switch -c hotfix/corrigir-validacao-cpf
```

### 3.10. `git merge`
**Explicação:** Integra mudanças de uma branch em outra, combinando os históricos.

**Exemplos:**
```bash
# Fazer merge da feature na develop (estando na develop)
git merge feature/validacao-documento

# Merge sem fast-forward (cria commit de merge)
git merge --no-ff feature/impressao-boarding-pass
```

## 4. Repositórios Remotos

### 4.11. `git remote`
**Explicação:** Gerencia repositórios remotos conectados ao repositório local.

**Exemplos:**
```bash
# Adicionar repositório remoto
git remote add origin https://github.com/usuario/totem-checkin.git

# Listar repositórios remotos
git remote -v
```

### 4.12. `git push`
**Explicação:** Envia commits locais para um repositório remoto.

**Exemplos:**
```bash
# Enviar commits da branch atual
git push origin develop

# Enviar branch pela primeira vez e configurar tracking
git push -u origin feature/validacao-documento
```

### 4.13. `git pull`
**Explicação:** Busca e integra mudanças do repositório remoto na branch atual (equivale a git fetch + git merge).

**Exemplos:**
```bash
# Atualizar branch atual com mudanças remotas
git pull origin develop

# Pull com rebase ao invés de merge
git pull --rebase origin main
```

### 4.14. `git fetch`
**Explicação:** Baixa objetos e refs de um repositório remoto sem fazer merge automático.

**Exemplos:**
```bash
# Buscar todas as atualizações do remoto
git fetch origin

# Buscar de todos os remotos configurados
git fetch --all
```

### 4.15. `git clone`
**Explicação:** Cria uma cópia local de um repositório remoto.

**Exemplos:**
```bash
# Clonar repositório
git clone https://github.com/prettyflights/totem-checkin.git

# Clonar para diretório específico
git clone https://github.com/prettyflights/totem-checkin.git meu-projeto
```

## 5. Inspeção e Comparação

### 5.16. `git diff`
**Explicação:** Mostra diferenças entre commits, branches, working directory e staging area.

**Exemplos:**
```bash
# Ver mudanças não staged
git diff

# Comparar duas branches
git diff develop..feature/validacao-documento
```

### 5.17. `git show`
**Explicação:** Exibe informações detalhadas sobre objetos Git (commits, tags, etc).

**Exemplos:**
```bash
# Mostrar detalhes do último commit
git show

# Mostrar commit específico
git show a3f5b2c
```

## 6. Desfazendo Mudanças

### 6.18. `git reset`
**Explicação:** Desfaz commits movendo o ponteiro da branch, podendo alterar staging area e working directory.

**Exemplos:**
```bash
# Desfazer último commit mantendo mudanças em staging
git reset --soft HEAD~1

# Desfazer commits e descartar mudanças
git reset --hard HEAD~2
```

### 6.19. `git revert`
**Explicação:** Cria um novo commit que desfaz as mudanças de um commit anterior, preservando o histórico.

**Exemplos:**
```bash
# Reverter último commit
git revert HEAD

# Reverter commit específico
git revert a3f5b2c
```

## 7. Tags e Releases

### 7.20. `git tag`
**Explicação:** Cria, lista ou deleta tags, que são referências fixas a pontos específicos no histórico (normalmente releases).

**Exemplos:**
```bash
# Criar tag anotada (recomendado para releases)
git tag -a v1.0.0 -m "Release versão 1.0.0 - Totem Check-in"

# Listar todas as tags
git tag -l
```
