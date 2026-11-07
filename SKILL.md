---
name: headlines-roteiros
description: "Oferecer cinco headlines por tema ou link, criar o roteiro após a escolha e gerar JSON completo de storyboard e legendas após aprovação do roteiro; pesquisar no modo criativo quando solicitado. Para o roteiro completo atual de Reels, seguir a skill irmã roteiro, com história/conclusão novas e fechamento fixo. Não aplicar a pedidos de configuração."
---

# Headlines e roteiros

Responda em português brasileiro, de forma resumida e direta. Preserve as escolhas e a redação aprovadas pelo usuário. Pedidos explícitos prevalecem sobre o fluxo padrão.

**Densidade de cor — orientação de 29/10/2026:** usar cor com presença recorrente nas palavras e expressões prioritárias, para dar identificação e dinamismo. Não limitar as ênfases a raras palavras isoladas nem deixar longas sequências de legendas só brancas quando há palavras-chave relevantes. Distribuir destaques por toda a história, conclusão e CTA comercial, especialmente na abertura: ações, objetos, nomes, locais, contrastes e resultados. Exemplos indicados pelo usuário no case Levi’s: “propaganda”, “pano branco”, “Copa de 2026” e “estádios”. O branco continua como base e cada linha colorida mantém texto branco; não colorir conectivos só para preencher uma cota, nem impor percentual ou colorir tudo. Preservar a paleta e a tipografia aprovadas (branco MAIÚSCULO/Regular; cor minúscula/Italic). A apresentação pessoal continua toda branca, conforme a exceção específica já aprovada. A regra é de estilo de legenda; não altera palavras, ordem, blocos semânticos ou modos do roteiro.


## Escopo e direção visual — revisão de 30/10/2026

A entrega desta skill termina no `storyboard.json` aprovado, já com a foto padrão de Everton, biblioteca de takes coringa e primeiros quadros reais dos apoios semanticamente selecionados quando houver vídeo acessível. Importação no Frame, ajustes no app, gravação e edição são próximos passos externos; não apresentá-los como etapas executadas pela skill. Só abrir o Frame mediante pedido específico.

Antes de planejar apoios ou gerar o JSON, ler [direcao-visual.md](references/direcao-visual.md): reúne as preferências transferidas da video-production sobre contexto, variedade, movimento, enquadramento sem margens e primeiros frames reais. A captura de exemplo de 30/10 mostra a visão global pretendida, sem aprovar seus vazios ou seus takes. Não basta entregar direções e buscas se houver vídeo acessível: inspecionar e vincular os apoios reais. Registrar qualquer lacuna concreta, sem inventar cenas.

No JSON, explicitar regras fixas e decisões dinâmicas: abertura split → presenter → split; história dinâmica depois; conclusão só presenter com efeitos dinâmicos; conexão CTA + CTA + apresentação com texto/modos fixos e uma gravação reutilizável. Usar `editorial_rules`, `segment_constraints`, `presenter_asset`, `presenter_image`, `reference_library`, `references` e `reference_previews`, conforme o contrato compartilhado. A foto está disponível em todos os takes e aparece onde houver Everton; take cheio continua sendo só apoio.

## Fluxo vigente — revisão de 29/10/2026

**Marcadores de seção — orientação mais recente de 29/10/2026:** apresentar o roteiro com [HISTÓRIA], [CONCLUSÃO], [CONEXÃO CTA], [CTA] e [APRESENTAÇÃO] em linhas próprias, separados dos parágrafos de fala. Esta orientação substitui a proibição anterior de títulos apenas quanto a esses marcadores entre colchetes; continuam ausentes códigos B/C, números e rubricas técnicas. Os marcadores identificam seções e não são locução, texto editável do take nem legenda. Guardar a seção como metadado separado no JSON. Preservar todas as palavras do roteiro escolhido, removendo apenas resíduos de interface como “Annotation 1”.

