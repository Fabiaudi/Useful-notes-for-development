# 💻 Super Resumão: Comandos Essenciais do Terminal Ubuntu para Devs

## 📂 Navegação entre Diretórios
| Comando | Descrição |
|--------|-----------|
| `pwd` | Mostra o caminho completo do diretório atual |
| `ls` | Lista arquivos e pastas no diretório atual |
| `ls -la` | Lista todos os arquivos com detalhes (inclusive ocultos) |
| `cd nome` | Entra na pasta chamada `nome` |
| `cd ..` | Volta um nível na hierarquia de diretórios |
| `cd /` | Vai para a raiz do sistema de arquivos |
| `cd ~` | Vai para o diretório do usuário (home) |
| `cd -` | Volta para o último diretório acessado |
| `cd /mnt/c/` | Acessa arquivos do Windows dentro do WSL (ex: disco C:) |
| `tree` | Mostra estrutura de diretórios em formato de árvore (se instalado) |

---

## 📁 Manipulação de Arquivos e Pastas
| Comando | Descrição |
|--------|-----------|
| `mkdir nome` | Cria nova pasta |
| `touch arquivo.txt` | Cria novo arquivo vazio |
| `rm arquivo.txt` | Remove arquivo |
| `rm -r pasta/` | Remove pasta e tudo dentro dela |
| `cp origem destino` | Copia arquivos ou pastas |
| `mv origem destino` | Move ou renomeia arquivos/pastas |

---

## 📄 Visualização e Edição
| Comando | Descrição |
|--------|-----------|
| `cat arquivo.txt` | Mostra conteúdo do arquivo |
| `less arquivo.txt` | Mostra conteúdo página por página |
| `nano arquivo.txt` | Edita o arquivo no terminal (editor simples) |
| `vim arquivo.txt` | Editor avançado no terminal |
| `head -n 10 arquivo.txt` | Mostra as 10 primeiras linhas |
| `tail -f log.txt` | Mostra últimas linhas e acompanha em tempo real |

---

## 🧑‍💻 Permissões e Usuários
| Comando | Descrição |
|--------|-----------|
| `chmod +x script.sh` | Torna um arquivo executável |
| `chmod 755 arquivo` | Permissões completas para o dono, leitura e execução para outros |
| `chown user:grupo arquivo` | Muda dono e grupo de um arquivo/pasta |
| `whoami` | Mostra o usuário atual |
| `sudo comando` | Executa comando com permissões de superusuário |

---

## ⚙️ Gerenciamento de Processos
| Comando | Descrição |
|--------|-----------|
| `ps aux` | Lista todos os processos ativos |
| `top` | Monitor em tempo real de processos |
| `htop` | Versão avançada do `top` (se instalado) |
| `kill PID` | Encerra processo pelo PID |
| `kill -9 PID` | Força encerramento imediato |
| `jobs` | Lista processos em segundo plano |
| `fg %1` | Traz processo %1 para o primeiro plano |

---

## 🔌 Rede e Internet
| Comando | Descrição |
|--------|-----------|
| `ping google.com` | Testa conexão com servidor |
| `curl url` | Faz requisição para uma URL (muito útil para APIs) |
| `wget url` | Baixa arquivos pela internet |
| `ifconfig` ou `ip a` | Mostra interfaces de rede |

---

## 🧰 Utilitários para Devs
| Comando | Descrição |
|--------|-----------|
| `clear` | Limpa o terminal |
| `history` | Mostra comandos digitados anteriormente |
| `alias gs="git status"` | Cria atalho para comandos longos |
| `source ~/.bashrc` | Recarrega configurações do terminal |
| `echo $VARIAVEL` | Exibe o valor de uma variável de ambiente |
| `which node` | Mostra o caminho do executável `node` |
| `nvm use 18` | Usa a versão 18 do Node.js (com NVM) |

---

## 🧠 Dica Extra: Comandos em Cadeia
- `&&`: executa o próximo comando **somente se o anterior tiver sucesso**
  ```bash
  cd projeto && npm run dev
  ```
- `|` (pipe): envia saída de um comando como entrada de outro
  ```bash
  cat arquivo.log | grep "ERRO"
  ```

---

## 🎯 Em resumo:
> Dominar o terminal acelera sua produtividade como dev.  
> Esses comandos são base para navegação, edição, rede, permissões e automação!

---
