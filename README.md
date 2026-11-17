# 🏎️ Porsche Sales Intelligence — Dashboard Executiva Interativa

Dashboard interativa em arquivo único (`index.html`) desenvolvida como entrega prática do desafio **Criando Agentes de Tratamento de Dados** da **DIO**, transformando uma base de 100 registros de vendas da Porsche em insights visuais dinâmicos, sem as limitações de planilhas estáticas.

🔗 **Acesse a Dashboard Publicada:** [https://naiarasouuuza-droid.github.io/porsche-sales-dashboard/](https://naiarasouuuza-droid.github.io/porsche-sales-dashboard/)

---

## 🎯 Perguntas de Negócio Escolhidas (e Por Quê)

1. **Concentração Geográfica de Receita — *Quais estados lideram o faturamento da Porsche?***
   * **Por quê:** Identificar onde está o maior volume financeiro permite direcionar campanhas regionais e estoque. Na base, embora a Califórnia (`CA`) lidere em unidades vendidas (16 veículos), o **Texas (`TX`)** lidera em faturamento total (**US$ 2.023.400,50**) devido ao ticket médio mais elevado.
2. **Perfil Financeiro por Modalidade — *Qual método de pagamento gera maior receita total e qual possui o maior ticket médio?***
   * **Por quê:** Em vendas de alto luxo, entender como o cliente paga orienta parcerias financeiras. **Wire Transfer** concentra o maior volume (26 vendas / US$ 3,98M), enquanto **Crypto Payment** apresenta o maior ticket médio da operação (**US$ 180.500,00**).
3. **Mix de Portfólio e Eficiência Logística — *Qual família de modelos concentra o faturamento e como está o funil de entrega?***
   * **Por quê:** Avaliar a dependência de receita por linha de produto e gargalos operacionais. A família **911** representa **33,3%** de todo o faturamento (US$ 4,27M), seguida pela linha elétrica **Taycan** (US$ 2,33M). No funil logístico, **41%** dos veículos já constam como `Delivered`.

---

## 🧹 Tratamento e Sanitização da Base de Dados

* **Remoção de Dados Sensíveis (PII):** As colunas `customer_name` e `salesperson` foram excluídas para garantir que nenhum dado pessoal fosse exposto publicamente no código-fonte.
* **Seleção de Colunas Sanitizadas:** Mantidas apenas as colunas tratadas (`SaleDateSanitized`, `PorscheModelSanitized`, `ModelYearSanitized`, `SalesPriceSanitized`, `VehicleMileageSanitized`, `PayMethodSanitized`, `CitySanitized`, `StateSanitized`, `DeliveryStatusSanitized`) além do `sale_id`.
* **Tipagem Numérica Pura:** Preços, anos e quilometragem convertidos em valores numéricos puros (sem fórmulas ou texto).
* **Enriquecimento de Categoria (`ModelFamily`):** Agrupamento das 40 variações de modelos em 6 famílias principais (`911`, `Taycan`, `Cayenne`, `Panamera`, `Macan`, `718`) para leitura executiva clara.
* **Tratamento de Datas Inválidas:** Os `24` registros com `SaleDateSanitized = INVALID` foram preservados na base para rastreabilidade, optando-se por não utilizar a data como filtro principal.

---

## 🤖 Processo com Agente de IA & Evolução do Prompt

1. **Diagnóstico e Sanitização:** O agente auditou a planilha `.xlsx`, identificou os 24 registros `INVALID`, validou a receita total (**US$ 12.827.800,50**) e gerou a base limpa sem PII.
2. **Prompt Inicial:**
   > *"Crie uma dashboard executiva em arquivo único (`index.html`) usando Chart.js para analisar 100 vendas sanitizadas da Porsche, com paleta inspirada na marca (preto fosco, grafite e vermelho Guards Red), 4 KPIs de topo, filtros interativos (Família, Estado, Ano, Método de Pagamento e Status de Entrega) e gráficos respondendo às 3 perguntas de negócio."*
3. **Refinamentos:** Inclusão do botão **Limpar Filtros**, tabela dinâmica no rodapé e agrupamento dos status de entrega em 4 macro-categorias.

---

## 📂 Estrutura do Repositório

* `index.html` — Aplicação web completa (HTML + CSS + JavaScript + Chart.js + Base JSON sanitizada embutida).
* `README.md` — Documentação técnica e de negócio do projeto.
