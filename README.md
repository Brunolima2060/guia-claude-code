# 🚀 Guia de sobrevivência do Claude Code

Tá começando no Claude Code? Beleza. Aqui está o kit que eu uso todo dia, sem enrolação: o que é cada coisa, pra que serve e como instalar em minutos.

Tudo aponta pra repositórios públicos oficiais. Zero chave, zero dado pessoal.

> **Antes de tudo:** Claude Code instalado e logado (digite `claude` no terminal ou use a extensão do VS Code).

---

## 🗺️ O mapa rápido

| Ferramenta | Em uma frase | Vale a pena? |
|---|---|---|
| **RTK** | Faz seu Claude gastar menos token | Instala hoje |
| **Superpowers** | Ensina o Claude a trabalhar com método | Instala hoje |
| **Skills da Anthropic** | Docs, planilhas, design, testes prontos | Muito |
| **Remotion** | Faz vídeo e motion graphics com código | Se você quer vídeo |
| **Anatomy** | Ilustrações técnicas animadas | Se você quer site bonito |

---

## 💸 1. RTK: o seu "Rust Token Killer"

**A ideia:** quando o Claude roda `git status` ou `npm test`, o terminal cospe um monte de texto inútil, e cada pedacinho vira token (ou seja, dinheiro e limite de uso). O RTK fica no meio do caminho e **enxuga a saída** antes de ela chegar no Claude: corta ruído, junta repetição, mostra só o que importa.

Resultado: sessões que duram mais e limite que demora mais pra acabar.

**Números reais (os meus):** depois de mais de **22 mil comandos**, economizei **22,6 milhões de tokens (~22%)**. O projeto promete 60–90% em comandos de desenvolvimento; na vida real depende do que você faz. Quanto mais `git`, testes e leitura de arquivo, mais ele rende.

🔗 https://github.com/rtk-ai/rtk

**Instalar (Windows):**

```powershell
winget install rtk-ai.rtk
rtk --version
rtk init -g
```

> Mac/Linux: `brew install rtk` e depois `rtk init -g`.

O `rtk init -g` instala o hook no Claude Code sozinho. Depois é só **reiniciar o Claude Code** e esquecer: você continua pedindo as mesmas coisas, o hook troca `git status` por `rtk git status` por baixo dos panos.

**Comandos pra você se sentir o hacker da economia:**

```bash
rtk gain             # quanto você já economizou
rtk gain --history   # economia por comando
rtk discover         # onde você ainda tá perdendo token
rtk proxy <comando>  # roda sem filtro (pra depurar)
```

**Pegadinhas:**
- Se `rtk gain` der erro, você pode ter instalado outro programa com o mesmo nome (o "Rust Type Kit"). Confere com `rtk --version`.
- Script com heredoc e barras invertidas dentro do Bash pode ser mexido pelo RTK. Solução: grava o script num arquivo e roda o arquivo.

---

## 🧠 2. Superpowers: dá disciplina pro Claude

Sabe quando o Claude sai programando antes de entender o problema, e depois diz "pronto!" com o código quebrado? O Superpowers resolve isso. É um plugin que força um processo: **pensar antes de fazer** (brainstorming), planejar, escrever teste, depurar com método e **provar que funciona antes de dar como terminado**.

🔗 https://github.com/obra/superpowers

**Instalar:** no Claude Code, digite `/plugin` e procure `superpowers`.

---

## 🧰 3. Skills oficiais da Anthropic

Uma caixa de ferramentas pronta: criar Word, PDF, PowerPoint e Excel, fazer design de interface, arte, testar app web, criar servidores MCP e até **criar suas próprias skills**.

🔗 https://github.com/anthropics/skills

```
/plugin marketplace add anthropics/skills
/plugin install example-skills@anthropic-agent-skills
```

---

## 🎬 4. Remotion: vídeo feito com código

O Remotion cria vídeo usando React. Você descreve cenas, textos e animações e ele renderiza um MP4. Com o Claude Code, **você descreve o vídeo em português e ele escreve o código**. Dá pra fazer anúncio, Reels, legenda palavra por palavra, tudo.

🔗 https://www.remotion.dev
🔗 Skills oficiais pro Claude: https://github.com/remotion-dev/skills (ensinam o Claude a usar o Remotion do jeito certo)

```bash
npx create-video@latest          # cria o projeto
npx skills add remotion-dev/skills   # ensina o Claude
npx remotion studio              # vê o vídeo ao vivo
npx remotion render              # gera o MP4
```

**Prompt de exemplo:** *"Faz um vídeo vertical de 15 segundos pra Reels, com título animado, fundo escuro e legenda palavra por palavra."*

**Aprendido na marra:**
- 🐌 **Renderize um vídeo por vez.** Vários ao mesmo tempo entopem RAM e disco (o Remotion deixa pastas temporárias do Chrome no Temp, limpa de vez em quando).
- 📝 Gera primeiro um **rascunho em baixa qualidade**, só depois o final.
- 🎙️ Quer narração de graça? O `edge-tts` (Python) gera voz em português sem custo.

---

## 🧊 5. Anatomy: ilustração técnica que parece de site premium

Skill que cria figuras isométricas animadas em SVG pra explicar uma ideia como se fosse um objeto físico. Ótimo pra landing page, artigo e documentação.

🔗 https://github.com/wheresryan22/anatomy (instalação na seção "Install" do README deles)

---

## 🧭 6. Hábitos que separam amador de profissional

1. **Crie um `CLAUDE.md`** na raiz do projeto (ou rode `/init`). É o manual que o Claude lê toda vez. Quanto melhor ele, menos você se repete.
2. **Uma tarefa por sessão.** Sessão longa e misturada gasta token e confunde o bichinho. Mudou de assunto? `/clear`.
3. **Plano antes de mudança grande.** Peça pra ele explicar o que vai fazer e só aprove se fizer sentido.
4. **Permissões com cabeça.** Comece aprovando tudo e libere aos poucos. Bloqueie o que é perigoso (`git push`, deploy) na lista `deny` do `settings.json`.
5. **Nunca cole senha ou chave no chat.** Use arquivo `.env` e ponha no `.gitignore`.
6. **Exija prova.** Peça pra ele rodar o teste ou abrir o app e mostrar funcionando, em vez de aceitar "deve estar certo".
7. **Peça pra ele lembrar.** Preferências e decisões importantes valem a pena guardar entre sessões.

---

## ✅ Por onde começar (ordem sugerida)

1. Instala o **RTK** (5 minutos, benefício imediato)
2. Instala o **Superpowers**
3. Cria o **`CLAUDE.md`** do seu primeiro projeto
4. Só então brinca com **Remotion** e o resto

Dúvida ou achou algo errado? Abre uma issue. Bom código! 🤙
