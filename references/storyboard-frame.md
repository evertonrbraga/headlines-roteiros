# JSON completo aprovado → Frame

Ler [direcao-visual.md](direcao-visual.md) antes de selecionar apoios: a revisão de 30/10/2026 define a entrega visual e os campos fixos/dinâmicos. A skill termina no JSON; as operações de Frame descritas abaixo são próximos passos externos, somente mediante pedido próprio.

Toda aprovação explícita do roteiro gera **storyboard.json**, sem precisar pedir storyboard separadamente. O JSON é a entrega principal para copiar/colar no Frame: arquivo anexo completo, sem comentários, reticências ou resumo de campos. Mostrar um bloco JSON integral no chat somente quando solicitado. Texto de legenda separado acompanha quando solicitado. Antes da aprovação, manter apenas os parágrafos do roteiro de avaliação, sem códigos B/C, títulos, notas ou legendas. “Está tudo certo, é isso mesmo” e aprovações inequívocas equivalentes do roteiro inteiro iniciam esta entrega. Não iniciar edição no Premiere nem fazer deploy/publicação.

## Gerar o contrato completo

Usar o montador da skill irmã `roteiro`, preservando o texto literal, IDs B/C, ordem, modos e fechamento. Completar `shot_suggestion` e `support_queries` nos itens variáveis e, quando necessário, `take_suggestions` por segmento (inclusive fechamento) com direção específica para o case. Direções e buscas são propostas; quando houver vídeo acessível, completar a seleção com intervalos e primeiros quadros realmente inspecionados. Uma direção genérica ou capa não substitui o apoio real. Uma composição contínua é um take C; legendas e blocos B permanecem internos, sem fragmentar cartões por legenda.

```sh
python3 /Users/evertonbraga/.codex/skills/roteiro/scripts/montar_roteiro.py /caminho/partes-variaveis.json --output-dir /caminho/entrega --include-captions --title "Título do roteiro aprovado"
```

`storyboard.json` e `roteiro.json` aprovado contêm o mesmo documento completo e podem ser colados no app. Verificar que todas as cinco seções estão representadas: HISTÓRIA, CONCLUSÃO, CONEXÃO CTA, CTA Repolish e APRESENTAÇÃO. Não entregar somente `blocos.json` nesse fluxo, pois ele não contém todos os detalhes de legendas.

Campos principais:

- `version: 1`, `schema: frame-storyboard-v1`, `id`, `revision`, `title`, `script_format: roteiro_v1` e registro de aprovação.
- `blocks`, `narration_blocks` e `information_blocks`: roteiro integral, fontes dos trechos, índices de palavras, IDs B e vínculos aos itens C; preservar o fechamento literal e sua assinatura.
- `full_text`: a fala integral aprovada, com uma linha em branco entre unidades semânticas; `composition_options`: valores `split`, `edit`, `presenter`, com rótulos Tela dividida, Take cheio, Narração cheia; `editor_options`: texto editável, seleção exclusiva por take e grade de 1 a 30 colunas.
- `composition_blocks`: todos os takes C, com `id`, `mode` (`split`, `edit`, `presenter`), `text` integral do take, `text_editable: true`, `sections`, `information_block_ids`, `source_segments`, `narration_ids`, `duration`, `timing_is_estimate`, `effects`, `shot_suggestion`, `support_queries`, `caption_ids`, `captions`, `presenter_image`.
- `caption_blocks` e `caption_profile`: cada linha com texto final, spans, cores, fonte, face, tamanhos base/efetivo, tracking, caixa e intervalos de palavras. Perfil JetBrains Mono NL Regular/Italic, escala 118% aplicada uma vez, paleta, tarja Dracula, padding, altura uniforme e posição aproximada conforme `roteiro/assets/legendas-config-definitiva.json`. A apresentação inteira permanece branca/MAIÚSCULA/Regular/sem itálico.
- `editorial_rules`, `presenter_asset`, `segment_constraints` por take, `mode_locked`, `support_status`, `reference_library`, `references`, `reference_previews` e `visual_review`: regras fixas/dinâmicas, ativo de Everton, apoios e primeiros quadros inspecionados, conforme [direcao-visual.md](direcao-visual.md).
- `timing`, `caption_timing_pending_audio`, `fontes`, `notas` e regra de vínculo `reference_binding`.

Sem gravação, os tempos são estimativas. Não inventar timecodes sincronizados das legendas. A duração estimada do take serve para escolher apoios e pode ser ajustada pelo usuário. A foto padrão autorizada de Everton está em `/presenter/everton.png`; não reintroduzir avatar genérico. Preservar escolhas manuais e referências quando revisar um JSON exportado do Frame.

## Próximo passo externo — colar e ajustar apoios no Frame

No Frame, **Colar JSON → Montar storyboard** cria os cartões e mostra as legendas/direções. O usuário abre um vídeo do YouTube no player centralizado somente dentro do módulo do YouTube, com blur restrito a esse módulo e o storyboard livre à direita, reproduz com som e pausa no início desejado. Arrastar a imagem pausada para um take vincula `[momento pausado, momento pausado + duração do take]`. Exemplo: pause em 12 s + take de 4 s = 12–16 s. Se o vídeo acabar antes, manter o início escolhido e sinalizar o trecho menor; nunca deslocar silenciosamente o início para trás. Os vínculos, tempos, legendas e demais metadados são preservados na exportação.

