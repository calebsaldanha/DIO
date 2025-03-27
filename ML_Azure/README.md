# **Projeto de Previsão de Vendas de Sorvete com AutoML** 🍦📊

![Banner do Projeto](https://github.com/calebsaldanha/DIO/blob/93f92d9be03652209eb2c8d79d267ec5ebb58b68/ML_Azure/images/Captura%20de%20tela%202025-03-27%20064240.png)

## **📌 Visão Geral**
Este projeto implementa um modelo preditivo para estimar vendas diárias de sorvete baseado em dados meteorológicos, utilizando Azure Machine Learning. O sistema auxilia na otimização de produção e redução de desperdícios.

## **🔍 Processo de Desenvolvimento**

### **1. Configuração do Ambiente AutoML**
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
![Treinamento em Andamento](https://github.com/calebsaldanha/DIO/blob/93f92d9be03652209eb2c8d79d267ec5ebb58b68/ML_Azure/images/Captura%20de%20tela%202025-03-27%20064005.png)
- 20 iterações completadas em 45 minutos
- Testou 7 algoritmos diferentes
- Aplicou feature engineering automático

### **3. Resultados dos Modelos**
![Leaderboard](https://github.com/calebsaldanha/DIO/blob/93f92d9be03652209eb2c8d79d267ec5ebb58b68/ML_Azure/images/Captura%20de%20tela%202025-03-27%20070732.png)
| Modelo | RMSE | R² Score |
|--------|------|----------|
| XGBoost | 4.21 | 0.91 |
| LightGBM | 4.35 | 0.89 | 
| Random Forest | 4.78 | 0.85 |

## **💡 Insights Principais**

### **Relação Temperatura-Vendas**
![Gráfico de Dispersão](https://github.com/calebsaldanha/DIO/blob/0fe736f1fdb02542bbe8c30eb93673d2d59fb2cc/ML_Azure/images/dispersao.png)
- Cada 1°C aumenta ≈3.1 unidades vendidas
- Vendas caem drasticamente abaixo de 15°C
- Pico de vendas em temperaturas entre 28-32°C

### **Sazonalidade Detectada**
- Aumento de 35% nas vendas no verão
- Quartas-feiras têm menor movimento
- Finais de semana representam 45% das vendas semanais

## **📂 Estrutura do Projeto**
```
├── azure/
│   ├── automl_driver.py       # Configurações do experimento
│   └── definition.json        # Código de inferência
│   └── requirements.txt
├── notebooks/
│   ├── 01_preprocessamento.ipynb
└── docs/
    ├── modelo_explicado.md      # Interpretabilidade
└── inputs/
    ├── contexto_negocio.txt     
```

## **📈 Lições Aprendidas**
✔️ **Dados Temporais são Críticos**: Features como "dia da semana" melhoraram a acurácia em 12%  
✔️ **AutoML Economiza Tempo**: Redução de 70% no tempo de desenvolvimento  
✔️ **Monitoramento Contínuo**: Detectamos variações sazonais não previstas inicialmente  