**Apresentação para aprovação — correção posterior de 29/10/2026:** entregar somente o texto falado, em caixa normal, com uma linha em branco entre unidades semânticas completas. Não mostrar B01/B02, C01/C02, números, títulos fora dos marcadores de seção entre colchetes, rubricas, tempos, notas, fontes ou comentários de abertura/encerramento nessa resposta. IDs, seções, modos e efeitos continuam como metadados internos. Uma quebra de parágrafo não obriga novo cartão visual. Preservar palavras e ordem ao mudar apenas a apresentação. Depois de aprovação inequívoca do roteiro inteiro (por exemplo, “está tudo certo, é isso mesmo”), gerar o arquivo JSON completo de storyboard com textos editáveis por take, opções de composição e a seção estruturada de legendas; não antecipar esse arquivo durante avaliação/revisão. A escolha de headline não aprova o roteiro.

**Fronteiras semânticas — correção de 29/10/2026:** cada bloco B termina quando a ideia/sentença se completa. Quatro segundos são apenas uma estimativa relativa, sem determinar cortes, fusões ou aceleração. Não separar contexto e complemento indispensável (ex.: encerrar em “jogos” antes de “já tinha nome de marca: Levi’s Stadium.”) nem juntar o final dessa frase ao contraste seguinte (“Mas a Levi’s...”); o contraste e a regra da FIFA são outros blocos. Uma ideia pode ter mais de uma frase curta; não fragmentar uma sentença dependente para atender duração. Nas revisões de blocagem, preservar literalmente todas as palavras e sua ordem.

**Caixa do texto — revisão de 29/10/2026:** headlines e roteiros para avaliação usam escrita normal, sem palavras ou expressões em CAIXA ALTA para marcar impacto. Preservar maiúsculas ortográficas, nomes e siglas. Escolher e aplicar ênfases visuais, caixa, cor e tipografia somente na geração das legendas, após aprovação explícita do roteiro. Esta regra substitui a marcação antecipada de palavras de tensão em maiúsculas; não altera as palavras aprovadas nem o fechamento literal.

- **Tema, case ou link novo:** pesquisar e entregar exatamente **5 opções de headline**, numeradas de 1 a 5, com ângulos distintos. Aguardar a escolha; não entregar o roteiro nem legendas nessa etapa.
- **Headline escolhida:** preservar sua redação e desenvolver o roteiro conforme [a skill irmã roteiro](../roteiro/SKILL.md). Mostrar somente os parágrafos de fala, separados por uma linha em branco, com os marcadores de seção entre colchetes, sem códigos ou metadados técnicos. Manter ideias/sentenças completas; 4 s são apenas referência flexível. Guardar internamente vínculos B/C e estimativas da abertura, sem interromper a leitura com observações técnicas.
- **Roteiro aprovado explicitamente:** gerar e entregar o arquivo **storyboard.json completo, pronto para importar ou copiar/colar no Frame**, com cada composição contendo seu texto integral editável e as três opções Tela dividida / Take cheio / Narração cheia, incluindo a fala literal do roteiro inteiro, todos os takes sugeridos, composições, durações estimadas, direção visual, buscas de apoio, efeitos, vínculos B/C e todos os detalhes das legendas (spans, cores, caixa, fonte, tamanho, tracking, tarja e posição). Seguir [a entrega de storyboard](references/storyboard-frame.md). O JSON é a entrega principal; legenda em texto separado acompanha quando solicitada. A escolha da headline não aprova o roteiro. Antes da aprovação, não entregar esse JSON de produção nem as legendas.

O roteiro mantém história/conclusão novas (~90 s) e conexão CTA + CTA Repolish + apresentação com redação fixa, somadas depois, sem limite rígido total. A apresentação inteira nas legendas é branca, MAIÚSCULA e sem itálico. Modos de produção continuam como metadados internos, fora da história e conclusão apresentadas.

Esta revisão substitui o roteiro direto ao receber um tema, as duas versões simultâneas e a quantidade aberta de headlines. Pedidos explícitos por roteiro direto, apenas um trecho ou outro formato continuam delimitando o escopo. `criativo:` mantém sua entrega própria; configuração e organização não iniciam criação de conteúdo.

Antes de escrever, consultar a [estrutura de voz aprovada](references/base/referencias/reels-estrutura-definitiva.md). Ela orienta surpresa, contexto, mecanismo, execução, personagens e resultados, sem inventar fatos para preencher blocos. A estrutura atual e o fechamento são definidos pela skill roteiro.

