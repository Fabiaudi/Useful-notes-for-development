
# 🧒 Guia de Commits Semânticos com Emojis no Git

> Um jeito divertido e colorido de aprender como deixar seus commits lindos, organizados e mágicos!

---

## 🐥 O que é um Commit?

Imagine que você está escrevendo um **livro com amigos**.  
Cada vez que alguém escreve uma parte, deixa um **bilhetinho** contando o que fez.  
Esse bilhetinho é o **commit**!

---

## 🎨 O que é um Commit Semântico?

É quando você **deixa o bilhetinho mais organizado**, começando com uma palavrinha mágica (tipo `feat`, `fix`, `docs`) e um **emoji fofo** pra mostrar o que você fez.

📌 Exemplo:

```bash
feat: criei uma nova página ✨
fix: consertei um botão que não funcionava 🐛
```

---

## 🧠 Tipos de Commit + Emojis

| Tipo      | O que significa                   | Emoji |
|-----------|-----------------------------------|--------|
| feat      | Nova funcionalidade               | ✨      |
| fix       | Corrigir um erro                  | 🐛      |
| docs      | Atualizar documentação            | 📚      |
| style     | Mudar estilo do código            | 🎨      |
| refactor  | Melhorar o código                 | ♻️      |
| test      | Criar ou mudar testes             | 🧪      |
| chore     | Tarefas de manutenção             | 🔧      |
| perf      | Melhorar desempenho               | ⚡      |
| cleanup   | Limpeza de código inútil          | 🧹      |
| remove    | Remover arquivos                  | 🗑️      |

---

## 🪄 O que são Hooks?

Hooks são como **mágicos do Git** que garantem que sua mensagem de commit está certinha antes de salvar ✨🧙‍♂️

---

## ⚙️ Nossos três scripts mágicos:

- `push.sh` → Um **menu interativo** com emojis para você escolher o tipo de commit.
- `prepare-commit-msg.sh` → Um **ajudante com IA** que sugere mensagens de commit baseado no que você mudou.
- `commit-msg.sh` → O **fiscal** que confere se sua mensagem segue as regras.

---

## 📦 Como instalar os Hooks?

```bash
mkdir -p .git/hooks
cp caminho/para/commit-msg.sh .git/hooks/commit-msg
chmod +x .git/hooks/commit-msg
```

> Use `./push.sh` para fazer seus commits com magia! 🧚

---

## 🍫 Exemplo doce

```bash
./push.sh
# Escolha: 1 (feat)
# Mensagem: adicionei a receita de brigadeiro
```

💌 Resultado:
```
[feat] ✨: adicionei a receita de brigadeiro
```

---

## 🖼️ Visual didático

Veja esse resumo ilustrado com ícones e explicações fofinhas:

![Guia Infantil de Commits](guia_commits_semanticos_infantil.png)

> 💡 Dica: Coloque esse PNG na raiz do repositório e use o nome acima ou edite o caminho da imagem.

---

## ✅ Perfeito para:

- Iniciantes 🐣  
- Times que querem padronizar os commits 🧑‍🤝‍🧑  
- Projetos com integração contínua 🤖  
- Ensinar Git de forma divertida 🎉  

---

Feito com carinho para aprender brincando! 💜
