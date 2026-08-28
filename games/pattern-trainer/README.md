# Pattern Trainer 🧠

Um pequeno jogo (React, arquivo único) para **treinar o reconhecimento de padrões**.
Faz parte deste repositório como app independente — não depende do código Python do
Agent Reach nem interfere nele.

## Modos

| Modo | Objetivo |
| --- | --- |
| 🔢 **Sequências** | Descobrir o item que falta numa sequência lógica (aritmética, geométrica, alternada, ciclo de formas, soma tipo Fibonacci). |
| 🔍 **Ache o Intruso** | Encontrar, numa grade, o único item que quebra o padrão (forma, cor ou rotação). |
| 🧩 **Agrupar por Regra** | Selecionar todos os itens que seguem uma regra oculta (cor, forma, E/OU compostos). |

## Progressão e pontuação

- **Dificuldade progressiva:** o nível sobe a cada 4 acertos e os geradores ficam mais difíceis.
- **Pontuação:** pontos-base + bônus por nível + **bônus de velocidade** (quanto mais rápido, melhor)
  × **multiplicador de streak** (acertos seguidos).
- **3 vidas:** errar ou deixar o tempo acabar custa uma vida; sem vidas, fim de jogo.
- **Recorde por modo** salvo no navegador (`localStorage`).

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