## Ação adicional, somente quando solicitada — abrir no Frame

Checkout: `/Users/evertonbraga/Documents/ChatGPT/youtube-pinterest`.

```sh
node --experimental-strip-types /Users/evertonbraga/Documents/ChatGPT/youtube-pinterest/scripts/open-storyboard.mjs /caminho/entrega/storyboard.json --title "Título do roteiro aprovado"
```

Isso prepara o mesmo JSON em `public/storyboards/current.json`, localmente. Reutilizar a aba local aberta ou iniciar `npm run dev` no checkout e abrir a URL impressa no painel do Codex. Verificar o título e os takes à direita. A skill roda no Codex; o app apenas lê o arquivo/JSON. Abertura automática é local; o JSON pode ser colado diretamente na interface sem executar comandos.


**Marcadores de seção — orientação mais recente de 29/10/2026:** apresentar o roteiro com [HISTÓRIA], [CONCLUSÃO], [CONEXÃO CTA], [CTA] e [APRESENTAÇÃO] em linhas próprias, separados dos parágrafos de fala. Esta orientação substitui a proibição anterior de títulos apenas quanto a esses marcadores entre colchetes; continuam ausentes códigos B/C, números e rubricas técnicas. Os marcadores identificam seções e não são locução, texto editável do take nem legenda. Guardar a seção como metadado separado no JSON. Preservar todas as palavras do roteiro escolhido, removendo apenas resíduos de interface como “Annotation 1”.


## Referência do YouTube e takes coringa

Ao receber um link de vídeo na invocação de `headlines-roteiros` ou `roteiro`, extrair a biblioteca durante a pesquisa e conservar o resultado até a geração do storyboard aprovado. O extrator usa os quadros de contato disponibilizados pelo YouTube e fronteiras da transcrição. Mantém a cobertura do vídeo inteiro; vídeos muito longos usam até 2.000 amostras visuais além dos pontos da transcrição. Os cartões do app são carregados em lotes sem descartar a biblioteca.

```sh
node --experimental-strip-types /Users/evertonbraga/Documents/ChatGPT/youtube-pinterest/scripts/extract-youtube-references.mjs 'https://www.youtube.com/watch?v=VIDEO_ID' --output /caminho/entrega/referencias-youtube.json
```

Após a aprovação e geração do `storyboard.json`, para obter uma pré-seleção que ainda exige revisão visual, repetir com `--storyboard /caminho/entrega/storyboard.json` para incorporar a mesma biblioteca em `reference_library` e sugerir apoios pela transcrição. O comando preserva referências manuais e não vincula automaticamente trechos sem palavras de contexto em comum. Se já houver transcrição externa com tempos, aceitar `--captions /caminho/cues.json`, contendo `[{"start":0,"end":4,"text":"fala"}]` ou `{"cues":[...]}`. Não inventar tempos para texto sem marcação temporal. Atualizar também o `roteiro.json` da entrega se ele deve continuar sendo o mesmo documento completo.

Revisar a pré-seleção seguindo direcao-visual.md, substituir correspondências inadequadas e incorporar os primeiros quadros reais de cada intervalo. Inspecionar quadros e transcrição para refinar descrições e escolher takes pertinentes ao roteiro; o contexto automático representa a fala daquele intervalo, não uma descrição comprovada da imagem. O JSON da biblioteca contém `storyboard.detail` / `overview`, cujos templates e dimensões permitem localizar os quadros. Se a transcrição estiver indisponível, tentar o conteúdo do vídeo/transcrição pelo navegador conectado e registrar o que faltou. Não afirmar análise audiovisual completa quando só os metadados ou a capa estiverem acessíveis. A indisponibilidade deve acompanhar a entrega útil, sem inventar conteúdo ou esvaziar referências escolhidas.

O app também oferece **Referência do YouTube → Extrair takes**, busca por contexto e seleção manual em **Takes coringa**. O Rascunho mostra quadros estáticos e não monta players. **Detalhes** desmarcado deixa apenas a composição visual nos cartões. A grade aceita 1–30 colunas, reduzindo os cartões dentro da largura disponível. **Play geral** percorre os takes e as legendas com voz-guia pt-BR, pausa/continuação e ritmos até 4×. As legendas usam fronteiras da síntese quando disponíveis, com estimativa por palavras como alternativa; não são sincronização da gravação original.

**Renderizar** prepara a aba **Final** como prévia da sequência: os apoios vinculados são reproduzidos como vídeos reais nos seus intervalos, com a voz-guia e as legendas. Os cartões Final carregam players pausados apenas quando visíveis; o play geral reproduz um take por vez na prévia principal. O apresentador permanece com a foto de referência enquanto não houver gravação vinculada. Takes sem vídeo continuam identificados. Essa ação não exporta MP4 nem publica; revisões do rascunho entram no Final após **Atualizar renderização**. A velocidade suportada diretamente pelo vídeo depende das taxas liberadas pelo player do YouTube; a sequência mantém seu relógio de prévia.
