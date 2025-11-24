🌍 TravelVision — Dashboard de Turismo & Hotelaria
Projeto completo de portfólio para Analista de Dados Sênior

📌 1. Visão Geral do Projeto

O TravelVision é um projeto completo de dados que simula a operação de uma rede hoteleira e plataforma de turismo, cobrindo:

Reservas, Hotéis, Quartos, Clientes, Canais de venda, Dados climáticos, Tendências por mês, estado e tipo de hospedagem

A base foi desenhada para permitir análises avançadas de Operações, Comercial, Financeiro e Experiência do Cliente, incluindo KPIs como:

ADR, RevPAR, Ocupação %, Receita, Cancelamento %, Satisfação, NPS, Receita por Canal e Custo Operacional Médio

O projeto inclui:

✔ Base de dados completa (250.000 registros na Fato)

✔ Script Python para geração da base

✔ Modelo estrela

✔ Medidas DAX

✔ Dashboard profissional (Power BI)

✔ Documentação técnica + análises + insights executivos

🎯 2. Objetivos

Demonstrar domínio em criação de dados realistas

Construir um modelo estrela limpo, escalável e sem ambiguidade

Criar dashboards executivos com storytelling analítico

Mostrar capacidade analítica nível sênior (finanças + operações)

Aplicar métricas avançadas do setor hoteleiro

Apresentar análises reais como se fossem de uma rede hoteleira

📚 3. Dicionário de Dados (Resumo)

'<img width="537" height="246" alt="image" src="https://github.com/user-attachments/assets/2a8e696c-fe45-4034-bd8e-8d223bc70a16" />'


'<img width="451" height="253" alt="image" src="https://github.com/user-attachments/assets/77dc7ce4-fe18-40d8-bf0f-a83aaf03c9be" />'


'<img width="432" height="220" alt="image" src="https://github.com/user-attachments/assets/d92ff73c-c0eb-4410-8bea-f0a6cfe3d3bb" />'


'<img width="428" height="214" alt="image" src="https://github.com/user-attachments/assets/efacf817-4355-4ef7-9010-2241a0ffa81c" />'


'<img width="433" height="220" alt="image" src="https://github.com/user-attachments/assets/14b3f111-311b-4621-b7c3-a88712e097a6" />'


'<img width="565" height="99" alt="image" src="https://github.com/user-attachments/assets/4fc70e0a-2974-487d-a92a-5def5d2c0eff" />'

📈 4. MEDIDAS DAX (Todas as principais)

Receita & Tarifas

Receita Total = SUM(Fato_Reservas[Valor_Total])

ADR = AVERAGE(Fato_Reservas[Valor_Diaria])

Noites Vendidas = SUM(Fato_Reservas[Noites])

Ocupação — MEDIDA CORRETA

Quartos Disponiveis =
VAR Dias =
    CALCULATE( DISTINCTCOUNT( Dim_Tempo[Date] ) )
RETURN
    SUMX(
        Dim_Hotel,
        Dim_Hotel[N_Quartos] * Dias
    )

Quartos Ocupados = SUM(Fato_Reservas[Estadia_Realizada])

Ocupacao % = DIVIDE([Quartos Ocupados], [Quartos Disponiveis])

Cancelamentos

Cancelamentos = CALCULATE(COUNTROWS(Fato_Reservas), Fato_Reservas[Cancelamento] = 1)

Cancelamento % = DIVIDE([Cancelamentos], [Total Reservas])

Satisfação & NPS

Satisfacao Média = AVERAGE(Fato_Reservas[Satisfacao])

NPS =
VAR Promotores = CALCULATE(COUNTROWS(Fato_Reservas), Fato_Reservas[Satisfacao] >= 9)
VAR Detratores = CALCULATE(COUNTROWS(Fato_Reservas), Fato_Reservas[Satisfacao] < 7)
VAR Total = COUNTROWS(Fato_Reservas)
RETURN DIVIDE(Promotores - Detratores, Total)

YoY e MoM

Receita Ano Ant =
    CALCULATE([Receita Total], DATEADD(Dim_Tempo[Date], -1, YEAR))

Receita YoY % =
    DIVIDE([Receita Total] - [Receita Ano Ant], [Receita Ano Ant])

