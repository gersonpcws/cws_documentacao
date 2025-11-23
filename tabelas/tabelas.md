# Documentação do Modelo de Dados


# 📊 Tabela: `dvendedores`
---

## 📌 Descrição Geral

A tabela **dvendedores** é uma dimensão essencial do modelo de dados, responsável por armazenar as informações cadastrais, hierárquicas, geográficas e comerciais dos vendedores.
Cada registro representa um vendedor único e centraliza os principais atributos relacionados ao seu perfil, canal de origem, área de atuação e relacionamento com clientes.
Essa dimensão serve como base para análises de performance de vendas, acompanhamento de metas, segmentação comercial, hierarquias de equipe e cruzamentos com fatos de vendas, clientes e tempo.

---

## 📑 Descrição das Colunas

### **account_id (INTEGER)**

Identificador único do vendedor no sistema. Atua como chave primária da dimensão e é utilizado para junções com tabelas fato e outras dimensões.

### **account_create_date (DATE)**

Data de criação da conta do vendedor. Permite medir o tempo de atividade e histórico de ingresso no sistema.

### **client_id (INTEGER)**

Identificador do cliente principal vinculado ao vendedor. Usado como chave estrangeira em integrações com dimensões de clientes.

### **client_status (BOOLEAN)**

Indica se o cliente vinculado ao vendedor está ativo (**TRUE**) ou inativo (**FALSE**). Facilita análises de relacionamento e carteira ativa.

### **account_origin (VARCHAR(50))**

Canal de origem do cadastro do vendedor (ex.: aplicativo, plataforma web, integração).

### **client_create_date (DATE)**

Data de criação do cliente vinculado ao vendedor, usada para análises históricas de relacionamento.

### **name (VARCHAR(150))**

Nome completo ou razão social do vendedor.

### **contact (VARCHAR(150))**

Nome do contato principal do vendedor, utilizado para comunicações comerciais.

### **account_user (VARCHAR(150))**

Login ou e-mail de acesso à conta do vendedor, utilizado para auditoria e autenticação.

### **document (VARCHAR(20))**

Documento identificador do vendedor (CPF ou CNPJ), usado para validações fiscais e integração entre sistemas.

### **gender (VARCHAR(20))**

Gênero informado no cadastro, quando disponível.

### **person_type (VARCHAR(10))**

Tipo de pessoa jurídica: **PF** (Pessoa Física) ou **PJ** (Pessoa Jurídica).

### **age (INTEGER)**

Idade do vendedor, derivada da data de nascimento.

### **country (VARCHAR(50))**

País de origem ou atuação do vendedor.

### **UF (VARCHAR(5))**

Sigla da Unidade Federativa onde o vendedor está localizado (ex.: SP, RJ, MG).

### **state (VARCHAR(50))**

Nome completo do estado de atuação.

### **region (VARCHAR(30))**

Região geográfica associada à UF (ex.: Sul, Sudeste, Nordeste), utilizada em análises territoriais.

### **city (VARCHAR(100))**

Cidade principal de atuação do vendedor.

### **zip_code (VARCHAR(15))**

Código postal (CEP) do endereço comercial do vendedor.

### **phone_number (VARCHAR(20))**

Telefone principal de contato.

### **CNAE (VARCHAR(15))**

Código de atividade econômica cadastrado para o vendedor.

### **wpp_opt_in (BOOLEAN)**

Indica se o vendedor consentiu receber comunicações via WhatsApp.

### **salesperson_account_id (INTEGER)**

Identificador de outro vendedor ou gestor responsável (supervisor).

### **salesperson_document (VARCHAR(20))**

CPF do vendedor responsável, caso exista uma relação hierárquica.

### **site_id (INTEGER)**

Identificador do site, canal ou ambiente de origem do cadastro.

### **client_last_updated (DATE)**

Data da última atualização cadastral do vendedor.

### **profile_picture (VARCHAR(255))**

Endereço (URL) da imagem de perfil do vendedor.

### **line (VARCHAR(50))**

Linha comercial ou categoria de produtos que o vendedor representa.

### **total_credit_limit (DECIMAL(18,2))**

Limite total de crédito disponível para operações do vendedor.

### **credit_balance (DECIMAL(18,2))**

Saldo atual de crédito disponível.

### **datekey (INTEGER)**

Chave temporal no formato AAAAMMDD, usada para relacionamento com a dimensão de calendário.

### **salesperson_code (VARCHAR(20))**

Código interno do vendedor utilizado para integrações e identificações únicas.

### **salesperson_document_code (VARCHAR(20))**

CPF vinculado ao registro interno do vendedor no sistema.

### **client_segment (VARCHAR(10))**

Código de segmentação comercial do cliente vinculado ao vendedor (ex.: M1, Q4).

### **segment_description (VARCHAR(100))**

Descrição textual da segmentação comercial.

### **division (VARCHAR(30))**

Divisão comercial à qual o vendedor pertence (ex.: AUTO, METAL, MANUTENÇÃO).

**Tabela Técnica**


| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador único do vendedor                                           | Chave Primária         |
| account_create_date          | DATE             | Data de criação da conta                                                  | —                      |
| client_id                    | INTEGER          | Código do cliente associado                                               | Chave Estrangeira      |
| client_status                | BOOLEAN          | Status ativo/inativo do cliente                                           | —                      |
| account_origin               | VARCHAR(50)      | Canal de origem do cadastro                                               | —                      |
| client_create_date           | DATE             | Data de criação do cliente vinculado                                      | —                      |
| name                         | VARCHAR(150)     | Nome completo ou razão social                                             | —                      |
| contact                      | VARCHAR(150)     | Contato principal do vendedor                                             | —                      |
| account_user                 | VARCHAR(150)     | Login ou e-mail de acesso                                                 | —                      |
| document                     | VARCHAR(20)      | CPF ou CNPJ do vendedor                                                   | —                      |
| gender                       | VARCHAR(20)      | Gênero informado                                                          | —                      |
| person_type                  | VARCHAR(10)      | Tipo de pessoa (PF/PJ)                                                    | —                      |
| age                          | INTEGER          | Idade do vendedor                                                         | —                      |
| country                      | VARCHAR(50)      | País de origem                                                            | —                      |
| UF                           | VARCHAR(5)       | Unidade Federativa                                                        | —                      |
| state                        | VARCHAR(50)      | Estado                                                                    | —                      |
| region                       | VARCHAR(30)      | Região geográfica derivada                                                | —                      |
| city                         | VARCHAR(100)     | Cidade                                                                    | —                      |
| zip_code                     | VARCHAR(15)      | Código postal (CEP)                                                       | —                      |
| phone_number                 | VARCHAR(20)      | Telefone de contato                                                       | —                      |
| CNAE                         | VARCHAR(15)      | Código de atividade econômica                                             | —                      |
| wpp_opt_in                   | BOOLEAN          | Indica aceitação de comunicação via WhatsApp                              | —                      |
| salesperson_account_id       | INTEGER          | ID do vendedor responsável                                                | Chave Estrangeira      |
| salesperson_document         | VARCHAR(20)      | CPF do vendedor responsável                                               | —                      |
| site_id                      | INTEGER          | Canal ou site de origem                                                   | —                      |
| client_last_updated          | DATE             | Data da última atualização cadastral                                      | —                      |
| profile_picture              | VARCHAR(255)     | URL da imagem de perfil                                                   | —                      |
| line                         | VARCHAR(50)      | Linha ou categoria comercial                                              | —                      |
| total_credit_limit           | DECIMAL(18,2)    | Limite máximo de crédito                                                  | —                      |
| credit_balance               | DECIMAL(18,2)    | Saldo de crédito disponível                                               | —                      |
| datekey                      | INTEGER          | Chave temporal (AAAAMMDD)                                                 | —                      |
| salesperson_code             | VARCHAR(20)      | Código interno do vendedor                                                | —                      |
| salesperson_document_code    | VARCHAR(20)      | CPF interno cadastrado                                                    | —                      |
| client_segment               | VARCHAR(10)      | Código de segmentação comercial                                           | —                      |
| segment_description          | VARCHAR(100)     | Descrição do segmento                                                     | —                      |
| division                     | VARCHAR(30)      | Divisão comercial                                                         | —                      |

---
# Tabela: fVendas

## Descrição Geral

A tabela **fVendas** é a tabela fato central do modelo analítico, responsável por consolidar todas as transações comerciais registradas no ambiente de vendas.
Cada registro representa uma linha de pedido (item vendido), incluindo informações sobre valores financeiros, descontos, tributos, quantidades e dados de relacionamento com clientes, vendedores e canais de venda.
Essa estrutura é utilizada para medir indicadores como faturamento, ticket médio, volume de pedidos, margem de lucro e desempenho por canal, região ou vendedor.

---

## Descrição das Colunas

### **amount_charged (DECIMAL(18,2))**

Valor total cobrado na venda, calculado a partir da multiplicação de preço unitário pela quantidade, somado a impostos e juros aplicáveis.

### **avg_credit_card_interest (DECIMAL(10,4))**

