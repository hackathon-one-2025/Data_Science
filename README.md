# 📊 ChurnInsight — Plataforma de Predição de Churn

**Status:** ✅ Concluído | MVP Integrado  
**Domínio:** Serviços de Assinatura (Telecom, Fintech, Streaming)

---

## 📌 Visão Geral

Este projeto foi desenvolvido no contexto de um hackathon, com o objetivo de construir um **modelo de Machine Learning para predição de churn (evasão de clientes)** em uma operadora de telecomunicações. 
A solução visa apoiar decisões de negócio, permitindo identificar clientes com alto risco de cancelamento e possibilitando ações preventivas.

O problema foi tratado como uma **classificação binária**, onde: - 0 → Cliente não evadiu - 1 → Cliente evadiu

O projeto foi desenvolvido de forma colaborativa entre os times de **Data Science** e **Back-end**, demonstrando como um modelo preditivo pode ser transformado em um **produto de negócio escalável**.


---

## 🎯 Problema de Negócio

Empresas de receita recorrente sofrem perdas significativas com churn. Estudos de mercado mostram que **reter um cliente é muito mais barato do que adquirir um novo**.

O ChurnInsight funciona como uma “bola de cristal baseada em dados”, analisando comportamento de uso, histórico financeiro e indicadores de qualidade para prever:

- Se um cliente está propenso a cancelar  
- Qual a probabilidade desse cancelamento ocorrer  

Essas informações permitem ações proativas por times de:
- Marketing  
- Customer Success  
- Retenção  
- CRM  

---

## 🧠 Arquitetura da Solução

A solução foi construída seguindo o conceito de **microsserviços**, garantindo desacoplamento, escalabilidade e resiliência.

### 1️⃣ AI Service — *O Cérebro*
- **Tecnologia:** Python + Flask  
- **Responsabilidade:**
  - Carregar o modelo de Machine Learning  
  - Processar features  
  - Retornar previsão e probabilidade de churn  

### 2️⃣ Back-end API — *O Gerente*
- **Tecnologia:** Java + Spring Boot  
- **Responsabilidade:**
  - Receber requisições externas  
  - Validar regras de negócio  
  - Orquestrar chamadas para o serviço de IA  

### 3️⃣ Dashboard — *A Vitrine*
- **Tecnologia:** Streamlit  
- **Responsabilidade:**
  - Interface visual para usuários de negócio  
  - Exibir alertas de risco de churn de forma intuitiva  

---

### 🧪Modelo de Machine Learning

- **Objetivo:** Predizer churn e gerar saídas utilizáveis em produção

- **Tecnologias:**

* Python
* Pandas / NumPy
* Scikit-learn
* XGBoost
* Joblib

### 📈Output do Modelo

O modelo gera automaticamente o arquivo:

```
churn_predictions_production.csv
```

Arquivo padronizado para produção, contendo:

* Identificador do cliente
* Classe prevista (Churn / Não Churn)
* Probabilidade de cancelamento

---

### 🔎Features Utilizadas (13 Variáveis)

As variáveis estão organizadas em **3 pilares de decisão:**

**1️⃣ Perfil e Contrato**

```months``` — Tempo de contrato

```rev_Mean``` — Fatura média

```avgrev``` — Receita histórica

```eqpdays``` — Idade do equipamento

```eqp_age_index``` — Índice de depreciação

**2️⃣ Comportamento de Uso**

```mou_Mean``` — Minutos de uso

```totcalls``` — Total de chamadas

```avgmou``` — Média histórica de uso

```rev_per_minute``` — Custo por minuto

```calls_per_month``` — Frequência mensal

**3️⃣ Satisfação e Qualidade**

```custcare_Mean``` — Chamadas ao suporte

```drop_vce_Mean``` — Chamadas caídas

```blck_vce_Mean``` — Chamadas bloqueadas

---

### 🔄Evolução do Back-end
**Fase 1 — MVP**

* API com apenas **5 variáveis**
* Problema de feature mismatch com o modelo final

**Fase 2 — Versão Final**

* Expansão para **13 features**
* DTOs refatorados com Lombok
* Pipeline de dados mais robusto

**🛡️Resiliência**

* Implementação de fallback automático
* aso o modelo principal falhe, um modelo de backup é carregado
* Garante SLA e disponibilidade da API

---

### 🧪Testes Automatizados

O projeto possui **testes de integração reais**, garantindo a confiabilidade entre os serviços.

Fluxo do teste:

1. Sobe o contexto Spring Boot
2. Injeta o serviço de churn
3. Cria um cliente fictício com 13 variáveis
4. Realiza chamada real à IA
5. Valida resposta e probabilidade

### ▶️ Como Executar o Projeto

**Pré-requisitos**
* Java 17+
* Python 3.10+ e bibliotecas (```flask```, ```pandas```, ```scikit-learn```, ```joblib```, ```streamlit```)

**Passo 1 — Iniciar o Serviço de IA**

```
cd churn-ia
python app.py
```

**Passo 2 — Iniciar a API Java**

* Execute a classe ```ChurninsightApplication``` na sua IDE

**Passo 3 — Abrir o Dashboard**

```
cd churn-ia
streamlit run dashboard.py
```

### 🤝 Colaboração

Este projeto demonstra a integração real entre Ciência de Dados e Engenharia de Software, mostrando como modelos matemáticos podem se tornar produtos utilizáveis, confiáveis e escaláveis.
