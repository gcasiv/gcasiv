# Documentacao do Projeto — README Personalizado GitHub
> **@gcasiv — Gustavo Casanova**

---

## Estrutura de Arquivos

```
gcasiv/                              ← repositorio especial (mesmo nome do usuario)
│
├── README.md                        ← Perfil principal (PT-BR — padrao)
├── README_EN.md                     ← Versao em ingles
├── ESTRUTURA.md                     ← Este arquivo
│
└── assets/
    ├── cat.gif                      ← Seu gif do gatinho (feito no Aseprite)
    └── icons/                       ← Todos os 50 SVGs do projeto
        │
        ├── — BANDEIRAS —
        ├── BR-Brazil.svg
        ├── US-United States.svg
        │
        ├── — CONTATO —
        ├── behance.svg
        ├── e-mail.svg
        ├── linkedin.svg
        ├── logo-instagram.svg
        │
        ├── — LINGUAGENS —
        ├── css3.svg
        ├── html5.svg
        ├── typescript.svg
        ├── javascript.svg
        ├── php.svg
        ├── python.svg
        ├── node.js.svg
        ├── react.svg
        ├── next.js.svg
        ├── angular.svg
        ├── vue.svg
        ├── tailwindcss.svg
        ├── mysql.svg
        ├── postgresql.svg
        ├── firebase.svg
        ├── xampp.svg
        ├── bootstrap.svg
        ├── sass.svg
        ├── ionic.svg
        ├── ruby.svg
        ├── git.svg
        ├── linux.svg
        ├── markdown.svg
        ├── vite.js.svg
        ├── github-copilot.svg
        ├── visual-studio-code.svg
        ├── android.svg
        ├── godot.svg
        ├── blender.svg
        ├── figma.svg
        ├── penpot.svg
        ├── affinity.svg
        ├── behance-black.svg
        ├── ibis-paint-x.svg
        ├── clip-studio-paint.svg
        ├── krita.svg
        ├── aseprite.svg
        ├── notion.svg
        ├── trello.svg
        │
        └── — LOGOTIPOS ESPECIAIS —
            ├── vscode-logotype.svg
            ├── notepad++-logotype.svg
            ├── github-logotype.svg
            └── vercel-logotype.svg
```

---

## Como adicionar o gif do gato

1. Crie seu gif no **Aseprite** (pixel art — fica incrivel no GitHub)
2. Salve como `cat.gif` dentro da pasta `assets/`
3. No `README.md` e `README_EN.md`, encontre o comentario:

```md
<!-- <img src="./assets/cat.gif" width="200" alt="cat gif"/> -->
```

4. Remova o comentario e apague a linha do gif temporario do Giphy acima dele

---

## Como configurar o Pac-Man

O grafico Pac-Man e gerado via **GitHub Actions**. Siga os passos:

### 1. Criar o arquivo da Action

Crie `.github/workflows/pacman.yml` com o conteudo abaixo:

```yaml
name: Generate Pac-Man Graph

on:
  schedule:
    - cron: "0 */12 * * *"
  workflow_dispatch:

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - name: Generate pacman graph
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/pacman-contribution-graph.svg
            dist/pacman-contribution-graph-dark.svg?palette=github-dark

      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### 2. Habilitar permissoes

- Va em **Settings → Actions → General**
- Em **Workflow permissions**, marque: `Read and write permissions`
- Salve

### 3. Rodar pela primeira vez

- Va em **Actions → Generate Pac-Man Graph → Run workflow**

---

## Sistema de idiomas

| Arquivo        | Idioma  | Comportamento                          |
|----------------|---------|----------------------------------------|
| `README.md`    | PT-BR   | Exibido por padrao ao entrar no perfil |
| `README_EN.md` | English | Acessado clicando na bandeira dos EUA  |

A bandeira do Brasil no topo do `README_EN.md` volta para o PT-BR.
A bandeira dos EUA no topo do `README.md` vai para o ingles.

---

## Links para atualizar

Abra os dois READMEs e substitua:

| Placeholder                         | Substitua por               |
|-------------------------------------|-----------------------------|
| `seuemail@gmail.com`                | Seu e-mail real             |
| `https://www.linkedin.com/in/gcasiv`| Seu link real do LinkedIn   |
| `https://www.behance.net/gcasiv`    | Seu link real do Behance    |

---

## Paleta de cores

```
#004d1a  — verde escuro 1   (banner, footer)
#006622  — verde escuro 2   (gradientes)
#00a651  — verde principal  (badges, titulos, bordas)
#39d353  — verde claro      (icones, linhas do grafico)
#1a6b3c  — verde link       (badges secundarias)
#0d1117  — fundo dark       (cards de stats)
#c9d1d9  — texto claro      (texto dos cards)
#f0a500  — amarelo          (badge "Em Aperfeicoamento")
```

---

## Checklist de publicacao

- [ ] Repositorio `gcasiv` criado como publico
- [ ] `README.md` na raiz
- [ ] `README_EN.md` na raiz
- [ ] `ESTRUTURA.md` na raiz
- [ ] Pasta `assets/icons/` com os 50 SVGs
- [ ] Links reais de LinkedIn, e-mail e Behance atualizados
- [ ] GitHub Action do Pac-Man criada e rodada ao menos uma vez
- [ ] Permissoes de Actions habilitadas (read + write)
- [ ] Gif do gato adicionado em `assets/cat.gif` (quando pronto)

---

<div align="center">
  <sub>Documentacao para <strong>@gcasiv — Gustavo Casanova</strong></sub>
</div>