Média dos juros cobrados em vendas realizadas por meio de cartão de crédito, útil para análise de custo financeiro e margem líquida.

### **avg_total_tax (DECIMAL(10,4))**

Valor médio dos tributos aplicados sobre os pedidos, utilizado em estudos de carga tributária e precificação.

### **cart_order_id (INTEGER)**

Identificador do carrinho de compras vinculado ao pedido, permitindo rastrear o processo de compra digital antes da confirmação da venda.

### **client_account_id (INTEGER)**

Chave estrangeira que referencia o cliente comprador na dimensão de clientes.
Usada para análises de comportamento de compra e fidelização.

### **coupon_id (VARCHAR(50))**

Identificador do cupom de desconto aplicado ao pedido, utilizado para mensurar o impacto de campanhas promocionais e estratégias de marketing.

### **datekey (INTEGER)**

Chave temporal no formato AAAAMMDD que indica a data da transação.
Relaciona-se diretamente com a dimensão de calendário.

### **datekey_faturamento (INTEGER)**

Chave temporal representando a data de faturamento da venda, permitindo distinguir entre criação e faturamento efetivo do pedido.

### **device_id (VARCHAR(50))**

Identificador do dispositivo ou plataforma de compra (desktop, aplicativo, mobile), usado em análises de canal digital.

### **discount_value (DECIMAL(18,2))**

Valor total de descontos aplicados na transação, incluindo reduções promocionais, cupons e ajustes comerciais.

### **invoice (VARCHAR(50))**

Número da nota fiscal vinculada à venda, utilizado para rastreabilidade fiscal e contábil.

### **marketplace (VARCHAR(50))**

Canal de origem da transação (e-commerce próprio, marketplace, venda direta), útil para comparações entre canais de venda.

### **median_charged_shipping (DECIMAL(18,2))**

Valor mediano de frete cobrado ao cliente, utilizado para controle logístico e análise de custos de entrega.

### **order_status_id (INTEGER)**

Identificador numérico do status do pedido (pendente, pago, faturado, cancelado), essencial para monitoramento operacional.

### **order_subtotal (DECIMAL(18,2))**

Subtotal do pedido antes da aplicação de impostos, frete e juros.
Usado em cálculos de margem e comparativos de precificação.

### **order_total (DECIMAL(18,2))**

Valor final do pedido, incluindo impostos, frete e eventuais juros.
Representa o faturamento líquido da venda.

### **order_type_id (INTEGER)**

Código que define o tipo de pedido (venda, devolução, amostra, transferência etc.), utilizado para segmentação transacional.

### **partner_id (INTEGER)**

Identificador do parceiro comercial responsável pela venda, quando aplicável (como distribuidores ou integradores).

### **partner_order_id (VARCHAR(50))**

Identificador do pedido no sistema do parceiro, usado em integrações externas e processos de conciliação.

### **payment_method_id (INTEGER)**

Identificador do método de pagamento utilizado (boleto, cartão, PIX, transferência bancária).

### **quantity (INTEGER)**

Quantidade total de unidades vendidas no item do pedido.
Campo essencial para cálculos de ticket médio e volume total de vendas.

### **salesperson_account_id (INTEGER)**

Identificador do vendedor responsável pela venda, permitindo relacionar transações à dimensão de vendedores.

### **salesperson_document (VARCHAR(20))**

Documento (CPF ou CNPJ) do vendedor responsável, usado para validações fiscais e integrações.

### **shipping_type_id (INTEGER)**

Tipo de envio associado à entrega (Correios, transportadora, retirada em loja), usado para análises logísticas e de SLA.

### **site_id (INTEGER)**

Identificador do site ou ambiente digital onde a venda foi registrada, facilitando análises por canal de origem.

### **sku_id (INTEGER)**

Identificador único do produto (SKU) vendido, usado como chave estrangeira para a dimensão de produtos.

### **unit_price (DECIMAL(18,2))**
---

**Tabela técnina**  


| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| amount_charged               | DECIMAL(18,2)    | Valor total cobrado na venda                                              | —                      |
| avg_credit_card_interest     | DECIMAL(10,4)    | Média dos juros sobre cartão de crédito                                   | —                      |
| avg_total_tax                | DECIMAL(10,4)    | Média de impostos aplicados                                               | —                      |
| cart_order_id                | INTEGER          | Identificador do carrinho de compra                                       | —                      |
| client_account_id            | INTEGER          | Referência ao cliente comprador                                           | Chave Estrangeira      |
| coupon_id                    | VARCHAR(50)      | Código do cupom promocional                                               | —                      |
| datekey                      | INTEGER          | Chave temporal da data da transação                                       | Chave Estrangeira      |
| datekey_faturamento          | INTEGER          | Data de faturamento da venda                                              | —                      |
| device_id                    | VARCHAR(50)      | Identificador do dispositivo de compra                                    | —                      |
| discount_value               | DECIMAL(18,2)    | Valor total de descontos aplicados                                        | —                      |
| invoice                      | VARCHAR(50)      | Número da nota fiscal da venda                                            | —                      |
| marketplace                  | VARCHAR(50)      | Canal de origem da venda                                                  | —                      |
| median_charged_shipping      | DECIMAL(18,2)    | Valor mediano de frete cobrado                                            | —                      |
| order_status_id              | INTEGER          | Código do status do pedido                                                | —                      |
| order_subtotal               | DECIMAL(18,2)    | Valor dos produtos sem impostos e frete                                   | —                      |
| order_total                  | DECIMAL(18,2)    | Valor total do pedido                                                     | —                      |
| order_type_id                | INTEGER          | Tipo de pedido (venda, devolução, etc.)                                   | —                      |
| partner_id                   | INTEGER          | Identificador do parceiro comercial                                       | —                      |
| partner_order_id             | VARCHAR(50)      | Código do pedido no sistema parceiro                                      | —                      |
| payment_method_id            | INTEGER          | Método de pagamento utilizado                                             | —                      |
| quantity                     | INTEGER          | Quantidade total de itens vendidos                                        | —                      |
| salesperson_account_id       | INTEGER          | Conta do vendedor responsável                                             | Chave Estrangeira      |
| salesperson_document         | VARCHAR(20)      | CPF ou CNPJ do vendedor responsável                                       | —                      |
| shipping_type_id             | INTEGER          | Tipo de envio associado à entrega                                         | —                      |
| site_id                      | INTEGER          | Canal ou ambiente de origem                                               | —                      |
| sku_id                       | INTEGER          | Identificador do produto (SKU)                                            | Chave Estrangeira      |
| unit_price                   | DECIMAL(18,2)    | Valor unitário do item vendido                                            | —                      |

---

## 👥 Tabela: `dClientes`
---
## Descrição Geral

A tabela **dClientes** é uma dimensão que consolida as informações cadastrais, financeiras, geográficas e de relacionamento dos clientes registrados no sistema.
Cada linha representa um cliente único, com detalhes que permitem analisar perfil de compra, origem, comportamento comercial, limites de crédito e relacionamento com vendedores.
Ela serve como base para integrações com fatos de vendas, análises de retenção, segmentação de mercado, inadimplência e performance comercial por região ou segmento.

---
## Descrição das Colunas

### **account_age_days (INTEGER)**

Representa o tempo de existência da conta em dias, calculado a partir da data de criação.
É útil para análises de tempo médio de relacionamento e fidelização do cliente.

### **account_create_date (DATE)**

Data em que o cliente foi cadastrado no sistema, servindo como marco inicial do relacionamento comercial.

### **account_id (INTEGER)**

Identificador único da conta associada ao cliente.
Utilizado como chave primária na dimensão e em junções com tabelas fato.

### **account_origin (VARCHAR(50))**

Canal de origem do cadastro do cliente, como “Aplicativo”, “Plataforma Web” ou “Integração Externa”.
Permite avaliar a origem dos cadastros e a efetividade de canais de aquisição.

### **account_user (VARCHAR(150))**

Nome de usuário ou e-mail de login do cliente no sistema.
Utilizado para fins de auditoria e autenticação.

### **age (INTEGER)**

Idade do cliente, calculada a partir da data de nascimento (quando informada).
Apoia análises demográficas e segmentação por faixa etária.

### **city (VARCHAR(100))**

Cidade de residência ou sede principal do cliente, utilizada em relatórios geográficos e de cobertura de atendimento.

### **client_create_date (DATE)**

Data de criação formal do registro do cliente, útil para monitorar o crescimento da base.

### **client_id (INTEGER)**

Identificador único do cliente no sistema ERP ou plataforma de origem.
É a chave principal de integração com fatos e outras dimensões.

### **client_last_updated (DATE)**

Data da última atualização das informações cadastrais, utilizada para controle de versionamento e atualizações recentes.

### **client_status (VARCHAR(20))**

Status atual do cliente (ex.: “Ativo”, “Inativo”, “Bloqueado”), permitindo análises de base ativa e churn.

### **CNAE (VARCHAR(15))**

Código da Classificação Nacional de Atividades Econômicas.
Identifica o ramo de atuação do cliente e apoia análises por segmento de mercado.

