# Definição das Histórias de Usuário (US)

## 1. História do Usuárioo

### **US 1 – Precificação**

**Descrição:**  
Como um usuário **(Proprietário ou Inquilino)**, eu quero **obter uma estimativa do valor de aluguel** de um imóvel específico (com base em suas características), para saber se o preço de anúncio é justo.  

**Critérios de Aceitação (CA):**  
- O sistema retorna a estimativa em R$ em menos de 10 segundos.  
- O sistema indica a margem de erro.  

---

### **US 2 – Previsão de Preços**

**Descrição:**  
Como um **usuário focado no futuro**, eu quero **visualizar a tendência de preço de aluguel** para o bairro nos próximos 6 meses, para **auxiliar minha decisão de investimento ou momento de alugar/vender**.  

**Critérios de Aceitação (CA):**  
- O sistema apresenta a previsão em um gráfico ou valor percentual para o horizonte de 6 meses.  

---

### **US 3 – Custo x Benefício**

**Descrição:**  
Como um **usuário que busca por uma boa oferta**, eu quero **que o sistema classifique o preço** de um imóvel anunciado (Ex: "Excelente Negócio" ou "Alto Custo"), para priorizar minha busca.  

**Critérios de Aceitação (CA):**  
- A classificação (Bom/Ruim Negócio) é exibida automaticamente após a precificação.  

---

## 2. Priorização MoSCoW


| Categoria MoSCoW | Descrição | Histórias de Usuário (US) | Funcionalidades |
| :--- | :--- | :--- | :--- |
| **M - Must Have** (Deve ter) | **Essencial** para o produto funcionar e entregar o valor principal ao usuário. Sem isso, o produto não tem utilidade. | **US 1 (Preço Justo):** Obter uma estimativa de aluguel. | **Precificação (Regressão)** |
| **S - Should Have** (Deveria ter) | **Muito importante** para o sucesso, agregando valor significativo. Será priorizado no MVP após o "Must Have". | **US 3 (Custo-Benefício):** Classificar o imóvel como boa/má oferta. | **Classificação/Métrica Automática** |
| **C - Could Have** (Poderia ter) | **Desejável**, mas opcional. Será incluído se houver tempo e recursos disponíveis no ciclo do MVP, mas sem comprometer o *Must* ou *Should*. | **US 4 (Feedback):** Coletar feedback do usuário sobre a estimativa. | **Coleta de Feedback (MLOps)** |
| **W - Won't Have** (Não terá) | Funcionalidades que **não farão parte do escopo do MVP** e estão planejadas para o **Incremento 1** ou fases futuras. | **US 2 (Previsão de Tendência):** Visualizar a tendência de preço. | **Previsão de Preços (Séries Temporais)** |

---

## 3. Definição do Produto Mínimo Viável (MVP)

O escopo do MVP será focado nas categorias **Must Have** e **Should Have**, garantindo a entrega do valor central com as funcionalidades de menor risco técnico e maior solidez nos dados.

**Definição do MVP:**

> O **Produto Mínimo Viável (MVP)** será um **Sistema Web** capaz de receber as características de um imóvel e retornar uma **Precificação (Preço Justo)**, acompanhada de uma **Classificação de Custo-Benefício** (indicador de boa oferta) baseada em regras estatísticas.

**Planejamento das Entregas:**

| Entrega | Foco Principal | Histórias de Usuário | Justificativa |
| :--- | :--- | :--- | :--- |
| **MVP** | **Core Value e Risco Mínimo** | US 1 (Preço Justo) e US 3 (Custo-Benefício) | Valida o modelo de **Regressão** e entrega a principal proposta de valor (preço justo). A métrica de Custo-Benefício é de fácil implementação (regras). |
| **Incremento 1** | **Evolução e Complexidade (Série Temporal)** | US 2 (Previsão de Tendência) e US 4 (Feedback) | Foca na **Previsão de Preços** (Séries Temporais), que exige tratamento de dados histórico e na criação do pipeline de **MLOps** (Coleta de Feedback). |

### Planejamento Mínimo (Cronograma Sugerido)

Este cronograma sugere a alocação de esforço focado na entrega do MVP e no planejamento do Incremento 1, priorizando a estabilidade e a qualidade do modelo central de Regressão.

| Fase | Foco Principal | US Envolvidas | % do Esforço Total (Sugerido) |
| :--- | :--- | :--- | :--- |
| **Fase 1: Preparação do MVP (Dados)** | Coleta, Unificação e Pré-processamento dos Dados (Limpeza, *Outliers*, *Missing Values*). | US 1, US 3 | 40% |
| **Fase 2: Desenvolvimento do MVP (Regressão)** | Engenharia de *Features*, Treinamento, Otimização e Implementação da API de **Precificação**. Criação da **Métrica de Custo-Benefício**. | US 1, US 3 | 30% |
| **Fase 3: Incremento 1 (Séries Temporais)** | Estruturação da Série Temporal, Treinamento do Modelo de **Previsão** e desenvolvimento da **US 2**. Criação da interface de **Feedback (US 4)**. | US 2, US 4 | 30% |

