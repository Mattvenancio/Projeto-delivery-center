📊 Delivery Center — Inteligência & Analytics Operacional

Solução analítica e executiva desenvolvida para monitoramento de ponta a ponta de operações de entrega urbana (last-mile) em quatro regiões metropolitanas (São Paulo, Rio de Janeiro, Curitiba e Porto Alegre). O painel centraliza resultados comerciais, auditoria de SLA de entrega, gargalos operacionais e cobertura de parceiros.

🖥️ Visão das Telas do Painel

1. Visão Executiva & Comercial

Acompanhamento dos principais indicadores de vendas, distribuição por canal e métodos de liquidação financeira.


GMV Transacionado: R$ 38,8M (R$ 39M)

Volumetria de Pedidos: 369K pedidos (368.999)

Ticket Médio: R$ 105,15

Cancelamentos: 17K pedidos (taxa global de 4,6%)

Destaque para o canal Food Place (R$ 25M) e predominância de pagamentos online (R$ 31,85M).

2. Operações, Logística & SLA

Monitoramento de tempos de resposta, cumprimento de janelas operacionais e eficiência logística.


Cumprimento do SLA de 45 min: 99,10% de entregas no prazo

Custo Médio de Entrega: R$ 7,58 por entrega concluída

Tempo Médio de Atendimento: 42,17 minutos

Decomposição de Gargalos (Parâmetro de Campo):

Produção: 62,29 min

Trânsito: 46,63 min

Coleta: 2,75 min

Análise comparativa de modal: Motoboy (maior volume e menor raio médio) vs. Biker.

3. Parceiros & Cobertura Geográfica

Mapeamento de capilaridade e distribuição de demanda por praça operacional.


Lojas / Restaurantes Ativos: 951

Hubs Operacionais: 32

Entregadores Parceiros: 4.570

Faturamento Médio por Parceiro: R$ 40,80K

Concentração de volume liderada por São Paulo (168K pedidos / R$ 21,4M) e Rio de Janeiro (138K pedidos / R$ 12,3M).

🏗️ Arquitetura do Modelo Dimensional (Star Schema)

A modelagem foi desenhada sob o conceito de Star Schema (Esquema Estrela) com relacionamentos unidirecionais Muitos para 1 (*:1), assegurando consistência analítica e performance na engine VertiPaq:

fOrders (Fato Principal): Granularidade por pedido (order_id), consolidando timestamps do ciclo de entrega, distâncias, custos logísticos e status da operação.

fPayments (Fato Paralela): Granularidade por transação (payment_id), gerenciando pedidos com métodos de pagamento combinados sem duplicar receita bruta.

dStores: Dados cadastrais das lojas parceiras, cidades e hubs vinculados.

dChannels: Canais de venda e plataformas integradas.

dCalendario: Tabela dimensional contínua de datas para análise de sazonalidade e inteligência temporal.

⚡ Governança e Otimização com Measure Killer

O modelo semântico passou por auditoria detalhada via Measure Killer:

Eliminação de Colunas Ociosas: Remoção de colunas não utilizadas em visuais, filtros ou relacionamentos, otimizando o consumo de memória RAM.

Governança DAX (22 Medidas Homologadas):

Emprego de KEEPFILTERS na métrica de cancelamentos para respeitar seleções de tela do usuário.

Uso de ALL(coluna) no denominador de taxas para blindar cálculos percentuais contra filtros pontuais de linha.

📁 Organização do Repositório

├── Base de dados/              # Arquivos de dados compactados (.zip)
├── Layouts/                    # Capturas de tela e temas visuais (.png)
├── Report BI/
│   └── PBIP/                  # Arquivo .pbip e estrutura completa compactada (.zip)
├── documentacao_tecnica_pbip_datalp.pdf # Manual técnico completo da solução
└── README.md                   # Vitrine e documentação oficial do repositório


🚀 Como Executar o Projeto

Acesse o diretório Report BI/PBIP/.

Baixe o arquivo compactado contendo as definições do projeto.

Descompacte os arquivos mantendo o arquivo Report Delivery Center.pbip junto às pastas .Report e .SemanticModel.

Abra o arquivo Report Delivery Center.pbip no Power BI Desktop.