### **contact (VARCHAR(150))**

Nome do contato principal do cliente.
Usado em comunicações diretas e gestão de relacionamento (CRM).

### **country (VARCHAR(50))**

País de origem do cliente, geralmente “Brasil”, podendo conter registros internacionais.

### **credit_balance (DECIMAL(18,2))**

Saldo atual de crédito disponível para o cliente, representando o montante ainda utilizável em compras a prazo.

### **credit_limit (DECIMAL(18,2))**

Limite total de crédito concedido ao cliente.
Comparado com o saldo para identificar exposição financeira e risco de inadimplência.

### **datekey (INTEGER)**

Chave temporal no formato AAAAMMDD.
Relaciona-se à dimensão de calendário para análises históricas e sazonais.

### **document (VARCHAR(20))**

Documento fiscal do cliente (CPF ou CNPJ), utilizado para validação, emissão de notas fiscais e controle de duplicidade.

### **gender (VARCHAR(20))**

Gênero do cliente, aplicável para pessoas físicas, utilizado em análises de perfil.

### **line (VARCHAR(50))**

Categoria comercial ou linha de produtos predominante do cliente.
Usado para segmentar a carteira por área de interesse.

### **name (VARCHAR(150))**

Nome completo ou razão social do cliente, campo principal de identificação.

### **person_type (VARCHAR(10))**

Define se o cliente é Pessoa Física (PF) ou Pessoa Jurídica (PJ).
Afeta regras tributárias e políticas de crédito.

### **phone_number (VARCHAR(20))**

Número de telefone principal para contato.
Usado em automações e cadastros de comunicação.

### **region (VARCHAR(30))**

Região geográfica derivada do estado (ex.: Sul, Sudeste, Nordeste).
Usada em relatórios e agrupamentos regionais.

### **salesperson_account_id (INTEGER)**

Identificador do vendedor responsável pelo cliente, permitindo associar contas a representantes comerciais.

### **salesperson_document (VARCHAR(20))**

Documento (CPF) do vendedor responsável, usado para validação e rastreamento.

### **segment_description (VARCHAR(100))**

Descrição textual do segmento de mercado em que o cliente atua (ex.: Autopeças, Indústria, Serviços).

### **site_id (INTEGER)**

Identificador do site, canal ou ambiente digital onde o cliente foi cadastrado.

### **state (VARCHAR(50))**

Nome completo do estado do cliente.
Permite agrupamento territorial em relatórios.

### **total_credit_limit (DECIMAL(18,2))**

Limite total de crédito disponível ao cliente.
Usado para cálculo de exposição e classificação de risco financeiro.

### **UF (VARCHAR(5))**

Sigla da Unidade Federativa correspondente ao endereço (ex.: SP, RJ, MG).

### **zip_code (VARCHAR(15))**

Código postal (CEP) do endereço principal do cliente.

---

**Tabela Técnica**  

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_age_days             | INTEGER          | Dias de existência da conta do cliente                                    | —                      |
| account_create_date          | DATE             | Data de criação da conta do cliente                                       | —                      |
| account_id                   | INTEGER          | Identificador único da conta do cliente                                   | Chave Primária         |
| account_origin               | VARCHAR(50)      | Canal de origem do cadastro                                               | —                      |
| account_user                 | VARCHAR(150)     | Usuário ou e-mail do cliente                                              | —                      |
| age                          | INTEGER          | Idade do cliente                                                          | —                      |
| city                         | VARCHAR(100)     | Cidade do cliente                                                         | —                      |
| client_create_date           | DATE             | Data de criação do cliente                                                | —                      |
| client_id                    | INTEGER          | Código identificador do cliente                                           | Chave Primária         |
| client_last_updated          | DATE             | Data da última atualização                                                | —                      |
| client_status                | VARCHAR(20)      | Status atual do cliente                                                   | —                      |
| CNAE                         | VARCHAR(15)      | Código de atividade econômica                                             | —                      |
| contact                      | VARCHAR(150)     | Nome do contato principal                                                 | —                      |
| country                      | VARCHAR(50)      | País do cliente                                                           | —                      |
| credit_balance               | DECIMAL(18,2)    | Saldo atual de crédito                                                    | —                      |
| credit_limit                 | DECIMAL(18,2)    | Limite total de crédito concedido                                         | —                      |
| datekey                      | INTEGER          | Chave temporal (AAAAMMDD)                                                 | Chave Estrangeira      |
| document                     | VARCHAR(20)      | CPF ou CNPJ do cliente                                                    | —                      |
| gender                       | VARCHAR(20)      | Gênero (quando aplicável)                                                 | —                      |
| line                         | VARCHAR(50)      | Linha comercial ou categoria                                              | —                      |
| name                         | VARCHAR(150)     | Nome completo ou razão social                                             | —                      |
| person_type                  | VARCHAR(10)      | Tipo de pessoa (PF/PJ)                                                    | —                      |
| phone_number                 | VARCHAR(20)      | Telefone principal                                                        | —                      |
| region                       | VARCHAR(30)      | Região geográfica derivada                                                | —                      |
| salesperson_account_id       | INTEGER          | Identificador do vendedor responsável                                     | Chave Estrangeira      |
| salesperson_document         | VARCHAR(20)      | Documento do vendedor responsável                                         | —                      |
| segment_description          | VARCHAR(100)     | Descrição do segmento de atuação                                          | —                      |
| site_id                      | INTEGER          | Canal ou ambiente de cadastro                                             | —                      |
| state                        | VARCHAR(50)      | Estado do cliente                                                         | —                      |
| total_credit_limit           | DECIMAL(18,2)    | Limite total de crédito do cliente                                        | —                      |
| UF                           | VARCHAR(5)       | Unidade Federativa                                                        | —                      |
| zip_code                     | VARCHAR(15)      | Código postal (CEP)                                                       | —                      |

---

# 🤝 Tabela: `dAssociados`
---

## Descrição Geral

A tabela **dAssociados** é uma dimensão que reúne informações sobre parceiros comerciais, distribuidores, transportadoras e outros tipos de entidades associadas ao negócio. Cada linha representa um parceiro único, com dados cadastrais, operacionais e logísticos que permitem identificar o tipo de relacionamento mantido, a abrangência de atuação e as condições de integração comercial.
Essa dimensão é amplamente utilizada em análises B2B, logísticas e de performance de rede, auxiliando no entendimento da infraestrutura de entrega e da cobertura nacional.
---

## Descrição das Colunas

### **city (VARCHAR(100))**

Nome da cidade onde o parceiro ou distribuidor está localizado.
Usado em relatórios regionais e análises de capilaridade logística.

### **company_name (VARCHAR(150))**

Razão social completa da empresa associada, registrada para fins legais e fiscais.

### **copartner_id (INTEGER)**

Identificador único do parceiro comercial.
É a chave primária da dimensão e serve como referência em junções com fatos de transações ou indicadores operacionais.

### **correios (BOOLEAN)**

Indica se o parceiro realiza entregas por meio dos Correios.
Campo útil para controle de canais logísticos.

### **country (VARCHAR(50))**

País de origem ou operação do parceiro comercial.

### **cupon_habilitado (BOOLEAN)**

Indica se o parceiro aceita cupons promocionais em suas operações.

### **datekey (INTEGER)**

Chave de data no formato AAAAMMDD que representa o vínculo temporal de registro ou atualização do parceiro.
Usada para relacionamentos com a dimensão de tempo.

### **document (VARCHAR(20))**

Documento fiscal do parceiro (CNPJ ou CPF).
Utilizado para controle de identidade e validações fiscais.

### **ecommerce_habilitado (BOOLEAN)**

Indica se o parceiro possui integração ativa com plataformas de e-commerce.

### **entrega_economica (BOOLEAN)**

Identifica se o parceiro oferece modalidade de frete econômico, relevante para análises de custo logístico.

### **estados_b2b (VARCHAR(255))**

Lista ou código dos estados onde o parceiro opera no modelo B2B (Business-to-Business).

### **estados_b2c (VARCHAR(255))**

Lista ou código dos estados onde o parceiro opera no modelo B2C (Business-to-Consumer).

### **frota_propria (BOOLEAN)**

Indica se o parceiro possui frota própria para entregas e transporte de produtos.

### **last_update_date (DATE)**

Data da última atualização dos dados do parceiro.
Permite controle de manutenção e sincronização cadastral.

### **loggi (BOOLEAN)**

Indica se o parceiro possui integração com o serviço Loggi, relevante para entregas rápidas.

### **loja_configurada (BOOLEAN)**

Sinaliza se o parceiro possui loja ou hub configurado dentro do sistema.

### **melhor_envio (BOOLEAN)**

Indica se o parceiro utiliza integração com o serviço de logística Melhor Envio.

### **partner (VARCHAR(150))**

Nome comercial ou identificação principal do parceiro.
Campo complementar ao *company_name* para exibição em relatórios.

### **partner_type (VARCHAR(50))**

