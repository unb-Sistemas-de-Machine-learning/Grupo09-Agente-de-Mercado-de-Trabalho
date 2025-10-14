## 1. Mapeamento de Dados do PrediAluguel

Para o projeto **PrediAluguel**, a qualidade e o mapeamento dos dados são cruciais para o desenvolvimento do nosso Modelo de Precificação. Nosso foco é estimar o valor justo de aluguel para imóveis no **Distrito Federal (Brasília)**, utilizando uma base que combina dados públicos do **Kaggle** (Datasets Zap Imóveis/DF) com *scrapping* complementar.

O objetivo deste mapeamento é definir claramente quais variáveis serão utilizadas como entrada (*Features*) para o modelo de Regressão e qual é o nosso Alvo (*Target*).

A tabela a seguir detalha as colunas essenciais, suas fontes e o propósito no contexto do Machine Learning. É importante notar que o sucesso do PrediAluguel depende da correta transformação destas *Features* (como a localização categórica) em um formato numérico que o modelo possa interpretar.

### Tabela de Mapeamento de Dados (Modelo de Regressão e Custo-Benefício)

| Variável | Rótulo (Propósito) | Tipo de Dado | Fonte Principal | Notas e Requisito de ML |
| :--- | :--- | :--- | :--- | :--- |
| `rent_amount` (ou `price`) | **Alvo (Target / Y)** | Numérico Contínuo | Zap Imóveis Dataset (Kaggle/Scrapping) | Variável que o modelo DEVE predizer. |
| `area` | Feature (X) | Numérico Contínuo | Zap Imóveis Dataset (Kaggle/Scrapping) | Tamanho do imóvel em m². |
| `rooms` / `bedrooms` | Feature (X) | Numérico Discreto | Zap Imóveis Dataset (Kaggle/Scrapping) | Número de quartos. |
| `bathroom` | Feature (X) | Numérico Discreto | Zap Imóveis Dataset (Kaggle/Scrapping) | Número de banheiros. |
| `parking spaces` | Feature (X) | Numérico Discreto | Zap Imóveis Dataset (Kaggle/Scrapping) | Número de vagas de garagem. |
| `city` / `neighborhood` | Feature (X) | Categórico | Zap Imóveis Dataset (Kaggle/Scrapping) | A localização será transformada via **One-Hot Encoding**. |
| `furniture` | Feature (X) | Categórico (Binário) | Zap Imóveis Dataset (Kaggle/Scrapping) | Mobiliado (Sim/Não). Será usado **One-Hot Encoding**. |
| `hoa` (Condomínio) | Feature (X) | Numérico Contínuo | Zap Imóveis Dataset (Kaggle/Scrapping) | O valor da taxa de condomínio é um forte preditor de luxo/infraestrutura. |
| **`price_per_sqm`** | Feature Criada (X) | Numérico Contínuo | *Feature Engineering* | Criada para capturar a densidade de preço e padronizar o valor. |
| **`deviation_pct`** | Métrica de Saída | Numérico Contínuo | *Feature Engineering* (Regra) | Métrica usada para a funcionalidade **Custo-Benefício** (Regras: Desvio em relação à predição). |