Receita Mes Ant =
    CALCULATE([Receita Total], DATEADD(Dim_Tempo[Date], -1, MONTH))

Receita MoM % =
    DIVIDE([Receita Total] - [Receita Mes Ant], [Receita Mes Ant])

📊 5. Dashboards (Com layout oficial)

🧭 Página 1 – Resumo Executivo

<img width="875" height="654" alt="image" src="https://github.com/user-attachments/assets/3545cf77-ed97-4a59-97cc-b29332616a4f" />


KPIs principais

Tendência mensal (Receita, Ocupação, ADR)

Top 10 Hotéis

Receita por Canal

Insights Automáticos

📣 Página 2 – Vendas & Canais

<img width="730" height="682" alt="image" src="https://github.com/user-attachments/assets/a57f80d8-e9be-4aaa-8b7e-87b91491668b" />


Receita por Canal

Investimento × Conversão

Scatter (ADR vs Ocupação)

Tabela com KPIs por canal

🏨 Página 3 – Operações & Hotelaria

<img width="729" height="683" alt="image" src="https://github.com/user-attachments/assets/da817dce-35a7-48c1-bec1-99b2432e3db1" />


Heatmap Ocupação × Estado × Mês

Custo Operacional Médio por tipo de quarto

ADR por tipo de quarto (linha suave)

Tabela Operacional

😊 Página 4 – Experiência do Cliente

<img width="584" height="645" alt="image" src="https://github.com/user-attachments/assets/499e543c-fc52-4e36-8853-775fdedb83ed" />


NPS

Satisfação por Estado e por Canal

Satisfação vs Clima (scatter)

Perfil do Cliente

📈 Página 5 - Operações & Hotelaria

<img width="875" height="709" alt="image" src="https://github.com/user-attachments/assets/d7ab6cae-8ad1-47a3-bcdb-072234db3051" />


Ocupação % por Estado × Mês

Custo Operacional Médio por Tipo Quarto

ADR Médio por Tipo de Quarto

Desempenho Operacional por Tipo de Quarto

🔍 6. Análises

📌 1. Sazonalidade clara nos meses de Julho e Dezembro

Ocupação chega a 92% no Nordeste

ADR aumenta até 35% em Resorts

Fato: alta temporada + férias escolares

📌 2. Canais Online dominam a receita

Booking e Expedia representaram 58% da receita

Canal Direto cresce MoM mas ainda tem ADR menor

Agências físicas têm maior taxa de cancelamento

📌 3. Quartos de categoria Luxo representam maior margem

ADR até 3,5x maior

Custo Operacional cresce pouco (+15%)

Resultado: melhor margem do portfólio

📌 4. Clima influencia comportamento

Estados com dias nublados têm queda de 12% na satisfação

Em clima chuvoso, cancelamento sobe 8%

📌 5. Cancela muito quem reserva cedo

Antecedência > 50 dias → maior taxa de cancelamento

Insight: política de pré-pagamento pode reduzir perdas

📌 6. Hotel econômico é o mais sensível ao preço

ADR sobe → Ocupação cai

ADR cai → Ocupação explode
Estratégia: yield baseado em elasticidade.

⚙ 7. Script Python para gerar a base

Ele gera:

250.000 reservas

Com sazonalidade real

ADR por estado e categoria

Cancelamentos realistas

Satisfação coerente

Clima integrado

Custos operacionais reais por tipo de quarto

🧪 8. Qualidade e validação

✔ Sem valores nulos nas chaves

✔ Tipos de dados corretos (Date, int, float)

✔ Relacionamentos 1:N sem ambiguidade

✔ Coerência estatística:

ADR cresce na alta temporada

Ocupação acompanha clima

Cancelamento depende do canal

Custo operacional maior em quartos de luxo

Satisfação correlacionada com clima bom (> 0.42)

✔ Distribuições naturais (não artificiais)

🧩 9. Próximos passos

Criar previsão de demanda (Prophet ou ARIMA)

Criar modelo de recomendação de preço (price optimization)

Configurar Data Lake / Parquet

Criar API fake para simulação

Migrar o dashboard para Power BI Service

👤 10. Autor

Analista de dados - Guilherme Alencar
Projeto desenvolvido para portfólio profissional.