Classificação do tipo de parceiro — como distribuidor, transportadora, fornecedor ou integrador.

### **partnership_date (DATE)**

Data de início do relacionamento comercial ou parceria.
Usada para acompanhar a evolução e o tempo de vínculo.

### **plataform_status (VARCHAR(30))**

Status da integração ou vínculo do parceiro na plataforma (ativo, inativo, pendente).

### **retirada_loja (BOOLEAN)**

Indica se o parceiro oferece a opção de retirada de pedidos em loja física.

### **state (VARCHAR(50))**

Nome completo do estado onde o parceiro está localizado.

### **street_address (VARCHAR(255))**

Endereço completo da sede ou ponto de atendimento principal do parceiro.

### **trading_name (VARCHAR(100))**

Nome fantasia utilizado comercialmente, exibido em relatórios e comunicações.

### **trading_name_cut1 (VARCHAR(50))**

Versão abreviada do nome fantasia.
Usada em relatórios compactos ou sistemas com limitação de caracteres.

### **transportadoras (VARCHAR(255))**

Lista ou código das transportadoras com as quais o parceiro opera.

### **uf (VARCHAR(5))**

Sigla da Unidade Federativa correspondente ao endereço.

### **wirecard (BOOLEAN)**

Indica se o parceiro possui integração ativa com o sistema de pagamento Wirecard.

### **zip_code (VARCHAR(15))**

Código postal (CEP) do endereço principal.

---
**Tabela Técnica**  

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| city                         | VARCHAR(100)     | Cidade principal de localização do parceiro                               | —                      |
| company_name                 | VARCHAR(150)     | Razão social completa                                                     | —                      |
| copartner_id                 | INTEGER          | Identificador único do parceiro comercial                                 | Chave Primária         |
| correios                     | BOOLEAN          | Indica uso de serviço dos Correios                                        | —                      |
| country                      | VARCHAR(50)      | País de operação                                                          | —                      |
| cupon_habilitado             | BOOLEAN          | Indica se o parceiro aceita cupons                                        | —                      |
| datekey                      | INTEGER          | Chave temporal (AAAAMMDD)                                                 | Chave Estrangeira      |
| document                     | VARCHAR(20)      | CNPJ ou CPF do parceiro                                                   | —                      |
| ecommerce_habilitado         | BOOLEAN          | Indica integração com e-commerce                                          | —                      |
| entrega_economica            | BOOLEAN          | Indica oferta de frete econômico                                          | —                      |
| estados_b2b                  | VARCHAR(255)     | Estados com operação B2B                                                  | —                      |
| estados_b2c                  | VARCHAR(255)     | Estados com operação B2C                                                  | —                      |
| frota_propria                | BOOLEAN          | Indica frota logística própria                                            | —                      |
| last_update_date             | DATE             | Data da última atualização cadastral                                      | —                      |
| loggi                        | BOOLEAN          | Integração com Loggi                                                      | —                      |
| loja_configurada             | BOOLEAN          | Loja ou hub configurado                                                   | —                      |
| melhor_envio                 | BOOLEAN          | Integração com serviço Melhor Envio                                       | —                      |
| partner                      | VARCHAR(150)     | Nome comercial do parceiro                                                | —                      |
| partner_type                 | VARCHAR(50)      | Tipo de parceiro (distribuidor, transportadora, etc.)                     | —                      |
| partnership_date             | DATE             | Data de início da parceria                                                | —                      |
| plataform_status             | VARCHAR(30)      | Status da integração ou vínculo                                           | —                      |
| retirada_loja                | BOOLEAN          | Indica se há opção de retirada em loja                                    | —                      |
| state                        | VARCHAR(50)      | Estado de localização                                                     | —                      |
| street_address               | VARCHAR(255)     | Endereço completo                                                         | —                      |
| trading_name                 | VARCHAR(100)     | Nome fantasia do parceiro                                                 | —                      |
| trading_name_cut1            | VARCHAR(50)      | Nome fantasia abreviado                                                   | —                      |
| transportadoras              | VARCHAR(255)     | Transportadoras associadas                                                | —                      |
| uf                           | VARCHAR(5)       | Unidade Federativa (sigla)                                                | —                      |
| wirecard                     | BOOLEAN          | Integração com sistema de pagamento Wirecard                              | —                      |
| zip_code                     | VARCHAR(15)      | Código postal (CEP)                                                       | —                      |

---

# 📅 Tabela: `dCalendario`

## Descrição Geral

A tabela **dCalendario** é uma dimensão temporal fundamental no modelo analítico.
Cada linha representa uma data única, contendo atributos que permitem análises em diferentes níveis de granularidade: dia, semana, mês, trimestre e ano.
Essa dimensão é utilizada em todos os relacionamentos temporais entre fatos, possibilitando comparação de períodos, análises sazonais, cálculos de indicadores acumulados e definição de períodos fiscais.

---

## Descrição das Colunas

### **Ano (INTEGER)**

Ano civil correspondente à data. Utilizado em agrupamentos e filtros de relatórios anuais.

### **AnoFiscal (INTEGER)**

Ano fiscal da organização, que pode divergir do ano civil. Facilita o controle de períodos contábeis.

### **AnoMes (VARCHAR(10))**

Combinação entre ano e mês no formato AAAAMM.
Usado para agrupamentos mensais e comparações de evolução de períodos.

### **AnoMes_Fechamento (VARCHAR(10))**

Identifica o período de fechamento fiscal ou contábil.
Usado em análises de encerramento de ciclo.

### **AnoMesDia (VARCHAR(15))**

Concatenação de ano, mês e dia (AAAAMMDD).
Representa a granularidade máxima temporal.

### **AnoSemana (INTEGER)**

Número da semana no ano civil (1 a 52).
Essencial para relatórios semanais e ciclos curtos.

### **AnoTrimestre (VARCHAR(10))**

Combinação entre o ano e o trimestre correspondente.
Facilita agrupamentos trimestrais.

### **Data (DATE)**

Campo que armazena a data completa.
É a base para todas as derivações temporais.

### **datekey (INTEGER)**

Chave de data no formato AAAAMMDD.
Utilizada como chave primária na dimensão e chave estrangeira nas tabelas fato.

### **Dia (INTEGER)**

Número do dia dentro do mês (1–31).

### **Dia_Semana (INTEGER)**

Número do dia dentro da semana (1 para domingo, 7 para sábado).

### **DiaÚtil (BOOLEAN)**

Indica se o dia é considerado útil (exclui sábados, domingos e feriados).

### **Feriado (BOOLEAN)**

Sinaliza se a data é feriado nacional.
Usado para análises de sazonalidade e impacto de calendário.

### **Futuro (BOOLEAN)**

Indica se a data pertence a um período futuro em relação à data atual.
Auxilia em filtros de previsões ou planos futuros.

### **Hoje (BOOLEAN)**

Marca a data atual (TRUE somente para o dia corrente).

### **Mês (INTEGER)**

Número do mês (1–12).

### **Mês_Atual (BOOLEAN)**

Sinaliza se a data pertence ao mês corrente.

### **Mês_Completo (VARCHAR(20))**

Nome completo do mês, por extenso (ex.: Janeiro, Fevereiro).

### **Mês_Fiscal (INTEGER)**

Número do mês no calendário fiscal, podendo diferir do mês civil.

### **Mês/Ano (VARCHAR(10))**

Combinação textual do mês e ano (ex.: Jan/2025).
Utilizada em relatórios sintéticos e gráficos temporais.

### **Mês/Ano_Fechamento (VARCHAR(10))**

Período fiscal de fechamento mensal.

### **MesNo (INTEGER)**

Índice sequencial do mês dentro do ano.

### **Nome_Dia (VARCHAR(15))**

Nome completo do dia da semana (ex.: Segunda-feira).

### **Nome_Dia_abv (VARCHAR(5))**

Abreviação do nome do dia (ex.: Seg, Ter).

### **Offset_Ano (INTEGER)**

Diferença entre o ano corrente e o ano da data.

### **Offset_Dia (INTEGER)**

Diferença em dias em relação à data atual.

### **Offset_Mês (INTEGER)**

Diferença em meses em relação ao mês atual.

### **Offset_Semana (INTEGER)**

Diferença em semanas em relação à semana atual.

### **Offset_Trimestre (INTEGER)**

Diferença em trimestres em relação ao trimestre atual.

### **Semana_Ano (INTEGER)**

Número da semana dentro do ano.

### **Semana_Atual (BOOLEAN)**

Indica se a data pertence à semana atual.

### **Semana_Completa (VARCHAR(15))**

Combinação textual “Semana/ANO”, usada em dashboards.

### **Semana_Mês (INTEGER)**

Número da semana dentro do mês.

### **Semana/Ano (VARCHAR(15))**

Combinação textual da semana e do ano (ex.: Semana 12/2025).

### **Trimestre (INTEGER)**

Número do trimestre correspondente (1–4).

### **Trimestre_Completo (VARCHAR(10))**

Nome completo do trimestre (ex.: 1º Trimestre).

### **Trimestre_Fiscal (INTEGER)**

