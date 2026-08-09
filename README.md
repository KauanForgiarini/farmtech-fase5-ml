# FarmTech Solutions — Fase 5: Machine Learning na Cabeça
**Cap 1 — FarmTech na Era da Cloud Computing**
Curso de Inteligência Artificial — FIAP | Grupo 7

**Integrante:** 
Kauan Maciel Forgiarini — RM: `RM574005` 
Wagner Adriano de Souza Silva Junior - RM: 'RM569431'

---

## 📋 Sobre o projeto

Este repositório contém a solução do Grupo 7 para o desafio da FarmTech Solutions: prever o rendimento de safra de uma fazenda de médio porte a partir de variáveis agroclimáticas, e avaliar a hospedagem dessa solução em nuvem (AWS).

O trabalho está dividido em duas entregas obrigatórias:

- **Entrega 1 — Machine Learning:** análise exploratória, clusterização e cinco modelos preditivos de regressão para estimar o rendimento de safra (`Yield`) a partir de dados de precipitação, umidade e temperatura.
- **Entrega 2 — Computação em Nuvem:** estimativa e comparação de custos AWS entre as regiões São Paulo (BR) e Virgínia do Norte (EUA) para hospedar a API que consumirá o modelo.

---

## 🧠 Entrega 1 — Machine Learning

Todo o desenvolvimento, análise e discussão dos resultados está no notebook Jupyter:

📓 **[`KauanMacielForgiarini_rmXXXXXX_pbl_fase5.ipynb`](./KauanMacielForgiarini_rm574005_pbl_fase5.ipynb)**

O notebook contém, em ordem:
1. Análise exploratória de dados (EDA) — distribuições, correlações e detecção de outliers.
2. Clusterização não supervisionada (K-Means + PCA) para identificação de tendências de produtividade e cenários discrepantes.
3. Cinco modelos preditivos de regressão (Regressão Linear, Ridge, Random Forest, Gradient Boosting e SVR), comparados por RMSE, MAE e R², com validação cruzada.
4. Discussão dos achados, pontos fortes e limitações do trabalho.

🎥 **Vídeo demonstrativo (até 5 min, não listado):** `[INSERIR LINK DO YOUTUBE AQUI]`

---

## ☁️ Entrega 2 — Estimativa de Custos AWS

**Cenário:** hospedagem de uma API que recebe dados de sensores da fazenda e executa o modelo de Machine Learning, em uma instância Linux simples com 2 vCPUs, 1 GiB de RAM, até 5 Gbps de rede e 50 GB de armazenamento — configuração compatível com a instância **t3.micro** + volume **EBS gp3**.

### Comparação de custos (On-Demand, 100%)

| Componente | 🇺🇸 N. Virginia (us-east-1) | 🇧🇷 São Paulo (sa-east-1) |
|---|---|---|
| EC2 t3.micro | US$ 0,0104/h ≈ **US$ 7,59/mês** | US$ 0,0168/h ≈ **US$ 12,26/mês** |
| EBS gp3 — 50 GB | US$ 0,08/GB-mês ≈ **US$ 4,00/mês** | US$ 0,152/GB-mês ≈ **US$ 7,60/mês** |
| **Total mensal** | **≈ US$ 11,59** | **≈ US$ 19,86** |

> São Paulo é aproximadamente **71% mais cara** que N. Virgínia para essa configuração — reflexo do custo de infraestrutura, energia e menor economia de escala da região sul-americana frente aos hubs americanos.

### Justificativa técnica da escolha

Apesar do custo mais elevado, **recomenda-se a região São Paulo (sa-east-1)** para este caso de uso, por dois motivos principais:

1. **Latência:** os sensores estão fisicamente instalados na fazenda no Brasil. A latência de rede até `sa-east-1` é significativamente menor do que até `us-east-1`, o que é crítico para ingestão de dados quase em tempo real e resposta da API de inferência.
2. **Conformidade legal (LGPD):** a Lei Geral de Proteção de Dados (Lei nº 13.709/2018, arts. 33–34) impõe requisitos adicionais para transferência internacional de dados. Manter o processamento em território nacional simplifica a conformidade, especialmente se os dados dos sensores puderem ser associados à geolocalização da propriedade rural.

O acréscimo de custo (~US$ 8,27/mês na configuração mínima) é considerado marginal frente aos ganhos de performance e à redução de risco regulatório.

🎥 **Vídeo demonstrativo da comparação na calculadora AWS (até 5 min, não listado):** `[INSERIR LINK DO YOUTUBE AQUI]`

---

## 🛠️ Como executar o notebook localmente

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook KauanMacielForgiarini_rmXXXXXX_pbl_fase5.ipynb
```

---

## 👤 Autor

**Kauan Maciel Forgiarini**
Curso de Inteligência Artificial — FIAP
[GitHub: KauanForgiarini](https://github.com/KauanForgiarini)
