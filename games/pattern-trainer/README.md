# Pattern Trainer 🧠

Um pequeno jogo (React, arquivo único) para **treinar o reconhecimento de padrões**.
Faz parte deste repositório como app independente — não depende do código Python do
Agent Reach nem interfere nele.

## Modos

| Modo | Objetivo |
| --- | --- |
| 🔢 **Sequências** | Descobrir o item que falta numa sequência lógica (aritmética, geométrica, alternada, ciclo de formas, soma tipo Fibonacci). Atalho: teclas 1–4. |
| 🔍 **Ache o Intruso** | Encontrar, numa grade, o único item que quebra o padrão (forma, cor ou rotação). |
| 🧩 **Agrupar por Regra** | Selecionar todos os itens que seguem uma regra oculta (cor, forma, E/OU compostos). |
| 🧠 **Memória** | Memorizar um padrão que pisca (estilo Simon) e reproduzir na ordem; a sequência cresce por nível. |
| 🧮 **Cálculo Mental** | Resolver contas de cabeça (+, −, ×, ÷) com múltipla escolha; operações e números crescem por nível (× a partir do nível 3, ÷ exata a partir do 5). Atalho: teclas 1–4. |
| 📅 **Desafio Diário** | 10 rodadas fixas do dia (semente determinística — o mesmo desafio para todos), sem vidas; guarda o melhor diário e o histórico. |

## Progressão e pontuação

- **Dificuldade progressiva:** o nível sobe a cada 4 acertos e os geradores ficam mais difíceis.
- **Pontuação:** pontos-base + bônus por nível + **bônus de velocidade** (quanto mais rápido, melhor)
  × **multiplicador de streak** (acertos seguidos).
- **3 vidas:** errar ou deixar o tempo acabar custa uma vida; sem vidas, fim de jogo.
- **Recorde por modo** salvo no navegador (`localStorage`), além do melhor resultado do Desafio Diário.

## Acessibilidade

- Navegação por teclado (Tab/Enter; teclas 1–4 nas Sequências), foco visível, `aria-label`/`aria-live`.
- Respeita `prefers-reduced-motion` (desliga animações) e tem botão de **mudo** para os efeitos sonoros.

## Como rodar

O app é 100% estático (React via CDN, sem build). Escolha uma opção:

```bash
# a partir da raiz do repositório
cd games/pattern-trainer

# opção 1: servidor local (recomendado)
python -m http.server 8000
# depois abra http://localhost:8000

# opção 2: abrir o arquivo direto no navegador
#   basta abrir games/pattern-trainer/index.html
```

## Estrutura

Tudo vive em **`index.html`**:

- Geradores puros de rodada: `generateSequenceRound`, `generateOddOneOutRound`, `generateGroupingRound`.
- Telas: `HomeScreen`, `GameScreen`, `ResultsScreen`.
- Estado, cronômetro, vidas, streak e pontuação ficam em `GameScreen`; o recorde é persistido em `App`.