Trimestre conforme calendário fiscal da organização.

### **Trimestre/Ano (VARCHAR(10))**

Combinação textual entre trimestre e ano (ex.: T1/2025).

**Tabela Técnica**  

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| Ano                          | INTEGER          | Ano civil correspondente à data                                           | —                      |
| AnoFiscal                    | INTEGER          | Ano fiscal da organização                                                 | —                      |
| AnoMes                       | VARCHAR(10)      | Combinação de ano e mês (AAAAMM)                                          | —                      |
| AnoMes_Fechamento            | VARCHAR(10)      | Período de fechamento fiscal                                              | —                      |
| AnoMesDia                    | VARCHAR(15)      | Ano, mês e dia concatenados                                               | —                      |
| AnoSemana                    | INTEGER          | Número da semana no ano civil                                             | —                      |
| AnoTrimestre                 | VARCHAR(10)      | Combinação de ano e trimestre                                             | —                      |
| Data                         | DATE             | Data completa                                                             | —                      |
| datekey                      | INTEGER          | Chave primária de data (AAAAMMDD)                                         | Chave Primária         |
| Dia                          | INTEGER          | Dia do mês                                                                | —                      |
| Dia_Semana                   | INTEGER          | Dia da semana (1 a 7)                                                     | —                      |
| DiaÚtil                      | BOOLEAN          | Indica se é dia útil                                                      | —                      |
| Feriado                      | BOOLEAN          | Indica feriado nacional                                                   | —                      |
| Futuro                       | BOOLEAN          | Indica data futura                                                        | —                      |
| Hoje                         | BOOLEAN          | Indica a data atual                                                       | —                      |
| Mês                          | INTEGER          | Mês do ano (1 a 12)                                                       | —                      |
| Mês_Atual                    | BOOLEAN          | Indica se pertence ao mês atual                                           | —                      |
| Mês_Completo                 | VARCHAR(20)      | Nome completo do mês                                                      | —                      |
| Mês_Fiscal                   | INTEGER          | Mês conforme calendário fiscal                                            | —                      |
| Mês/Ano                      | VARCHAR(10)      | Combinação de mês e ano                                                   | —                      |
| Mês/Ano_Fechamento           | VARCHAR(10)      | Período de fechamento mensal                                              | —                      |
| MesNo                        | INTEGER          | Índice do mês no ano                                                      | —                      |
| Nome_Dia                     | VARCHAR(15)      | Nome completo do dia da semana                                            | —                      |
| Nome_Dia_abv                 | VARCHAR(5)       | Abreviação do nome do dia                                                 | —                      |
| Offset_Ano                   | INTEGER          | Diferença em anos em relação ao atual                                     | —                      |
| Offset_Dia                   | INTEGER          | Diferença em dias em relação ao atual                                     | —                      |
| Offset_Mês                   | INTEGER          | Diferença em meses em relação ao atual                                    | —                      |
| Offset_Semana                | INTEGER          | Diferença em semanas em relação ao atual                                  | —                      |
| Offset_Trimestre             | INTEGER          | Diferença em trimestres em relação ao atual                               | —                      |
| Semana_Ano                   | INTEGER          | Semana dentro do ano                                                      | —                      |
| Semana_Atual                 | BOOLEAN          | Indica semana atual                                                       | —                      |
| Semana_Completa              | VARCHAR(15)      | Descrição completa da semana                                              | —                      |
| Semana_Mês                   | INTEGER          | Semana dentro do mês                                                      | —                      |
| Semana/Ano                   | VARCHAR(15)      | Combinação textual semana/ano                                             | —                      |
| Trimestre                    | INTEGER          | Número do trimestre (1–4)                                                 | —                      |
| Trimestre_Complete           | VARCHAR(10)      | Nome completo do trimestre                                                | —                      |
| Trimestre_Fiscal             | INTEGER          | Trimestre conforme calendário fiscal                                      | —                      |
| Trimestre/Ano                | VARCHAR(10)      | Combinação textual de trimestre e ano                                     | —                      |

---

## 🗂️ Tabela: `dCarteirizacao`

## Descrição Geral

A tabela **dCarteirizacao** registra o relacionamento direto entre clientes, vendedores e lojas dentro do ecossistema comercial.
Cada linha representa uma relação ativa entre um cliente e o vendedor responsável por atendê-lo em uma determinada loja ou unidade de negócio.

Essa dimensão é essencial para análises de carteirização comercial, permitindo identificar:

* quais clientes estão vinculados a quais vendedores,
* quais lojas ou unidades estão associadas ao atendimento,
* como se distribui a base de clientes por carteira.

Os dados dessa tabela são utilizados em cruzamentos com as dimensões **dClientes**, **dVendedores** e **dLojas**, além de se relacionar com tabelas fato, como **fVendas**, possibilitando análises de desempenho por carteira de clientes.

---

## Descrição das Colunas

### **id_account_customer (INTEGER)**

Identificador único do cliente associado à carteira.
Relaciona-se diretamente com a chave primária **account_id** da tabela **dClientes**.

### **id_account_seller (INTEGER)**

Identificador único do vendedor responsável pelo cliente.
Faz referência à chave primária **account_id** da tabela **dVendedores**.

### **id_store (INTEGER)**

Identificador da loja, unidade ou canal de venda associado à relação entre cliente e vendedor.
Usado para análises por ponto de atendimento, performance regional e cobertura comercial.


**Tabela Técnica**

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| id_account_customer          | INTEGER          | Identificador único do cliente associado à carteira                       | Chave Estrangeira      |
| id_account_seller            | INTEGER          | Identificador do vendedor responsável pelo cliente                        | Chave Estrangeira      |
| id_store                     | INTEGER          | Identificador da loja ou unidade de atendimento                           | Chave Estrangeira      |

---

## 🎫 Tabela: `dCupons`

## Descrição Geral

A tabela **dCupons** é uma dimensão responsável por armazenar informações relacionadas a cupons promocionais utilizados em campanhas de vendas, e-commerce e programas de fidelidade.
Cada registro representa um cupom único, com seus dados de identificação, período de validade, site de origem e vínculo com campanhas comerciais.
Essa tabela é essencial para análises de desempenho de campanhas promocionais, controle de validade de cupons e mensuração do impacto de descontos sobre as vendas.

---

## Descrição das Colunas

### **coupon_id (INTEGER)**

Identificador único do cupom no sistema.
Atua como chave primária da dimensão e permite o relacionamento com tabelas fato, como **fVendas**.

### **code (VARCHAR(50))**

Código alfanumérico do cupom aplicado na venda.
Utilizado pelos clientes durante o checkout e em campanhas de marketing digital.

### **campaign (VARCHAR(150))**

Nome ou descrição da campanha promocional associada ao cupom.
Permite identificar o contexto de uso e o objetivo comercial da promoção.

### **datekey_begin (INTEGER)**

Chave temporal no formato AAAAMMDD que indica a data de início da validade do cupom.
Serve para relacionar o período ativo com a dimensão **dCalendario**.

### **datekey_end (INTEGER)**

Chave temporal no formato AAAAMMDD referente à data de término da validade do cupom.
Usada para identificar o encerramento da promoção ou expiração do benefício.

### **site_id (INTEGER)**

Identificador do site, loja virtual ou canal de venda onde o cupom foi disponibilizado.
Facilita análises de desempenho de cupons por canal de origem.


**Tabela Técnica** 

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| coupon_id                    | INTEGER          | Identificador único do cupom promocional                                  | Chave Primária         |
| code                         | VARCHAR(50)      | Código do cupom aplicado em vendas                                        | —                      |
| campaign                     | VARCHAR(150)     | Nome ou descrição da campanha promocional                                 | —                      |
| datekey_begin                | INTEGER          | Data inicial da validade do cupom (AAAAMMDD)                              | —                      |
| datekey_end                  | INTEGER          | Data final da validade do cupom (AAAAMMDD)                                | —                      |
| site_id                      | INTEGER          | Identificador do site ou canal de origem                                  | —                      |

---

## 📱 Tabela: `dDispositivos`

## Descrição Geral

A tabela **dDispositivos** armazena informações sobre os dispositivos utilizados por clientes e vendedores nas interações com as plataformas digitais.
Seu principal objetivo é possibilitar análises de comportamento digital e desempenho de canais (como desktop, mobile e aplicativo), identificando o meio de acesso utilizado em vendas, cadastros ou navegação.

---

## Descrição das Colunas

### **device_id (INTEGER)**

Identificador único do dispositivo registrado.
Atua como chave primária da dimensão e é utilizado como referência em tabelas fato.

### **device (VARCHAR(50))**

Nome ou categoria do dispositivo (por exemplo, Desktop, Mobile, App, Tablet).
Permite classificar e agrupar interações por tipo de acesso.


**Tabela Técnica**

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| device_id                    | INTEGER          | Identificador único do dispositivo                                        | Chave Primária         |
| device                       | VARCHAR(50)      | Categoria ou tipo de dispositivo utilizado                                | —                      |

---

## 🎉 Tabela: `dFeriados`

