# Direção visual do JSON — preferência de 30/10/2026

## Escopo da entrega

A headlines-roteiros termina na entrega de `storyboard.json`, com fala, legendas, propostas de composição, foto de Everton e apoios reais selecionados. Importar no Frame, experimentar opções, gravar e editar no Premiere são próximos passos do usuário, fora do fluxo automático desta skill. Não abrir o app nem iniciar edição só porque o roteiro foi aprovado. A aprovação do roteiro continua necessária antes de entregar o JSON de produção.

A imagem de storyboard enviada em 30/10 é referência da visão global desejada (composição + quadro real + fala), não aprovação das escolhas, margens, fundos, cortes ou repetições nela presentes. Não usar a captura de tela como fonte dos takes ou fingir que ela fornece seus timecodes.

## O que é fixo e onde há dinamismo

- Abertura fixa: tela dividida com rising → flare/flash de câmera → narração cheia (Everton) com complemento → retorno à tela dividida. Preservar os três modos iniciais, independentemente do case. O apoio da abertura é escolhido pelo significado, não é sempre a mesma cena.
- História após essa abertura: alternância dinâmica, motivada pela fala, entre dividida, narração cheia e take cheio. Verde desenvolve com apoio e apresentador; azul valoriza fala direta/conexão/reação; rosa destaca ação/revelação/prova. Distribuir acentos ao longo da história; retomar o narrador para explicar. Não usar rotação mecânica nem quotas de layout.
- Conclusão: somente Everton em tela cheia. Sem apoio nem tela dividida. São dinâmicos os pontos e intensidades de flare, zoom sutil e SFX; a restrição de modo permanece fixa.
- Conexão CTA, CTA e apresentação: copiar texto e sequência de modos do fechamento aprovado da irmã roteiro. O usuário vai gravar um único fechamento reutilizável em todos os vídeos. Usar `reusable_recording_id: everton-fechamento-v1`, com os IDs de origem, e não criar um novo encerramento nem apoios específicos de cada case para substituí-lo. Até a gravação existir, usar a foto na prévia e registrar a gravação pendente.
- Todos os textos ficam preservados após aprovação. Dinamismo visual não autoriza reescrever a fala. Um cartão C corresponde a um modo contínuo; mudanças internas de apoio ficam em `references` e não fragmentam cartões por legenda.

O gerador registra essas regras em `editorial_rules` e em `segment_constraints` por trecho de origem. `mode_locked` indica restrição, não uma trava já implementada na interface. Alterações manuais explícitas do usuário prevalecem e devem atualizar a decisão e a regra correspondente, sem renumerar os IDs.

## Foto padrão e takes coringa

Usar a foto autorizada em `/presenter/everton.png` em TODOS os itens como `presenter_image`, com o ativo padrão em `presenter_asset`. Ela aparece abaixo no split e ocupa o quadro em presenter. Em edit, permanece disponível no metadado para mudar a composição, mas a imagem visível é só o apoio. Nunca usar avatar genérico ou uma pessoa do vídeo de referência no lugar de Everton.

`takes coringa` significa a biblioteca de trechos reais da referência, com tempo e contexto, em `reference_library`. Ela acompanha o JSON quando houver vídeo fornecido; não substitui a seleção principal. Entregar os apoios já contextualizados nos takes pertinentes, em vez de obrigar o usuário a escolher todas as imagens depois.

## Critérios transferidos da video-production

A ordem de escolha é significado preciso → leitura/enquadramento → ação/movimento → estética. Para cada apoio, registrar a ideia falada (`story_beat`), a razão do layout (`layout_reason`) e o que a imagem ilustra/comprova (`selection_reason`). Conferir personagem, produto, campanha, lugar e momento. Não usar uma cena parecida de outro case como prova nem preencher lacunas com imagem semanticamente errada.

Dentro das cenas corretas, preferir ação legível, movimento ou transições pertinentes. Não antecipar um assunto novo enquanto a voz ainda fala do anterior. Dar tempo para compreender gestos, títulos e resultados. Não preencher com borrão, mão isolada, cabeça cortada ou um frame de transição sem sentido.

Evitar repetição perceptível de ações. Se a mesma ação continua, continuar seu timecode; não reiniciar a mesma imagem em cada bloco. Para ideias diferentes, preferir ações ou planos diferentes. Pequeno offset ou outro zoom no mesmo gesto não é alternativa editorial. Se só houver poucas fontes adequadas, manter a coerência e registrar a lacuna em vez de forçar variedade errada.

