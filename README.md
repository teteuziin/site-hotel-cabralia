# Site — Hotel para Cães e Gatos Cabrália (@hotelparacaessalvadorbahia)

Site-modelo da fase 2 da missão de prospecção (empresa nº6), construído a partir do portfólio real do hotel. **NÃO PUBLICAR sem aprovação do usuário** — publicação no GitHub/Pages somente após o OK dele.

## Conceito — "O Pequeno Paraíso"
Palavras da própria Sofia Duarte, sócia-proprietária, no institucional dela: é assim que ela chama o lugar. Identidade ensolarada de clube de praia: base clara (areia/branco) + o azul da marca como acento (vermelho e amarelo só dentro da logo e das artes deles), molduras limpas e arredondadas, Baloo 2 (display amigável) + Nunito. Um único acento: o azul.

## Estrutura
- `index.html` — página única (intro temática de 1,6s pulável com a logo e uma barra de sol nascendo, hero com a logo transparente + slogan "Orgulho de ser Baiano" + vídeo do feriadão em autoplay mudo com botão "Ouvir com som", Atrações, Hospedagem de cães + tour do gatil, Creche, Natação canina em faixa azul, A família Cabrália, Feriadões e festas, Reservas com montador que abre o WhatsApp deles com a mensagem montada, Visite-nos, rodapé e botão flutuante de WhatsApp)
- `media/` — 13 vídeos reais deles (todos com áudio AAC), pôsteres extraídos de frames reais dos próprios vídeos, 2 fotos da rotina da creche (frames do vídeo do feriadão) e a logo transparente

## Logo sem fundo (instrução do usuário)
Gerada a partir da arte clássica em alta (`../hotel-cabralia-pet-portfolio/marca/logo-classica-fundo-branco-2848.jpg`, 2848×1930): recorte só da arte (casinha com cão/gato + "hotel para cães e gatos" + "cabrália"), **descartada a faixa inferior com os telefones antigos impressos**, e o fundo branco foi removido por flood-fill a partir das bordas (rotulação de componentes conexos) — os brancos internos da arte (olhos dos animais, contrafortes das letras) foram preservados. Resultado: `media/logo.png` (1800×845, PNG com transparência real, conferida sobre fundo claro e escuro). O slogan "Orgulho de ser Baiano" entra como texto do site (é o H1), não dentro da logo.

## Conteúdo — só o verificado (ficha: ../hotel-cabralia-pet-portfolio/README.md)
- Nome correto: **Hotel para Cães e Gatos Cabrália** (nunca "Hotel Cabrália Pet"), em **Vilas do Atlântico, Lauro de Freitas/BA** — endereço público completo no Visite-nos
- Fatos: 12 anos de experiência · nota 4,9 no Google (68 avaliações) · desde 2014 (na frase de aniversário deles, na seção da família)
- WhatsApp público confirmado (publicado por eles): (71) 99937-4215 — todos os CTAs e o montador apontam para ele; o segundo número que circula (99602-1205) ficou fora, como instruído
- Serviços confirmados: hospedagem de cães (salas amplas com sofás e camas — "nada de celas", nas palavras deles; separação por porte; monitoramento 24h da equipe; ração Royal Canin inclusa; avaliação de saúde na chegada), hospedagem de gatos em gatil climatizado, creche 100% solta (07h–19h, do folder oficial), Praia Pet exclusiva, natação canina feita pessoalmente pela Sofia, discoteca canina, adestramento com o Duarte sob orçamento, Taxi Dog
- Horários: creche 07h–19h (só na seção da creche); atendimento seg–sáb 8h–18h (só no Visite-nos)

## PREÇOS — decisão registrada: NENHUM valor em R$
As únicas tabelas deles (hotel e creche) vivem numa página Wix antiga, com vigência NÃO confirmada para nov/2026. O site imprime **zero valores em R$** (conferido por grep: 0 ocorrências de "R$") e vende a reserva pelo WhatsApp, que é como eles operam hoje — o montador avisa que valores e disponibilidade se confirmam na conversa.

## Escolhas sinalizadas
- **Vídeo 14 ("drone"):** conferi os frames antes de legendar — o vídeo é o especial do Dia das Crianças Pet (21/09/2026): arte de abertura da campanha + Praia Pet, discoteca canina e natação. Nos frames amostrados (3s, 20s, 40s, 60s, 82s) **não há tomada aérea clara** — a legenda afirma só o que o vídeo mostra ("Três atrações num dia só"), sem mencionar drone.
- **Seção de creche sem vídeo próprio:** o reel dedicado da creche (item 12 do catálogo) foi apagado por eles do Instagram. A seção se ancora no texto (day care 100% solto, 07h–19h) + 2 fotos que são frames reais do vídeo 02 (45s: turma na Praia Pet; 76s: área coberta com as caminhas e a Natasha) — o arquivo de vídeo 02 aparece como player uma única vez (no hero), como todos os outros.
- **Vídeo 13 (família/reabertura) é 360×640:** exibido contido em moldura de no máximo 320px — nunca esticado.
- **Recompressões:** os 9 vídeos acima de 25 MB (26–37 MB) foram recomprimidos para 19,3–20,4 MB (H.264, preset veryfast, CRF 24, teto de 1700 kbps, áudio AAC 96k), mantendo 720×1280 — todos abaixo do limite de 25 MB/arquivo do GitHub. Os demais (06, 07, 09, 13) entraram como vieram.
- Fora do site, de propósito: banho e tosa (não divulgam grooming — "banho de piscina" é socialização), câmera/aplicativo para o tutor (o monitoramento 24h é da equipe), endereço antigo de Buraquinho, telefones antigos da arte da logo, preços do Wix.

## Checagens feitas na construção
- ffprobe arquivo a arquivo no pacote final: 13/13 vídeos com faixa de áudio AAC; 720×1280 ×12 e 360×640 ×1 (contido); maior arquivo 20,4 MB — todos abaixo de 25 MB; pacote total ~219 MB
- Interações testadas em jsdom (32 asserções, 0 falhas): intro que fecha no clique e é removida do DOM, menu mobile, reveal por fallback, montador completo (hospedagem/creche, cão/gato com porte desligado para gato, nome do pet, datas formatadas dd/mm/aaaa, href do wa.me carregando exatamente a mensagem montada, saída escondida na creche com rótulo trocado), botão "Ouvir com som" do hero (desmuta, ganha controls, sai do modo ambiente), ano dinâmico do rodapé
- Contraste calculado: 11 pares texto×fundo, todos WCAG AA — pior caso 4,97:1 (azul de acento sobre areia); texto principal 11,17:1 sobre areia e 12,14:1 sobre branco; branco sobre a faixa azul 9,61:1
- Anti-duplicação: cada vídeo é player em exatamente 1 seção (grep por src: 1 ocorrência cada); cada fato uma vez (nota do Google, 12 anos, horários, endereço completo, Royal Canin, monitoramento 24h, Taxi Dog); "R$" com 0 ocorrências; termos proibidos com 0 ocorrências (banho, tosa, câmera, aplicativo, Buraquinho, "Cabrália Pet", telefones antigos/secundário, Wix)
- Todas as referências de mídia do HTML resolvem para arquivos do pacote; zero base64/data URI em vídeo; cursor apenas o nativo