## Descrição Geral

A tabela **dFeriados** é uma dimensão auxiliar que armazena informações de feriados e datas comemorativas.
Complementa a dimensão de tempo (**dCalendario**) e tem como finalidade indicar dias não úteis e períodos com impacto nas operações comerciais e logísticas.
É utilizada em análises sazonais, projeções de demanda e comparativos de desempenho entre períodos com e sem feriados.

---

## Descrição das Colunas

### **Data (DATE)**

Data completa no formato ISO (YYYY-MM-DD), representando o dia do feriado.

### **Dia_Semana (VARCHAR(15))**

Nome do dia da semana correspondente à data.
Usado para análises de distribuição e recorrência de feriados.

### **Feriado (VARCHAR(100))**

Nome ou descrição do feriado, como Natal, Carnaval ou Independência.
Inclui feriados nacionais e regionais.


**Tabela Técnica** 

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| Data                         | DATE             | Data completa do feriado                                                  | Chave Primária         |
| Dia_Semana                   | VARCHAR(15)      | Nome do dia da semana correspondente                                      | —                      |
| Feriado                      | VARCHAR(100)     | Nome ou descrição do feriado                                              | —                      |

---

## 👥 Tabela: `dGrupo_Cliente`

## Descrição Geral

A tabela **dGrupo_Cliente** centraliza informações sobre o agrupamento e a categorização dos clientes, de acordo com tipo de conta, documento fiscal e canal de origem.
Cada registro representa um cliente vinculado ao tipo de cadastro e ao site de origem.
Essa dimensão é utilizada para segmentar a base de clientes e realizar análises de comportamento, perfil e fidelização.

---

## Descrição das Colunas

### **account_id (INTEGER)**

Identificador único do cliente dentro do sistema.
Atua como chave primária e é utilizado em relacionamentos com tabelas de vendas e cadastros.

### **name (VARCHAR(150))**

Nome completo ou razão social do cliente.
Utilizado em relatórios e cadastros analíticos.

### **document (VARCHAR(20))**

Documento fiscal do cliente (CPF ou CNPJ).
Utilizado para controle de duplicidades e identificação tributária.

### **customer_type (VARCHAR(50))**

Tipo de cliente — por exemplo, Pessoa Física, Pessoa Jurídica, Revendedor ou Distribuidor.
Facilita a segmentação de análises.

### **site_id (INTEGER)**

Identificador do site ou canal de origem do cliente.
Permite análises de captação e fidelização por plataforma.


**Tabela Técnica**

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador único do cliente                                            | Chave Primária         |
| name                         | VARCHAR(150)     | Nome completo ou razão social                                             | —                      |
| document                     | VARCHAR(20)      | CPF ou CNPJ do cliente                                                    | —                      |
| customer_type                | VARCHAR(50)      | Categoria do cliente (PF, PJ, etc.)                                       | —                      |
| site_id                      | INTEGER          | Canal de origem do cadastro                                               | Chave Estrangeira      |

---

## 💳 Tabela: `dMetodo_pagamento`

## Descrição Geral

A tabela **dMetodo_pagamento** armazena os diferentes métodos de pagamento disponíveis nas transações realizadas.
Seu objetivo é possibilitar a identificação e categorização dos meios de pagamento utilizados pelos clientes, permitindo análises financeiras e operacionais relacionadas à forma de quitação dos pedidos.
Essa dimensão é fundamental para relatórios de vendas, controle de recebimentos e estudos sobre a preferência dos clientes quanto aos meios de pagamento.

---

## Descrição das Colunas

### **payment_method_id (INTEGER)**

Identificador único do método de pagamento.
Atua como chave primária da dimensão e é utilizado em junções com a tabela fato de vendas.

### **payment_method (VARCHAR(100))**

Nome ou descrição do método de pagamento, como Cartão de Crédito, Boleto Bancário, PIX ou Transferência.
Permite classificações e agrupamentos conforme a forma de pagamento utilizada.


**Tabela Técnica**

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| payment_method_id            | INTEGER          | Identificador único do método de pagamento                                | Chave Primária         |
| payment_method               | VARCHAR(100)     | Nome ou descrição do método de pagamento                                  | —                      |

---

## 🛍️ Tabela: `dOfertas`

## Descrição Geral

A tabela **dOfertas** centraliza as informações sobre os produtos ofertados no ambiente comercial, tanto em canais diretos quanto em integrações com parceiros e associados.
Cada registro representa uma oferta específica de produto, contendo dados sobre disponibilidade, preços, fornecedores e códigos de referência.
Essa dimensão é essencial para análises de catálogo, monitoramento de estoque, performance de produtos e controle de variações comerciais entre parceiros.

---

## Descrição das Colunas

### **associate_id (INTEGER)**

Identificador do associado responsável pela oferta.
Permite a vinculação com a dimensão de parceiros ou associados.

### **partner_id (INTEGER)**

Código do parceiro comercial que originou a oferta.
Utilizado para rastrear a origem de produtos e acordos comerciais.

### **company_name (VARCHAR(150))**

Nome da empresa ou parceiro associado à oferta.
Identifica o fornecedor responsável pelo produto.

### **partner_part_code (VARCHAR(50))**

Código interno do produto no sistema do parceiro comercial.
Facilita o controle de equivalência entre catálogos.

### **mfr_part_code (VARCHAR(50))**

Código do fabricante original do produto.
Utilizado em análises de procedência e integração com bases de fabricantes.

### **sku_id (INTEGER)**

Identificador único do SKU (Stock Keeping Unit) do produto.
Serve como chave primária e elo entre diferentes dimensões de produto.

### **sku_name (VARCHAR(150))**

Nome ou descrição comercial do produto.
Exibido em relatórios, dashboards e cadastros de oferta.

### **unit_price (DECIMAL(18,2))**

Preço unitário vigente da oferta.
Usado em análises de margem, precificação e competitividade.

### **quantity_available (INTEGER)**

Quantidade disponível em estoque para a oferta.
Indica a disponibilidade comercial e dá suporte a estratégias de venda.

### **by_request (BOOLEAN)**

Indica se o produto está disponível apenas sob solicitação.
Usado para identificar itens de cotação ou venda restrita.

### **datekey (INTEGER)**

Chave temporal no formato AAAAMMDD que representa a data de referência da oferta.
Utilizada para cruzamento com a dimensão **dCalendario**.

### **sku_created_date (DATE)**

Data de criação do SKU no sistema.
Útil para acompanhar a entrada de novos produtos no portfólio.

### **sku_last_updated (DATE)**

Data da última atualização de informações da oferta (preço, estoque ou disponibilidade).

**Tabela Técnica**

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| associate_id                 | INTEGER          | Identificador do associado responsável pela oferta                        | Chave Estrangeira      |
| partner_id                   | INTEGER          | Identificador do parceiro comercial                                       | Chave Estrangeira      |
| company_name                 | VARCHAR(150)     | Nome da empresa responsável pela oferta                                   | —                      |
| partner_part_code            | VARCHAR(50)      | Código do produto no sistema do parceiro                                  | —                      |
| mfr_part_code                | VARCHAR(50)      | Código original do fabricante do produto                                  | —                      |
| sku_id                       | INTEGER          | Identificador único do SKU do produto                                     | Chave Primária         |
| sku_name                     | VARCHAR(150)     | Nome ou descrição comercial do produto                                    | —                      |
| unit_price                   | DECIMAL(18,2)    | Preço unitário da oferta                                                  | —                      |
| quantity_available           | INTEGER          | Quantidade disponível em estoque                                          | —                      |
| by_request                   | BOOLEAN          | Indica se o item está disponível apenas sob solicitação                   | —                      |
| datekey                      | INTEGER          | Data de referência da oferta (AAAAMMDD)                                   | Chave Estrangeira      |
| sku_created_date             | DATE             | Data de criação do SKU                                                    | —                      |
| sku_last_updated             | DATE             | Data da última atualização do SKU                                         | —                      |

---

## 📊 Tabela: `dPeriodos`

# Tabela: dPeriodos

## Descrição Geral

A tabela **dPeriodos** armazena informações relacionadas aos períodos de análise temporal, sendo utilizada como dimensão auxiliar para segmentar dados por intervalo de tempo.
Cada registro representa um período definido (como mês, trimestre, ano fiscal ou ciclo operacional), permitindo análises comparativas e agregações temporais em relatórios e dashboards.

---

## Descrição das Colunas

### **Data (DATE)**

Data de referência do período.
Representa a data base associada a um determinado agrupamento temporal.

### **Ordem (INTEGER)**

Campo numérico que define a ordem sequencial do período.
Utilizado para ordenações lógicas em relatórios e visualizações temporais.

### **Periodo (VARCHAR(50))**

Descrição textual do período (ex.: “Janeiro/2025”, “1º Trimestre/2024”).
Facilita a identificação humana de intervalos de tempo.