Apoios têm áudio original desabilitado na edição futura. Não copiar tempos da montagem Haaland como fórmula. Música e bruto ainda ausentes não impedem o planejamento: durações são estimadas e a quantização 4/4 fica pendente da música real; não inventar BPM, cortes musicais nem sincronismo com fala ainda não gravada.

## Enquadramento sem margens

Prévia vertical 9:16, split exato 50/50, sem bordas, padding, gaps nem moldura dentro da composição. Espaços entre cartões de uma grade não são margens da imagem.

Identificar a imagem útil dentro da fonte, inclusive quando há preto embutido. Calcular crop, escala e posição por fonte E por layout; não reutilizar automaticamente um crop 50/50 no take cheio. Usar o menor zoom que preencha e preserve rostos, ações, produto e textos/números relevantes inteiros. Não deformar a imagem para preencher. A foto do apresentador também preenche sua área, com rosto alinhado pelos olhos.

Se preencher cortar informação essencial, primeiro reenquadrar, escolher outro intervalo/plano ou uma composição adequada. Fundo derivado/desfocado com primeiro plano grande é alternativa para preservar informação; não criar barras ou margens automáticas, não reduzir o assunto a uma miniatura sobre borrão decorativo. Não copiar os vazios da captura de exemplo.

Excluir legendas externas descartáveis por recorte quando viável, preservando títulos, marcas, números e textos que pertencem ao acontecimento. Conferir início, meio e fim do trecho em movimento; um primeiro frame bom não comprova que o rosto continua dentro do crop.

## Primeiro quadro real de cada apoio

1. Extrair/indexar os takes desde a pesquisa, mantendo a rodada de cinco headlines. Após aprovação, escolher os intervalos para a fala e inspecioná-los visualmente.
2. Para cada apoio selecionado, obter uma imagem real exatamente em `sourceIn` (primeiro quadro utilizado), não a capa do vídeo nem uma imagem ilustrativa. Guardar a imagem junto da entrega e usar URL/asset utilizável pelo destino. É permitido extrair quadros de vídeo acessível com ferramentas de mídia; não sintetizar nem retocar o conteúdo como se fosse evidência real.
3. Os quadros de contato do YouTube servem para localizar cenas; são amostras. Se não coincidirem com a entrada exata, não os chamar de primeiro frame: obter o quadro exato pelo vídeo acessível ou registrar a limitação. Não inventar tempos para transcrição sem marcação temporal.
4. Guardar `references` com os intervalos de origem e enquadramentos, `reference_previews` com o primeiro quadro de CADA apoio e `image` com o primeiro apoio do cartão. A foto de Everton completa a prévia de split/presenter. O texto integral do cartão permanece editável.
5. Só marcar `support_status: selected_first_frames_inspected` quando as imagens tiverem sido vistas e o vínculo semântico conferido. Se o acesso impedir a extração, manter `pending_selection`, listar o take em `visual_review.pending_take_ids` e informar a lacuna; entregar buscas/sugestões não equivale à entrega visual pronta.

O extrator automático por palavras é pré-seleção, não decisão final. Revisar falsos positivos, repetições, adequação de personagem e crop antes da entrega. Não substituir referências manuais exportadas do Frame.

## Campos da entrada para o montador

Além do roteiro, a entrada pode conter `reference_library` e `visual_plan`, um objeto indexado por IDs C do mapa técnico. Gerar/consultar esse mapa antes de compor o plano; depois executar novamente com `--include-captions`, sem mudar fala ou IDs.

Cada item de `visual_plan` aceita `story_beat`, `layout_reason`, `references` e `reference_previews`. Cada referência usa o contrato existente: `video` (id, title, channel, duration, thumbnail, views, isShort), `sourceIn`, `sourceOut`, `sourceDuration`, `requestedDuration`, `truncated` e `framing` (x, y, scale). Os intervalos devem cobrir a duração estimada do item; as divisões internas têm função semântica.

Cada preview contém `image` (asset `/storyboards/...` ou URL HTTPS utilizável), `seconds` igual a `sourceIn`, `inspected: true`, `exact: true` e `selection_reason`. O booleano é o registro de uma conferência efetivamente feita, não autorização para inventá-la. O montador valida estrutura e cobertura, não reconhece imagens nem comprova semântica. Arquivos locais dos quadros também devem acompanhar a entrega, com caminhos correspondentes no manifesto de assets quando necessário.

O JSON informa regras fixas, escolhas dinâmicas e pendências. Ter só um caminho de foto, capa do vídeo ou termos de busca não constitui storyboard visual finalizado. A fidelidade do primeiro quadro no visualizador depende de ele usar o asset exato fornecido; não declarar que uma interface baseada apenas em quadros amostrados já mostra esse instante exato.
