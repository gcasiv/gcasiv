# 📁 ESTRUTURA DO PROJETO — README Personalizado GitHub
> **@gcasiv — Gustavo Casanova**  
> Documentação completa de organização, configuração e manutenção do perfil.

---

## 📂 Estrutura de Arquivos e Pastas

```
gcasiv/                          ← repositório especial (mesmo nome do usuário)
│
├── README.md                    ← Perfil principal (PT-BR — padrão)
├── README_EN.md                 ← Versão em inglês do perfil
├── ESTRUTURA.md                 ← Este arquivo (documentação)
│
├── assets/                      ← Imagens e mídias referenciadas no README
│   ├── cat.gif                  ← Seu gif do gatinho (feito no Aseprite)
│   ├── banner.png               ← Banner opcional caso queira um customizado
│   └── preview.png              ← Screenshot do perfil para portfólio
│
└── .github/
    └── workflows/
        └── pacman.yml           ← GitHub Action para gerar o gráfico Pac-Man
```

---

## 🐱 Como Adicionar o Gif do Gato

1. Crie seu gif no **Aseprite** (pixel art recomendado — fica incrível no GitHub)
2. Salve como `cat.gif` dentro da pasta `assets/`
3. No `README.md`, substitua a linha abaixo:

```md
<!-- PLACEHOLDER DO GIF DO GATO (adicione seu .gif do Aseprite aqui) -->
<img src="https://media.giphy.com/media/JIX9t2j0ZTN9S/giphy.gif" .../>
```

Por:

```md
<img src="./assets/cat.gif" width="200" alt="cat gif" style="border-radius: 12px;"/>
```

> 💡 **Dica de tamanho:** 200×200px ou 150×200px funciona muito bem para a coluna lateral. Mantenha o gif com fundo transparente para combinar com qualquer tema do GitHub.

---

## 🕹️ Como Configurar o Pac-Man (Gráfico de Contribuições)

O gráfico Pac-Man é gerado automaticamente via **GitHub Actions**. Siga os passos:

### 1. Criar o arquivo da Action

Crie o arquivo `.github/workflows/pacman.yml` com o seguinte conteúdo:

```yaml
name: Generate Pac-Man Graph

on:
  schedule:
    - cron: "0 */12 * * *"   # Roda a cada 12 horas
  workflow_dispatch:           # Permite rodar manualmente

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

### 2. Habilitar permissões

- Vá em **Settings → Actions → General**
- Em **Workflow permissions**, marque: `Read and write permissions`
- Salve

### 3. Rodar manualmente pela primeira vez

- Vá em **Actions → Generate Pac-Man Graph → Run workflow**

Depois de rodar, o SVG estará disponível e o gráfico aparecerá automaticamente no seu README!

---

## 🌐 Alternância de Idioma (PT-BR ↔ EN)

O sistema de tradução funciona com **dois arquivos separados** e badges clicáveis:

| Arquivo        | Idioma padrão | Link da badge                   |
|----------------|---------------|---------------------------------|
| `README.md`    | 🇧🇷 Português  | Badge EN leva para README_EN.md |
| `README_EN.md` | 🇺🇸 English   | Badge PT leva para README.md    |

> Ao entrar no seu perfil (`github.com/gcasiv`), o GitHub exibe o `README.md` automaticamente — ou seja, **PT-BR é o padrão**, exatamente como você quis.

---

## 🔗 Links que Precisam Ser Atualizados

Abra o `README.md` e o `README_EN.md` e substitua os placeholders abaixo pelos seus links reais:

| Placeholder                         | Substitua por                            |
|-------------------------------------|------------------------------------------|
| `https://www.linkedin.com/in/gcasiv`| Seu link real do LinkedIn                |
| `seuemail@gmail.com`                | Seu e-mail real                          |
| `https://www.behance.net/gcasiv`    | Seu link real do Behance                 |
| `@colliriall`                       | ✅ Já está correto (Instagram de desenho) |

---

## 📊 Gráficos Utilizados (APIs Externas)

Todos os gráficos usam APIs gratuitas e confiáveis — sem necessidade de token para a maioria:

| Gráfico                  | Serviço                                | Documentação                                        |
|--------------------------|----------------------------------------|-----------------------------------------------------|
| Stats Card               | github-readme-stats                   | github.com/anuraghazra/github-readme-stats          |
| Streak Stats             | streak-stats.demolab.com              | github.com/DenverCoder1/github-readme-streak-stats  |
| Activity Graph           | github-readme-activity-graph          | github.com/Ashutosh00710/github-readme-activity-graph |
| Trophy                   | github-profile-trophy                 | github.com/ryo-ma/github-profile-trophy             |
| Pac-Man Graph            | Platane/snk                           | github.com/Platane/snk                              |
| Typing SVG               | readme-typing-svg.demolab.com         | github.com/DenverCoder1/readme-typing-svg           |
| Banner (capsule-render)  | capsule-render.vercel.app             | github.com/kyechan99/capsule-render                 |
| Ícones (skillicons)      | skillicons.dev                        | github.com/tandpfun/skill-icons                     |

---

## 🎨 Paleta de Cores Utilizada

```css
--verde-escuro-1:  #004d1a;   /* fundo de seções / footer */
--verde-escuro-2:  #006622;   /* gradientes intermediários */
--verde-principal: #00a651;   /* cor primária — badges, títulos */
--verde-claro:     #39d353;   /* destaque — ícones, linhas */
--verde-link:      #1a6b3c;   /* hover / links secundários */
--bg-dark:         #0d1117;   /* fundo dos cards (GitHub dark) */
--text-light:      #c9d1d9;   /* texto dos cards */
```

---

## ✅ Checklist de Publicação

Antes de publicar, confirme:

- [ ] Repositório criado com o nome exato `gcasiv` (igual ao seu usuário)
- [ ] `README.md` e `README_EN.md` na raiz do repositório
- [ ] Pasta `assets/` criada
- [ ] Gif do gato adicionado em `assets/cat.gif` e caminho atualizado no README
- [ ] Links reais do LinkedIn, e-mail e Behance substituídos
- [ ] GitHub Action do Pac-Man criada e rodada pelo menos uma vez
- [ ] Permissões de Actions habilitadas (read + write)
- [ ] Repositório configurado como **público**

---

## 💡 Dicas Extras

- **Atualize frequentemente:** Quanto mais commits você fizer, mais bonito fica o gráfico Pac-Man e o Activity Graph
- **Fixe repositórios:** Fixe seus melhores projetos no perfil para aparecerem em destaque
- **README dos repositórios:** Adicione um README caprichado em cada projeto — faz toda a diferença para quem visita
- **Contribuições privadas:** Nas configurações do card de stats, já está ativado `count_private=true`

---

<div align="center">
  <sub>Documentação criada para <strong>@gcasiv — Gustavo Casanova</strong> 💚</sub>
</div>