**Tabela Técnica**

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| Data                         | DATE             | Data de referência do período                                             | —                      |
| Ordem                        | INTEGER          | Sequência numérica para ordenação temporal                                | —                      |
| Período                      | VARCHAR(50)      | Nome ou descrição do período de análise                                   | Chave Primária         |

---

## 📦 Tabela: `dProdutos`

# Tabela: dProdutos

## Descrição Geral

A tabela **dProdutos** é uma dimensão que concentra as informações dos produtos comercializados.
Ela é utilizada para análises de desempenho por categoria, fabricante, linha e SKU (Stock Keeping Unit).
Cada registro representa um produto único, identificado por um SKU, com hierarquias de categorização e códigos de referência.

---

## Descrição das Colunas

### **sku_id (INTEGER)**

Identificador único do produto.
Atua como chave primária da dimensão e é usado em junções com tabelas fato de vendas e ofertas.

### **sku_name (VARCHAR(150))**

Nome comercial do produto.
Utilizado em relatórios e dashboards de análise de portfólio.

### **mfr_part_code (VARCHAR(50))**

Código do fabricante original do produto.
Usado para controle de equivalência e identificação de origem.

### **manufacturer (VARCHAR(100))**

Nome do fabricante responsável pelo produto.
Facilita análises por marca ou fornecedor.

### **category_level_1 (VARCHAR(100))**

Nível principal de categorização do produto (ex.: Automotivo, Ferramentas).

### **category_level_2 (VARCHAR(100))**

Subcategoria intermediária (ex.: Elétrica, Manual).

### **category_level_3 (VARCHAR(100))**

Subnível mais específico de classificação do produto (ex.: Chave de Fenda, Multímetro).

### **nivel (VARCHAR(20))**

Define o nível hierárquico ou de classificação do produto dentro da estrutura comercial.


**Tabela Técnica**

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| sku_id                       | INTEGER          | Identificador único do produto (SKU)                                      | Chave Primária         |
| sku_name                     | VARCHAR(150)     | Nome comercial ou descritivo do produto                                   | —                      |
| mfr_part_code                | VARCHAR(50)      | Código original do fabricante                                             | —                      |
| manufacturer                 | VARCHAR(100)     | Nome do fabricante responsável                                            | —                      |
| category_level_1             | VARCHAR(100)     | Categoria principal do produto                                            | —                      |
| category_level_2             | VARCHAR(100)     | Subcategoria intermediária                                                | —                      |
| category_level_3             | VARCHAR(100)     | Subnível de categorização                                                 | —                      |
| nivel                        | VARCHAR(20)      | Nível hierárquico ou tipo de produto                                      | —                      |

---

## 📋 Tabela: `dStatus_pedido`

## Descrição Geral

A tabela **dStatus_pedido** contém os status possíveis de um pedido, desde sua criação até o faturamento, cancelamento ou conclusão.
É utilizada como dimensão de referência para análises operacionais, acompanhamento do pipeline de vendas e monitoramento da performance de atendimento.

---

## Descrição das Colunas

### **order_status_id (INTEGER)**

Identificador único do status do pedido.
Atua como chave primária e é utilizado como referência em tabelas fato de vendas.

### **order_status (VARCHAR(100))**

Nome ou descrição do status (ex.: Pendente, Faturado, Cancelado, Concluído).
Permite classificações e agrupamentos por estágio do ciclo de pedido.


**Tabela Técnica**

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| order_status_id              | INTEGER          | Identificador único do status do pedido                                   | Chave Primária         |
| order_status                 | VARCHAR(100)     | Nome ou descrição textual do status                                       | —                      |

---

## 🚚 Tabela: `dTipo_envio`

## Descrição Geral

A tabela **dTipo_envio** armazena os diferentes tipos de envio utilizados nos pedidos realizados.
Cada registro representa uma forma de entrega adotada no processo logístico, permitindo identificar como os produtos foram transportados até o cliente final.
Essa dimensão é essencial para análises de eficiência logística, custos de frete, prazos de entrega e preferências de transporte.

---

## Descrição das Colunas

### **shipping_type_id (INTEGER)**

Identificador único do tipo de envio.
Atua como chave primária da dimensão e é utilizado como referência em tabelas fato, como vendas e entregas.

### **shipping_type (VARCHAR(100))**

Nome ou descrição do tipo de envio (ex.: Correios, Transportadora, Retirada em Loja, Loggi).
Permite segmentar os pedidos por modalidade de entrega e calcular tempos médios e custos associados.


 
**Tabela Técnica**

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| shipping_type_id             | INTEGER          | Identificador único do tipo de envio                                      | Chave Primária         |
| shipping_type                | VARCHAR(100)     | Nome ou descrição da modalidade de envio                                  | —                      |

---

## 📦 Tabela: `dTipo_pedido`

## Descrição Geral

A tabela **dTipo_pedido** contém as classificações dos diferentes tipos de pedidos registrados no sistema.
Cada registro representa uma categoria de operação comercial, permitindo distinguir entre vendas normais, devoluções, amostras ou transferências internas.
Essa dimensão é utilizada para análises de volume de pedidos por tipo, controle operacional e segmentação de indicadores de faturamento e logística.

---

## Descrição das Colunas

### **order_type_id (INTEGER)**

Identificador único do tipo de pedido.
Atua como chave primária e é utilizado para relacionar os registros com tabelas fato de vendas.

### **order_type (VARCHAR(100))**

Nome ou descrição do tipo de pedido (ex.: Venda Normal, Devolução, Amostra, Transferência).
Usado para relatórios e indicadores operacionais que segmentam os pedidos por natureza.


**Tabela Técnica**  

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| order_type_id                | INTEGER          | Identificador único do tipo de pedido                                     | Chave Primária         |
| order_type                   | VARCHAR(100)     | Nome ou descrição do tipo de pedido                                       | —                      |

---

## 🔐 Tabela: `fLogins`

## Descrição Geral

A tabela **fLogins** registra todos os eventos de login realizados pelos usuários da plataforma.
Cada linha representa uma tentativa de autenticação bem-sucedida, contendo informações sobre o tipo de conta, data e origem do acesso.
Essa tabela é fundamental para análises de engajamento, frequência de uso e comportamento de acesso entre diferentes tipos de usuários (clientes, vendedores, parceiros, administradores).

---

## Descrição das Colunas

### **account_id (INTEGER)**

Identificador único da conta do usuário que realizou o login.

### **account_type (VARCHAR(50))**

Tipo de conta vinculada ao login (ex.: cliente, vendedor, parceiro).

### **account_user (VARCHAR(150))**

Nome de usuário ou e-mail utilizado para acessar o sistema.

### **datekey (INTEGER)**

Chave temporal no formato AAAAMMDD correspondente à data do login.

### **document (VARCHAR(20))**

CPF ou CNPJ vinculado à conta.

### **login_date (DATE)**

Data e hora em que o login foi realizado.

### **login_type (VARCHAR(50))**

Método de autenticação utilizado (ex.: senha, SSO, token).

### **site_id (INTEGER)**

Identificador do site ou domínio em que o login ocorreu.


**Tabela Técnica**
| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador único do usuário                                            | Chave Primária         |
| account_type                 | VARCHAR(50)      | Tipo da conta (cliente, vendedor, etc.)                                   | —                      |
| account_user                 | VARCHAR(150)     | Usuário ou e-mail de acesso                                               | —                      |
| datekey                      | INTEGER          | Chave da data no formato AAAAMMDD                                         | —                      |
| document                     | VARCHAR(20)      | CPF ou CNPJ do usuário                                                    | —                      |
| login_date                   | DATE             | Data e hora do login                                                      | —                      |
| login_type                   | VARCHAR(50)      | Tipo de autenticação utilizada                                            | —                      |
| site_id                      | INTEGER          | Identificador do site de origem                                           | —                      |

---

## 📈 Tabela: `fDatalayer_session_summary`

## Descrição Geral

A tabela **fDatalayer_session_summary** consolida os dados de sessões de visitantes e usuários autenticados.
Cada registro representa um resumo de sessão, contendo a duração total, o tipo de usuário e o status de login.
Essas informações são essenciais para medir engajamento digital, duração média de visitas e taxa de conversão por sessão.

---

## Descrição das Colunas

### **account_id (INTEGER)**

Identificador do usuário (autenticado ou visitante).

### **datekey (INTEGER)**

Chave temporal da sessão no formato AAAAMMDD.

### **session (VARCHAR(100))**

Código único que identifica a sessão.

### **session_time_in_seconds (INTEGER)**

Duração total da sessão em segundos.

### **site_id (INTEGER)**

Identificador do site onde a sessão ocorreu.

### **user_type (VARCHAR(50))**

Tipo de usuário (visitante, cliente, vendedor).

### **vendor_id (INTEGER)**

Identificador do vendedor, quando aplicável.

### **vendor_isloggedin (BOOLEAN)**

Indica se o vendedor estava autenticado durante a sessão.

### **visitor_id (INTEGER)**

Identificador do visitante anônimo.

### **visitor_isloggedin (BOOLEAN)**

Indica se o visitante realizou login durante a sessão.


