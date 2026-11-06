# Legendas — configuração definitiva aprovada em 29/10/2026

O usuário declarou “essa é a config definitiva das legendas” ao fornecer o [print de referência](evidencias/legendas-config-definitiva-2026-10-29.png). Este perfil substitui as escolhas anteriores de peso, paleta, padding e escala das legendas comuns. Não altera o tratamento separado da palavra de tensão do hook.

| Parâmetro | Valor aprovado |
|---|---|
| Família/peso | JetBrains Mono NL Regular, peso 400; Italic quando o modo pedir itálico |
| Escala global do bloco | 118% |
| Tamanho base branco / colorido | 33 / 36 px, em composição 1080 × 1920 |
| Tamanho efetivo branco / colorido | 38,94 / 42,48 px |
| Tracking branco / colorido | −20 / −50 na escala Illustrator, equivalentes a −0,02 / −0,05 em |
| Padding horizontal / vertical | 28 / 16 px antes da escala global |
| Padding total adicional | 0 |
| Padding efetivo horizontal / vertical | 33,04 / 18,88 px após 118% |
| Fundo da legenda | Dracula — #282A36 |
| Branco | #FFFFFF |
| Verde | #17F294 |
| Rosa | #FF6BA6 |
| Azul | #7CB4FD |
| Amarelo | #F99902 |

Aplicar a escala **uma única vez** ao bloco inteiro, incluindo tarja, margens e tracking. Não usar 38,94/42,48 como tamanhos base e aplicar novamente 118%.

O centro da legenda está aproximadamente em **50,4% da largura e 19,8% da altura**, posição superior inferida dos pixels do print; o print não informa coordenadas numéricas exatas. Em 1080 × 1920, equivale a aproximadamente x=544,3 / y=380,2. Preservar posição normalizada ao mudar a resolução. A posição inferior anterior não prevalece; a área segura continua sendo apenas uma referência editorial. Conferir legibilidade/interface na produção concreta.

O fundo da prévia sem imagem é Grafite/VS Code #1E1E1E e o ajuste da imagem é preencher quadro. A foto IMG_7102.PNG serve como referência visual da prévia, não como fundo obrigatório de outros vídeos; a largura da coluna de edição também não é parâmetro de exportação.

Mantêm-se: uma linha; tarja de altura uniforme para cada configuração, variando somente em largura entre legendas; acentos e cedilhas corretos; sem pontos, sem pontuação final e com vírgulas apenas internas; permanência até a próxima entrada. A altura base do bloco desta configuração é 74,2 px (envelope −34,2 a 8 px e padding vertical de 16 px por lado), equivalente a 87,556 px após 118%; não recalcular pela presença de Q/ç em cada linha.

## Modos preservados, agora com Regular/Italic

- Conteúdo: branco Regular MAIÚSCULO; destaque colorido Italic minúsculo
- Apresentação: **toda branca, Regular MAIÚSCULA e sem itálico** — correção posterior explícita do usuário em 29/10/2026
- CTA “já me segue” em diante: todo branco, Regular MAIÚSCULO sem itálico

Aprovação refere-se ao perfil visual exibido, não a uma nova versão do roteiro ou do motion HATERS. Texto e timecodes existentes continuam preservados.

Perfil reutilizável: `outputs/assinatura-auditiva/legendas/perfil-definitivo.json`, replicado em `~/.codex/skills/video-production/assets/legendas-config-definitiva.json` e nos campos de legenda de `assets/perfil.json` da skill.