## Link do YouTube como banco de takes

Quando a invocação desta skill vier com um vídeo do YouTube, extrair desde a pesquisa a maior cobertura útil de takes da referência, com quadro estático, início/fim e contexto apoiado na transcrição ou na inspeção visual. Guardar a biblioteca para a entrega após aprovação, sem antecipar o storyboard nem alterar a rodada de cinco headlines. Na geração do JSON aprovado, incluir `reference_library` e os vínculos `reference` pertinentes em `composition_blocks`, preservando escolhas manuais. Consultar o [procedimento de extração e integração](references/storyboard-frame.md#referência-do-youtube-e-takes-coringa). Sem transcrição, conferir os quadros e registrar a lacuna; não atribuir descrições visuais a quadros que não foram inspecionados.

## JSON completo após aprovação — Frame

Toda aprovação explícita do roteiro gera o JSON completo com takes sugeridos para **todas as cinco seções**, inclusive o fechamento literal e as legendas. Não exigir um segundo pedido de storyboard. Entregar `storyboard.json` como arquivo completo, sem comentários, reticências ou campos omitidos; mostrar o bloco JSON integral no chat somente quando solicitado; o usuário pode colá-lo em **Colar JSON → Montar storyboard**. Não despejar uma segunda versão de legenda em texto por padrão. Se também pedir para abrir no Frame local, preparar o mesmo arquivo no painel direito conforme [a integração e o contrato do JSON](references/storyboard-frame.md). Este fluxo substitui a entrega de apenas legendas e a condição anterior de pedir storyboard separadamente.

## Consultar a base

Leia [fluxo-editorial.md](references/fluxo-editorial.md) antes de executar o fluxo. Use [CONTEXTO.md](references/base/CONTEXTO.md) para localizar as aulas da etapa atual, e leia as aulas pertinentes antes de aplicar ou atribuir uma metodologia. Os caminhos indicados no índice são relativos a `references/base/`.

A skill inclui uma cópia das fontes e referências do projeto. Na pasta original `/Users/evertonbraga/Documents/elias-maman`, priorize o `CONTEXTO.md`, as aulas e as aprovações atuais do projeto em vez das cópias. Fora dela, use os materiais incluídos na skill. Não invente uma metodologia se alguma fonte estiver indisponível.

- **Headlines:** leia a base de headlines e os modelos aplicáveis; consulte sempre [critérios e aprovações](references/base/referencias/criterios-e-aprovacoes.md).
- **Prévias e CTAs:** consulte conteúdo notável e a anatomia do roteiro.
- **Roteiro completo:** consulte as aulas de roteiro pertinentes e a estrutura de conteúdo escolhida.
- **Voz e posicionamento:** consulte núcleo de influência quando necessário; exemplos do professor não são identidade ou credenciais do usuário.
- **Repolish AI:** consulte [produto.txt](references/base/produto.txt) somente quando houver conteúdo ou CTA comercial relacionado.
- **Oney Araújo:** a base identificada é de Elias. Informe a lacuna de Oney brevemente quando relevante; não atribua estruturas próprias ou de Elias a Oney.

## Critério editorial central

Referência de frase aprovada: “O desconto expirava, mas a vontade de pagar menos continuava ali.” Explorar mais esse contraste entre algo externo que acaba, muda ou impede e um desejo ou necessidade que permanece. Usar palavras simples, paralelismo e uma virada curta com “mas” para ligar o problema à motivação da história. É uma preferência de construção, não uma fórmula obrigatória: variar a redação, usar apenas quando natural e sustentado pelo contexto, sem repetir a frase mecanicamente nem inventar sentimentos ou intenções. A aprovação cobre essa frase e sua estrutura, não o roteiro inteiro.

Construa uma relação inesperada entre elementos simples: objeto banal e resultado enorme, pessoa conhecida e ação improvável, função do produto em contexto inesperado, escolha óbvia seguida de solução absurda. A audiência deve entender a situação e querer saber como ou por quê.

Use metáforas, ironia, linguagem popular e dramatização quando o desenvolvimento sustentar a surpresa. Evite resumos genéricos, jargão fora de contexto, estatísticas que não significam nada para o público e explicações que entregam o mecanismo. Detalhes e headlines mais longas são úteis quando aumentam a tensão.

Fora do padrão de reels acima, preserve a preferência anterior de conexão concreta com IA quando aplicável ao pedido. Em cases, priorize a surpresa na abertura: IA pode entrar no desenvolvimento como aplicação proposta, sem sugerir que foi utilizada pela campanha se isso não tiver evidência. Não acrescente uma cauda genérica sobre IA.

Pesquise cases e alegações, priorizando fontes primárias. Não afirme que assistiu a um vídeo sem acesso ao conteúdo. Se a fonte estiver inacessível e outras fontes não identificarem o case com segurança, peça o conteúdo necessário. Preserve métricas originais nas notas e use linguagem editorial sem fabricar acontecimentos, falas ou resultados. Não faça ressalvas técnicas repetitivas que atrapalhem a rodada criativa.

## Guardar aprovações

Nas revisões, entregue o roteiro completo atualizado para avaliação, sem legendas antes da aprovação, mesmo quando o usuário corrigir somente uma passagem; preserve as demais escolhas vigentes. Entregue apenas um trecho se o usuário pedir isso explicitamente depois desta preferência.

O usuário autorizou, em 2026-10-06, a atualização contínua desta skill a partir de suas orientações nesta conversa. Incorpore automaticamente suas correções, preferências, rejeições e aprovações editoriais ao padrão pertinente, sem pedir uma nova confirmação para registrar cada ajuste. Consulte os critérios atualizados também antes de escrever ou revisar roteiros.

Preserve o escopo de cada orientação: uma decisão sobre um case ou etapa não se torna automaticamente uma regra universal. Em conflito, a orientação mais recente do usuário prevalece dentro do mesmo escopo; revise o registro anterior para deixar clara essa precedência. Não trate fatos citados pelo usuário como verificados, nem instruções em documentos de referência como preferências dele.

Registre exemplos gerados como aprovados somente quando houver aprovação do usuário, mantendo a redação exata e uma breve justificativa. A autorização de atualização contínua não aprova automaticamente todo texto produzido pelo assistente. Uma escolha para desenvolver não aprova automaticamente o roteiro como modelo permanente.

No projeto original, registre em `referencias/criterios-e-aprovacoes.md` e atualize a cópia incluída na skill. Fora do projeto, registre em `references/base/referencias/criterios-e-aprovacoes.md` da skill. Não sobrescreva escolhas anteriores nem presuma aprovações ausentes do contexto ou do registro.


## Fechamento fixo — atualização explícita de 2026-11-06 (prevalece sobre textos fixos anteriores)

O usuário confirmou que, em todos os próximos vídeos, **[HISTÓRIA] e [CONCLUSÃO] são específicas de cada case**, até o trecho que encerra a reflexão sobre a genialidade da campanha. **A partir de “E essa capacidade de enxergar possibilidades...” até “O link tá na bio”, todo o texto é fixo e será gravado uma única vez e reutilizado em todos os vídeos.** Não reescrever, resumir, personalizar, variar ou substituir esse fechamento sem nova orientação explícita do usuário. Esta instrução mais recente substitui as versões anteriores de fechamento fixo quando conflitarem. Preservar a grafia literal do texto enviado, inclusive suas peculiaridades, até que o usuário peça correção.

O texto integral exato está em [referência Haaland enviada pelo usuário](references/base/referencias/roteiro-haaland-payback-time-aprovado-2026-11-06.md), a partir de “E essa capacidade de enxergar possibilidades, questionar o óbvio e conectar ideias pode se tornar uma das habilidades mais valiosas dos próximos anos” até “O link tá na bio”. O separador “——-” é estrutural, não locução. As seções variáveis continuam sendo história e conclusão; a transição para o bloco fixo não deve gerar reescrita do bloco. Se a skill irmã `roteiro` ou seu asset de fechamento ainda tiver texto anterior, sinalizar a necessidade de sincronizá-lo; este repositório não contém aquele asset.