**Tabela Técnica**
| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador do usuário                                                  | Chave Primária         |
| datekey                      | INTEGER          | Data da sessão (AAAAMMDD)                                                 | —                      |
| session                      | VARCHAR(100)     | Código único da sessão                                                    | —                      |
| session_time_in_seconds      | INTEGER          | Tempo total da sessão em segundos                                         | —                      |
| site_id                      | INTEGER          | Identificador do site da sessão                                           | —                      |
| user_type                    | VARCHAR(50)      | Tipo de usuário                                                           | —                      |
| vendor_id                    | INTEGER          | Identificador do vendedor associado                                       | —                      |
| vendor_isloggedin            | BOOLEAN          | Status de login do vendedor                                               | —                      |
| visitor_id                   | INTEGER          | Identificador do visitante                                                | —                      |
| visitor_isloggedin           | BOOLEAN          | Status de login do visitante                                              | —                      |

---

## 📈 Tabela: `fDatalayer_product_pageviews`

## Descrição Geral

A tabela **fDatalayer_product_pageviews** armazena as visualizações de páginas de produtos no ambiente digital.
Cada linha representa uma interação de um visitante ou usuário autenticado com a página de um produto específico.
Essa tabela possibilita análises de comportamento, interesse por produtos e eficiência de campanhas de exposição.

---

## Descrição das Colunas

### **account_id (INTEGER)**

Identificador do usuário que visualizou o produto.

### **datekey (INTEGER)**

Chave de data da visualização no formato AAAAMMDD.

### **datekey_max_datecreated / datekey_min_datecreated (INTEGER)**

Datas de início e fim da visualização, utilizadas para medir a duração da interação.

### **distinct_count_session (INTEGER)**

Quantidade de sessões distintas em que o produto foi visualizado.

### **max_datecreated_time / min_datecreated_time (TIMESTAMP)**

Horários exatos da primeira e da última visualização do produto.

### **site_id (INTEGER)**

Identificador do site no qual a visualização ocorreu.

### **sku_id (INTEGER)**

Identificador do produto visualizado.

### **vendor_id (INTEGER)**

Identificador do vendedor associado ao produto.

### **vendor_email (VARCHAR(100))**

E-mail do vendedor.

### **vendor_isloggedin (BOOLEAN)**

Indica se o vendedor estava autenticado no momento da visualização.

### **visitor_id (INTEGER)**

Identificador do visitante.

### **visitor_email (VARCHAR(100))**

E-mail do visitante, quando disponível.

### **visitor_isloggedin (BOOLEAN)**

Indica se o visitante estava autenticado no momento da visualização.

**Tabela Técnica**  

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador do usuário                                                  | Chave Primária         |
| datekey                      | INTEGER          | Data da visualização                                                      | —                      |
| datekey_max_datecreated      | INTEGER          | Data máxima de interação                                                  | —                      |
| datekey_min_datecreated      | INTEGER          | Data mínima de interação                                                  | —                      |
| distinct_count_session       | INTEGER          | Contagem de sessões únicas                                                | —                      |
| max_datecreated_time         | TIMESTAMP        | Horário da última visualização                                            | —                      |
| min_datecreated_time         | TIMESTAMP        | Horário da primeira visualização                                          | —                      |
| site_id                      | INTEGER          | Identificador do site                                                     | —                      |
| sku_id                       | INTEGER          | Código do produto visualizado                                             | Chave Estrangeira      |
| vendor_id                    | INTEGER          | Identificador do vendedor                                                 | —                      |
| vendor_email                 | VARCHAR(100)     | E-mail do vendedor                                                        | —                      |
| vendor_isloggedin            | BOOLEAN          | Status de login do vendedor                                               | —                      |
| visitor_id                   | INTEGER          | Identificador do visitante                                                | —                      |
| visitor_email                | VARCHAR(100)     | E-mail do visitante                                                       | —                      |
| visitor_isloggedin           | BOOLEAN          | Status de login do visitante                                              | —                      |

---

## 🛒 Tabela: `fCarrinhos_abandonados`

## Descrição Geral

A tabela **fCarrinhos_abandonados** registra os carrinhos de compras iniciados e não finalizados.
Cada registro representa uma instância de abandono, contendo informações sobre cliente, produto, quantidade e valor.
Ela serve como base para estratégias de remarketing, análise de conversão e estudos de comportamento de compra.

---

## Descrição das Colunas

### **cart_type (VARCHAR(50))**

Tipo de carrinho (ex.: regular, promoção, pré-venda).

### **client_account_id (INTEGER)**

Identificador da conta do cliente que iniciou o carrinho.

### **data (DATE)**

Data da criação ou do abandono do carrinho.

### **datekey (INTEGER)**

Chave temporal associada à data da criação/abandono (AAAAMMDD).

### **device_id (VARCHAR(50))**

Identificador do dispositivo utilizado.

### **mfr_part_code (VARCHAR(50))**

Código do fabricante do produto.

### **partner (VARCHAR(100))**

Nome do parceiro associado à venda ou ao produto.

### **quantity (INTEGER)**

Quantidade de produtos adicionados ao carrinho.

### **session_id (VARCHAR(100))**

Código da sessão em que o carrinho foi criado.

### **site_id (INTEGER)**

Identificador do site ou plataforma de origem.

### **sku_id (INTEGER)**

Código identificador do produto no carrinho.

### **sku_name (VARCHAR(150))**

Nome comercial do produto.

### **unit_price (DECIMAL(18,2))**

Valor unitário do produto no momento da criação do carrinho.

**Tabela Técnica**   

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| cart_type                    | VARCHAR(50)      | Tipo de carrinho                                                          | —                      |
| client_account_id            | INTEGER          | Conta do cliente associado                                                | Chave Primária         |
| data                         | DATE             | Data de criação ou abandono                                               | —                      |
| datekey                      | INTEGER          | Chave temporal (AAAAMMDD)                                                 | —                      |
| device_id                    | VARCHAR(50)      | Identificador do dispositivo                                              | —                      |
| mfr_part_code                | VARCHAR(50)      | Código do fabricante                                                      | —                      |
| partner                      | VARCHAR(100)     | Nome do parceiro comercial                                                | —                      |
| quantity                     | INTEGER          | Quantidade de produtos                                                    | —                      |
| session_id                   | VARCHAR(100)     | Identificador da sessão                                                   | —                      |
| site_id                      | INTEGER          | Identificador do site                                                     | —                      |
| sku_id                       | INTEGER          | Código do produto (SKU)                                                   | Chave Estrangeira      |
| sku_name                     | VARCHAR(150)     | Nome do produto                                                           | —                      |
| unit_price                   | DECIMAL(18,2)    | Valor unitário do item                                                    | —                      |

---

## ⏱️ Tabela: `agg_last_login`

## Descrição Geral

A tabela **agg_last_login** consolida as informações do último login realizado por cada usuário.
É uma tabela agregada utilizada para calcular métricas de recorrência, inatividade e engajamento.
Cada registro contém a data do último acesso, o status do login e a quantidade de dias desde o último login.

---

## Descrição das Colunas

### **account_id (INTEGER)**

Identificador do usuário.

### **days_since_last_login (INTEGER)**

Quantidade de dias desde o último login.

### **login_status (VARCHAR(20))**

Status atual do login (ex.: ativo, inativo).

### **site_id (INTEGER)**

Identificador do site ou domínio vinculado ao acesso.


**Tabela Técnica** 

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador do usuário                                                  | Chave Primária         |
| days_since_last_login        | INTEGER          | Dias desde o último login                                                 | —                      |
| login_status                 | VARCHAR(20)      | Status do login                                                           | —                      |
| site_id                      | INTEGER          | Identificador do site                                                     | —                      |

---

## 🛍️ Tabela: `agg_last_purchase`

## Descrição Geral

A tabela **agg_last_purchase** armazena informações sobre a última compra realizada por cada cliente.
Ela é utilizada para análises de frequência de compra, detecção de inatividade e segmentação RFM (Recência, Frequência, Valor Monetário).
Cada linha representa o último evento de compra do cliente, contendo a quantidade de dias desde a transação e o status da conta na plataforma.

---

## Descrição das Colunas

### **account_id (INTEGER)**

Identificador do cliente.

### **days_since_last_purchase (INTEGER)**

Número de dias desde a última compra realizada.

### **plataform_status (VARCHAR(50))**

Status da conta na plataforma (ex.: ativo, inativo).

### **site_id (INTEGER)**

Identificador do site onde a compra foi realizada.


**Tabela Técnica**   

| Nome da Coluna               | Tipo de Dado     | Descrição                                                                 | Chave / Relacionamento |
|------------------------------|------------------|---------------------------------------------------------------------------|------------------------|
| account_id                   | INTEGER          | Identificador do cliente                                                  | Chave Primária         |
| days_since_last_purchase     | INTEGER          | Dias desde a última compra                                                | —                      |
| plataform_status             | VARCHAR(50)      | Status da plataforma do cliente                                           | —                      |
| site_id                      | INTEGER          | Identificador do site de origem                                           | —                      |

---


