# 📘 Resumo do Node Version Manager (nvm) v0.40.1

## 🧠 O que é o NVM?
O **Node Version Manager** (`nvm`) é uma ferramenta de linha de comando para instalar, gerenciar e alternar entre várias versões do Node.js no mesmo sistema.

---

## 🔧 Comandos principais do NVM

### 🔹 Instalação e remoção
- `nvm install <versão>`  
  Instala uma versão do Node.js  
  Exemplos: `nvm install 18`, `nvm install node`, `nvm install --lts`

  **Opções úteis:**
  - `--lts=<nome>`: instala versão de uma linha LTS específica (ex: `--lts=hydrogen`)
  - `--reinstall-packages-from=<versão>`: reinstala os pacotes da versão anterior
  - `--alias=<nome>`: cria alias durante a instalação
  - `--default`: define como versão padrão
  - `--save`: grava versão no `.nvmrc`

- `nvm uninstall <versão>`  
  Remove uma versão instalada

---

### 🔹 Uso de versões
- `nvm use <versão>`  
  Usa uma versão específica do Node.js

- `nvm run <versão> <arquivo.js>`  
  Executa um script com a versão especificada

- `nvm exec <versão> <comando>`  
  Executa um comando usando uma versão específica  
  Ex: `nvm exec 18 npm -v`

---

### 🔹 Gerenciamento de versões
- `nvm ls` ou `nvm list`  
  Lista as versões instaladas

- `nvm ls-remote`  
  Lista as versões disponíveis para instalar (remotas)

- `nvm current`  
  Mostra a versão atualmente ativa

- `nvm version <versão>`  
  Resolve uma descrição para uma versão instalada localmente

- `nvm version-remote <versão>`  
  Resolve para uma versão remota correspondente

---

### 🔹 Alias
- `nvm alias <nome> <versão>`  
  Cria um apelido (ex: `nvm alias default 18.12.1`)

- `nvm unalias <nome>`  
  Remove um alias

- `nvm alias`  
  Lista todos os aliases definidos

---

### 🔹 Outras funcionalidades úteis
- `nvm reinstall-packages <versão>`  
  Reinstala os pacotes globais de uma versão para outra

- `nvm install-latest-npm`  
  Atualiza o `npm` para a versão mais recente compatível

- `nvm which <versão>`  
  Mostra o caminho da instalação do Node.js

- `nvm deactivate`  
  Reverte alterações no PATH feitas pelo `nvm`

- `nvm unload`  
  Descarrega o `nvm` do shell

- `nvm cache dir` / `nvm cache clear`  
  Mostra ou limpa o cache do `nvm`

- `nvm set-colors cgYmW`  
  Personaliza as cores da saída

---

## 📂 Arquivo `.nvmrc`
rc = Run Commands
Se presente, permite que comandos como `nvm install`, `nvm use`, `nvm run` e `nvm exec` usem automaticamente a versão especificada no arquivo `.nvmrc`.

