# ⚡ Super Resumão: Node.js + NVM (Node Version Manager)

## 🧐 O que é Node.js?
- **Node.js** é um ambiente de execução de **JavaScript fora do navegador**.
- Baseado no **motor V8** do Google Chrome.
- Permite construir servidores, APIs, automações, backends e aplicativos escaláveis.

### Características principais:
- 🚀 Altamente performático (graças ao V8).
- ✨ Baseado em **eventos** e **programação assíncrona**.
- 📅 Muito usado para desenvolvimento web moderno (backend + frontend).

---

## 🔧 O que é o NVM?
- **NVM** = **Node Version Manager**.
- Gerenciador de várias versões do Node.js.

### Para que serve:
- Instalar várias versões do Node (ex: 14, 16, 18, 20).
- Alternar rapidamente entre versões.
- Testar projetos em versões diferentes sem conflito.

### Vantagem:
- Flexibilidade para trabalhar com projetos antigos e novos.
- Evita bugs por diferenças de versão.

---

# 🛠️ Instalação do NVM no Ubuntu (WSL)

### 1. Baixar e executar o script oficial:
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```

### 2. Recarregar configuração do terminal:
```bash
source ~/.bashrc
```

### 3. Verificar instalação:
```bash
command -v nvm
```
- Se retornar `nvm`, está instalado corretamente.

### (Problema?)
- Se `nvm` não funcionar, adicione manualmente no `~/.bashrc`:
```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```
- Depois rode:
```bash
source ~/.bashrc
```

---

# 🚀 Usando o NVM

## 📅 Comandos Básicos
- Instalar uma versão do Node.js:
  ```bash
  nvm install 18
  ```
- Listar versões instaladas:
  ```bash
  nvm ls
  ```
- Listar todas as versões disponíveis:
  ```bash
  nvm ls-remote
  ```
- Definir a versão a ser usada no momento:
  ```bash
  nvm use 18
  ```
- Definir uma versão como padrão:
  ```bash
  nvm alias default 18
  ```

## 🔄 Comandos Intermediários
- Remover uma versão instalada:
  ```bash
  nvm uninstall 16
  ```
- Usar versão baseada no arquivo `.nvmrc` do projeto:
  ```bash
  nvm use
  ```
- Instalar versão baseada no `.nvmrc`:
  ```bash
  nvm install
  ```

## 🧹 Comandos Avançados
- Usar versão específica para um comando:
  ```bash
  nvm exec 18 node -v
  ```
- Executar script com versão específica:
  ```bash
  nvm run 18 app.js
  ```
- Atualizar o próprio NVM:
  ```bash
  cd ~/.nvm && git pull origin master && source ~/.bashrc
  ```

---

# 📦 Extras: NPM e NPX

## 👉 O que é NPM?
- **Node Package Manager**.
- Gerenciador oficial de pacotes (bibliotecas) do Node.js.
- Usado para instalar dependências.

### Exemplos:
- Instalar pacote localmente:
  ```bash
  npm install express
  ```
- Instalar pacote globalmente:
  ```bash
  npm install -g nodemon
  ```
- Rodar script definido no package.json:
  ```bash
  npm run dev
  ```

## 👉 O que é NPX?
- **NPX** executa pacotes Node.js sem precisar instalá-los.

### Exemplos:
- Rodar create-react-app sem instalar:
  ```bash
  npx create-react-app meu-app
  ```

---

# 🌟 Boas Práticas
- Sempre use `nvm` para instalar Node.js (não instale direto com apt-get).
- Deixe definida uma **versão padrão** com `nvm alias default`.
- Em projetos, use sempre o arquivo **.nvmrc** com a versão usada:
  ```bash
  18
  ```
- Sempre verifique:
  ```bash
  which node
  which npm
  ```
  para garantir que o Node/NPM estão vindo do WSL (e não de C:/).

---

# 🎯 Em resumo:
> Instale o NVM → Instale e gerencie Node.js facilmente → Trabalhe com várias versões → Use o terminal sempre no WSL!

---
