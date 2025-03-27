# **Projeto de Previsão de Vendas de Sorvete com AutoML** 🍦📊

![Banner do Projeto](https://via.placeholder.com/800x300?text=Previsão+de+Vendas+com+Azure+AutoML)

## **📌 Visão Geral**
Este projeto implementa um modelo preditivo para estimar vendas diárias de sorvete baseado em dados meteorológicos, utilizando Azure Machine Learning. O sistema auxilia na otimização de produção e redução de desperdícios.

## **🔍 Processo de Desenvolvimento**

### **1. Configuração do Ambiente AutoML**
![Configuração AutoML](https://via.placeholder.com/400x250?text=Configuração+AutoML+no+Azure+Studio)
```python
automl_config = AutoMLConfig(
    task='regression',
    primary_metric='normalized_root_mean_squared_error',
    training_data=train_data,
    iterations=50,
    n_cross_validations=5
)
```

### **2. Treinamento Automatizado**
![Treinamento em Andamento](https://via.placeholder.com/400x250?text=Execução+do+AutoML+no+Azure)
- 20 iterações completadas em 45 minutos
- Testou 7 algoritmos diferentes
- Aplicou feature engineering automático

### **3. Resultados dos Modelos**
![Leaderboard](https://via.placeholder.com/500x300?text=Comparação+de+Modelos)
| Modelo | RMSE | R² Score |
|--------|------|----------|
| XGBoost | 4.21 | 0.91 |
| LightGBM | 4.35 | 0.89 | 
| Random Forest | 4.78 | 0.85 |

## **💡 Insights Principais**

### **Relação Temperatura-Vendas**
![Gráfico de Dispersão](https://via.placeholder.com/400x250?text=Relação+Temperatura×Vendas)
- Cada 1°C aumenta ≈3.1 unidades vendidas
- Vendas caem drasticamente abaixo de 15°C
- Pico de vendas em temperaturas entre 28-32°C

### **Sazonalidade Detectada**
![Sazonalidade](https://via.placeholder.com/400x250?text=Padrão+Sazonal+Anual)
- Aumento de 35% nas vendas no verão
- Quartas-feiras têm menor movimento
- Finais de semana representam 45% das vendas semanais

## **⚙️ Implementação**

## **📂 Estrutura do Projeto**
```
├── azure/
│   ├── automl_config.json       # Configurações do experimento
│   └── scoring_script.py        # Código de inferência
├── notebooks/
│   ├── 01_preprocessamento.ipynb
└── docs/
    ├── modelo_explicado.md      # Interpretabilidade
```

## **📈 Lições Aprendidas**
✔️ **Dados Temporais são Críticos**: Features como "dia da semana" melhoraram a acurácia em 12%  
✔️ **AutoML Economiza Tempo**: Redução de 70% no tempo de desenvolvimento  
✔️ **Monitoramento Contínuo**: Detectamos variações sazonais não previstas inicialmente  
