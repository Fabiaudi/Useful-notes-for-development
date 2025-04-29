# 📝 Super Resumão: Git + GitHub com SSH

## 🤓 O que é o Git?
- **Git** é um sistema de **controle de versão distribuído**.
- Permite salvar, comparar, restaurar e compartilhar código.
- Muito usado em projetos de software, sozinho ou com plataformas como GitHub.

## 🔗 O que é o GitHub?
- Plataforma online para **hospedar repositórios Git**.
- Permite colaborar, revisar código, abrir issues, fazer pull requests e versionar projetos publicamente ou de forma privada.

---

## 🚀 Configuração Inicial do Git no Ubuntu (WSL)

### 1. Configurar identidade do usuário:
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu_email@exemplo.com"
```

### 2. Definir o editor padrão do Git:
```bash
git config --global core.editor "code --wait"
```

### 3. Ver configurações atuais:
```bash
git config --list
```

---

# 🚪 Conectando com GitHub via SSH (sem senha)

## ✏️ Gerar nova chave SSH:
```bash
ssh-keygen -t ed25519 -C "seu_email@exemplo.com"
```
- Aperte `Enter` para aceitar local padrão.
- Aperte `Enter` duas vezes para ignorar a senha.

## 🚧 Iniciar ssh-agent:
```bash
eval "$(ssh-agent -s)"
```

## ➕ Adicionar a chave privada ao agente:
```bash
ssh-add ~/.ssh/id_ed25519
```

## 📋 Copiar chave pública para colar no GitHub:
```bash
cat ~/.ssh/id_ed25519.pub
```

### 🔎 No GitHub:
- Ir em **Settings > SSH and GPG keys > New SSH key**.
- Colar a chave.
- Dar um nome (ex: "WSL Bruno") e salvar.

## 📓 Clonar repositório com SSH:
```bash
git clone git@github.com:usuario/repositorio.git
```

---

# 💡 Comandos Básicos do Git

## 📰 Repositório
- Inicializar novo repo:
  ```bash
  git init
  ```
- Clonar repo remoto:
  ```bash
  git clone url
  ```

## ✍️ Alterar e versionar
- Verificar status:
  ```bash
  git status
  ```
- Adicionar arquivos ao stage:
  ```bash
  git add nome_arquivo
  git add .        # adiciona tudo
  ```
- Fazer commit:
  ```bash
  git commit -m "mensagem"
  ```

## 🔄 Enviar e atualizar
- Enviar commits:
  ```bash
  git push origin nome-da-branch
  ```
- Atualizar branch local:
  ```bash
  git pull
  ```

---

# 📆 Comandos Intermediários
- Ver histórico de commits:
  ```bash
  git log
  ```
- Trocar de branch:
  ```bash
  git checkout nome-da-branch
  ```
- Criar nova branch:
  ```bash
  git checkout -b nome-da-branch
  ```
- Exibir branches:
  ```bash
  git branch
  ```

---

# 🔧 Comandos Avançados
- Reverter commit (sem perder alterações):
  ```bash
  git reset --soft HEAD~1
  ```
- Reverter commit (perdendo alterações):
  ```bash
  git reset --hard HEAD~1
  ```
- Corrigir último commit (sem mudar o hash):
  ```bash
  git commit --amend
  ```
- Resolver conflitos:
  ```bash
  git status
  # editar os arquivos conflitados
  git add .
  git commit
  ```

---

# 📍 Boas práticas com Git + GitHub
- Faça commits com mensagens claras e descritivas.
- Use branches para novas funcionalidades.
- Sempre puxe antes de dar push (`git pull`).
- Crie `.gitignore` para ignorar arquivos temporários (ex: node_modules).
- Nunca suba senhas, chaves ou arquivos sensíveis.

---

# 🔢 Em resumo:
> Configure seu Git → Gere chave SSH → Conecte com GitHub → Use comandos com segurança → Versione seus projetos como um profissional!

---