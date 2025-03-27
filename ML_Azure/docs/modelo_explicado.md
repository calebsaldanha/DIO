Documentação do Modelo Preditivo - Previsão de Vendas de Sorvete
📌 Identificação do Modelo
Propriedade	Valor
Status	Concluído ✅
Nome do Modelo	coral_apricot_hltwnwr2vx_20
Tipo	Regressão (XGBoost)
Versão	1.0.0
Ciclo de Treinamento

Duração Total: 4min 43.38s

Ambiente: AzureML-ai-ml-automl:19

Experiment: exp-automl

Script: automl_driver.py

📊 Métricas de Desempenho
python
Copy
{
    "R² Score": 0.67216,
    "MAE": 7.6469,
    "MAPE": 10.973%,
    "MedAE": 6.4380,
    "Normalized MAE": 0.10475
}
Interpretação das Métricas
Variância Explicada (0.67): O modelo explica 67% da variabilidade nos dados de vendas

Erro Absoluto Médio (7.65 unidades): Erro médio nas previsões

MAPE (10.97%): Erro percentual aceitável para decisões de produção

🔍 Explicabilidade do Modelo
SHAP Summary Plot

Fatores Mais Influentes:

Temperatura (°C): 58% de impacto

Cada 1°C aumenta ≈2.8 vendas

Dia da Semana: 22%

Sábados: +18% vs média

Mês: 12%

Janeiro: +35% vs média anual

📥 Entradas do Modelo
json
Copy
{
    "training_data": {
        "source": "azureml:sorvetes:1",
        "features": [
            "Temperatura (°C)",
            "Dia da Semana", 
            "Mês",
            "Feriado"
        ]
    }
}
📤 Saídas do Modelo
json
Copy
{
    "output_model": {
        "name": "azureml_coral_apricot_hltwnwr2vx_20",
        "type": "MLFlow Model",
        "artifacts": [
            "model.pkl",
            "conda_env.yml",
            "explanation.json"
        ]
    }
}
