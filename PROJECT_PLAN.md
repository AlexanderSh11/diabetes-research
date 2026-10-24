# Diabetes Readmission Prediction. План курсовой работы

Бинарная классификация: предсказать, будет ли пациент с диабетом повторно госпитализирован в течение 30 дней после выписки.

Датасет: Diabetes 130-US hospitals for years 1999–2008 (Kaggle: [`brandao/diabetes`](https://www.kaggle.com/datasets/brandao/diabetes)).

Датасет содержит:
- 101766 строк, 50 признаков
- реальные клинические данные из 130 больниц США
- реальные пропуски
- дисбаланс классов по целевой переменной

---

## Этап 1. Подготовка данных

### 1.1. Загрузка данных

- файл `data/raw/diabetic_data.csv`
- целевая переменная: `readmitted` (`"<30"` соответствует 1, `">30"` и `"NO"` соответствует 0)

Файл: `notebooks/data_loading_and_initial_eda.ipynb`

### 1.2. Первичный EDA

- распределение целевой переменной (дисбаланс)
- типы признаков: числовые, категориальные, порядковые
- кардинальность категориальных
- визуализация пропусков

Файл: `notebooks/data_loading_and_initial_eda.ipynb`

### 1.3. Обработка пропущенных значений

- удаление признаков с большим количество пропусков
- замена пропущенных категорий
- файл `data/processed/diabetic_data_processed.csv`

Файл: `notebooks/data_loading_and_initial_eda.ipynb`

### 1.4. Кодирование категориальных признаков

- кодирование бинарных, порядковых и номинальных категориальных признаков
- файл `data/processed/diabetic_data_encoded.csv`

Файл: `notebooks/feature_encoding.ipynb`

### 1.5. Разделение данных для избежания утечки данных

Файл: `notebooks/split_outliers_scaling.ipynb`

### 1.6. Анализ выбросов

Файл: `notebooks/split_outliers_scaling.ipynb`

### 1.7. Feature engineering

Файл: `notebooks/split_outliers_scaling.ipynb`

### 1.8. Масштабирование признаков

Использование RobustScaler

Файл: `notebooks/split_outliers_scaling.ipynb`

### 1.9. Матрица корреляций и анализ мультиколлинеарности

Файл: `notebooks/split_outliers_scaling.ipynb`

### 1.10. Дисбаланс классов

Выбраны стратегии против дисбаланса классов: параметры у моделей и подбор порога классификации

Файл: `notebooks/split_outliers_scaling.ipynb`

### 1.11. Подготовка данных для обучения и сохранение в pickle

Файл: `notebooks/split_outliers_scaling.ipynb`

---

## Этап 2. Анализ важности признаков

Important features из Random Forest

Файл: `notebooks/feature_importance.ipynb`

---

## Этап 3. Обучение и оценка моделей

### 3.1. Модель 1 (линейная)

- Logistic Regression с L1/L2-регуляризацией
- подбор гиперпараметров через Optuna или RandomizedSearchCV

### 3.2. Модель 2 (нелинейная)

- LightGBM, CatBoost или XGBoost
- подбор гиперпараметров

### 3.3. Метрики

- ROC-AUC
- F1-score, Precision, Recall
- Accuracy

### 3.3. Подбор порога

### 3.4. Сравнение моделей

- таблица метрик на test set
- матрицы ошибок для моделей
- обоснование
- сравнение скорости, интерпретируемости, использования памяти

---

## Этап 4. Выводы

### 4.1. Итоговое сравнение

- какая модель лучше и почему
- где именно ошибаются модели

### 4.2. Ограничения

### 4.3. Возможные улучшения
