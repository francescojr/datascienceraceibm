[README (2).md](https://github.com/user-attachments/files/22651463/README.2.md)
# 🚀 SpaceX Falcon 9 First Stage Landing Prediction

## 📋 Sobre o Projeto

Este projeto implementa um pipeline de Machine Learning para prever se o primeiro estágio do foguete Falcon 9 da SpaceX irá pousar com sucesso. Esta informação é crucial para estimar o custo de lançamento, já que a SpaceX anuncia lançamentos por $62 milhões (comparado a mais de $165 milhões de outras empresas), sendo a economia possível devido à reutilização do primeiro estágio.

## 🎯 Objetivos

- Realizar Análise Exploratória de Dados
- Criar coluna de classificação (Class)
- Padronizar os dados
- Dividir em dados de treino e teste
- Encontrar os melhores hiperparâmetros para:
  - Logistic Regression
  - Support Vector Machine (SVM)
  - Decision Tree
  - K-Nearest Neighbors (KNN)
- Determinar qual método performa melhor

## 📊 Dataset

- **Total de registros:** 90 lançamentos
- **Features:** 83 colunas após one-hot encoding
- **Divisão:** 80% treino (72 amostras) / 20% teste (18 amostras)
- **Variável target:** Class (0 = falha no pouso, 1 = pouso bem-sucedido)

### Principais Features

- FlightNumber
- PayloadMass
- Orbit (LEO, GTO, ISS, etc.)
- LaunchSite (CCAFS, VAFB, KSC)
- GridFins, Reused, Legs
- Block, ReusedCount
- Serial do Booster
- Coordenadas geográficas

## 🔧 Tecnologias Utilizadas

```python
- Python 3.8
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn (preprocessing, GridSearchCV, train_test_split)
```

## 🧪 Metodologia

### 1. Pré-processamento
- Standardização dos dados usando `StandardScaler`
- Divisão treino/teste: 80/20 com `random_state=2`

### 2. Otimização de Hiperparâmetros
Utilização de `GridSearchCV` com **10-fold cross-validation** para todos os modelos.

## 📈 Resultados

### 🏆 Desempenho dos Modelos

| Modelo | Accuracy (Teste) | Best Parameters |
|--------|------------------|-----------------|
| **Logistic Regression** | **83.33%** | C: 0.01, penalty: 'l2', solver: 'lbfgs' |
| **Support Vector Machine** | **83.33%** | C: 1.0, gamma: 0.0316, kernel: 'sigmoid' |
| **K-Nearest Neighbors** | **83.33%** | n_neighbors: 10, algorithm: 'auto', p: 1 |
| Decision Tree | 72.22% | criterion: 'entropy', max_depth: 16, min_samples_leaf: 2 |

### 📊 Melhores Resultados por Modelo

#### Logistic Regression
```
Tuned hyperparameters (best parameters): {'C': 0.01, 'penalty': 'l2', 'solver': 'lbfgs'}
Accuracy: 0.8333333333333334
Validation Score: 0.8464285714285713
```

#### Support Vector Machine (SVM)
```
Tuned hyperparameters (best parameters): {'C': 1.0, 'gamma': 0.03162277660168379, 'kernel': 'sigmoid'}
Accuracy: 0.8333333333333334
```

#### K-Nearest Neighbors (KNN)
```
Tuned hyperparameters (best parameters): {'algorithm': 'auto', 'n_neighbors': 10, 'p': 1}
Accuracy: 0.8333333333333334
```

#### Decision Tree
```
Tuned hyperparameters (best parameters): {'criterion': 'entropy', 'max_depth': 16, 'max_features': 'sqrt', 'min_samples_leaf': 2, 'min_samples_split': 5, 'splitter': 'random'}
Accuracy: 0.7222222222222222
```

## 🎯 Conclusões

1. **Três modelos empatados:** Logistic Regression, SVM e KNN alcançaram a mesma acurácia de **83.33%** no conjunto de teste.

2. **Decision Tree teve menor desempenho:** Com apenas 72.22% de acurácia, indicando possível overfitting ou complexidade inadequada para o dataset.

3. **Modelos mais simples performaram melhor:** A Regressão Logística com regularização L2 baixa (C=0.01) foi suficiente para atingir o melhor resultado.

4. **Dataset pequeno:** Com apenas 18 amostras de teste, a margem de erro é alta. Mais dados seriam necessários para validação robusta.

## 💡 Recomendações

- Para produção, considerar **ensemble** dos três melhores modelos
- Coletar mais dados de lançamentos para melhorar a generalização
- Implementar validação cruzada estratificada para datasets pequenos
- Explorar feature engineering adicional (interações entre variáveis)

## 📝 Estrutura do Código

```
├── Data Loading & Exploration
├── Feature Engineering (One-Hot Encoding)
├── Data Preprocessing (Standardization)
├── Train-Test Split
├── Model Training & Hyperparameter Tuning
│   ├── Logistic Regression
│   ├── Support Vector Machine
│   ├── Decision Tree
│   └── K-Nearest Neighbors
├── Model Evaluation
└── Results Comparison
```

## 👤 Autor

**jrFrancesco**

## 📄 Licença

Este projeto faz parte do curso IBM Data Science da Skills Network.

---

**⏱️ Tempo estimado:** 60 minutos  
**🎓 Nível:** Intermediário  
**📚 Curso:** IBM Data Science Professional Certificate
