# 📦 Super Resumão: Docker

## O que é Docker?
- **Docker** permite executar programas em **contêineres**.
- **Contêiner** = ambiente isolado e padronizado → roda o app de forma igual em qualquer máquina.
- Evita problemas tipo “na minha máquina funciona”.

---

## Docker no Windows
- Docker foi feito para **Linux** → no Windows ele precisa de uma camada extra:
  - **Hyper-V**: virtualização completa (requer Windows Pro).
  - **WSL (Windows Subsystem for Linux)**: virtualização leve e integrada.

✅ Para projetos: **usar WSL 2** é a melhor escolha (mais leve e fácil).

---

## Tipos de Instalação do Docker
- **Docker Engine**: 
  - Só o núcleo.
  - Mais leve, só linha de comando.
- **Docker Desktop**:
  - Engine + Interface Gráfica.
  - Mais pesado, mas facilita para quem prefere clicar em botões.

✅ Recomendado: **Instalar Docker Engine direto no Ubuntu (via WSL)**.

---

## Como Instalar Docker Engine no Ubuntu (WSL)
Passos principais:

1. Atualizar pacotes:
   ```bash
   sudo apt-get update
   sudo apt-get install ca-certificates curl
   ```

2. Adicionar chave GPG e repositório do Docker:
   ```bash
   sudo install -m 0755 -d /etc/apt/keyrings
   sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
   sudo chmod a+r /etc/apt/keyrings/docker.asc
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   sudo apt-get update
   ```

3. Instalar o Docker:
   ```bash
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```

4. Liberar uso sem `sudo`:
   ```bash
   sudo usermod -aG docker $USER
   ```

5. Reiniciar o WSL:
   ```bash
   wsl --shutdown
   ```

6. Verificar se Docker está rodando:
   ```bash
   docker ps
   ```

---

# 📋 Principais Comandos Docker

## 📦 Comandos Básicos
- Listar imagens:
  ```bash
  docker images
  ```
- Listar contêineres rodando:
  ```bash
  docker ps
  ```
- Listar todos os contêineres (ativos e parados):
  ```bash
  docker ps -a
  ```
- Rodar um novo contêiner:
  ```bash
  docker run nome-da-imagem
  ```
- Rodar em segundo plano (modo detach):
  ```bash
  docker run -d nome-da-imagem
  ```
- Expor porta:
  ```bash
  docker run -p 3000:3000 nome-da-imagem
  ```

## ⚙️ Comandos Intermediários
- Parar um contêiner:
  ```bash
  docker stop id-ou-nome-do-container
  ```
- Iniciar contêiner parado:
  ```bash
  docker start id-ou-nome-do-container
  ```
- Remover contêiner:
  ```bash
  docker rm id-ou-nome-do-container
  ```
- Remover imagem:
  ```bash
  docker rmi nome-da-imagem
  ```

## 🛠️ Trabalhar com Volumes
- Listar volumes:
  ```bash
  docker volume ls
  ```
- Criar volume:
  ```bash
  docker volume create nome-do-volume
  ```
- Remover volume:
  ```bash
  docker volume rm nome-do-volume
  ```

## 🧩 Docker Compose
- Subir serviços:
  ```bash
  docker-compose up
  ```
- Subir serviços em segundo plano:
  ```bash
  docker-compose up -d
  ```
- Derrubar serviços:
  ```bash
  docker-compose down
  ```

## 🧹 Manutenção e Limpeza
- Remover todos contêineres parados:
  ```bash
  docker container prune
  ```
- Remover imagens não utilizadas:
  ```bash
  docker image prune
  ```
- Limpeza geral (contêineres, imagens, volumes):
  ```bash
  docker system prune
  ```

---

## Dicas de Uso
- Sempre use **WSL** como seu terminal principal para rodar Docker no Windows.
- Evite instalar Node.js e Docker no Windows "direto" para não confundir o sistema.
- Trabalhe com os projetos **dentro do WSL** (e não no disco C:/).

---

# 🎯 Em resumo:
> Instale o Docker Engine dentro do WSL → Trabalhe no Ubuntu → Use terminal → E seus projetos rodarão iguais em qualquer lugar!

---
