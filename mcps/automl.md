---
title: AutoML MCP сервер
description: Интеллектуальная платформа автоматизированного машинного обучения, которая предоставляет комплексные возможности анализа данных, предобработки, выбора моделей и настройки гиперпараметров через инструменты Model Context Protocol (MCP).
tags:
- AI
- Analytics
- Code
- Integration
author: emircansoftware
featured: false
---

Интеллектуальная платформа автоматизированного машинного обучения, которая предоставляет комплексные возможности анализа данных, предобработки, выбора моделей и настройки гиперпараметров через инструменты Model Context Protocol (MCP).

## Установка

### Из исходного кода

```bash
git clone https://github.com/emircansoftware/AutoML.git
cd AutoML
pip install -r requirements.txt
pip install uv
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "AutoML": {
      "command": "uv",
      "args": [
        "--directory",
        "C:\\YOUR\\PROJECT\\PATH\\AutoML",
        "run",
        "main.py"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `information_about_data` | Предоставляет подробную информацию о данных |
| `reading_csv` | Читает CSV файл |
| `visualize_correlation_num` | Визуализирует корреляционную матрицу для числовых столбцов |
| `visualize_correlation_cat` | Визуализирует корреляционную матрицу для категориальных столбцов |
| `visualize_correlation_final` | Визуализирует корреляционную матрицу после предобработки |
| `visualize_outliers` | Визуализирует выбросы в данных |
| `visualize_outliers_final` | Визуализирует выбросы после предобработки |
| `preprocessing_data` | Предобрабатывает данные (удаление выбросов, заполнение пропусков и т.д.) |
| `prepare_data` | Подготавливает данные для моделей (кодирование, масштабирование и т.д.) |
| `models` | Выбирает и оценивает модели на основе типа задачи |
| `visualize_accuracy_matrix` | Визуализирует матрицу ошибок для предсказаний |
| `best_model_hyperparameter` | Настраивает гиперпараметры лучшей модели |
| `test_external_data` | Тестирует внешние данные с лучшей моделью и возвращает предсказания |
| `predict_value` | Предсказывает значение целевого столбца для новых входных данных |
| `feature_importance_analysis` | Анализирует важность признаков в данных с использованием XGBoost |

## Возможности

- Комплексная статистика датасета, включая размер, использование памяти, типы данных и пропущенные значения
- Эффективное чтение CSV файлов с поддержкой pandas и pyarrow
- Анализ и визуализация корреляций для числовых и категориальных переменных
- Обнаружение и визуализация выбросов
- Автоматизированная предобработка с обработкой пропущенных значений, кодированием категориальных признаков и масштабированием
- Поддержка множества алгоритмов машинного обучения, включая Linear Regression, Ridge, Lasso, ElasticNet, Random Forest, XGBoost, SVR, KNN, CatBoost
- Алгоритмы классификации, включая Logistic Regression, Ridge Classifier, Random Forest, XGBoost, SVM, KNN, Decision Tree, Naive Bayes, CatBoost
- Метрики производительности для регрессии (R², MAE, MSE) и классификации (Accuracy, F1-Score)
- Визуализация матрицы ошибок для задач классификации
- Возможности сравнения моделей

## Примеры использования

```
Analyze dataset statistics and missing values for heart.csv
```

```
Preprocess data by handling missing values and outliers for target column
```

```
Train and compare multiple classification models on heart disease dataset
```

```
Visualize correlation matrix for numerical features in the dataset
```

```
Optimize hyperparameters for RandomForestClassifier with 100 trials
```

## Ресурсы

- [GitHub Repository](https://github.com/emircansoftware/MCP_Server_DataScience)

## Примечания

Требует Python 3.8+. Необходимо обновить путь к данным в utils/read_csv_file.py в соответствии с вашей директорией проекта. Включает 16 примеров датасетов с Kaggle для тестирования. Сервер должен быть настроен с правильными локальными путями в конфигурации Claude Desktop.