# Practice_Human-Activity-Recognition_Classifier
Разработка моделей классификации типа физической активности на основе данных с носимых приборов

# 📊 Учебная практика

## Разработка моделей классификации типа физической активности на основе данных с носимых приборов

### 👥 Исполнители

- **Студент 1 (Data & Signal Math):** [Арутюнова Яна] — предобработка данных, извлечение признаков (временная и частотная область)
- **Студент 2 (Classical ML Math):** [Вебер Михаил] — логистическая регрессия, математическое обоснование
- **Студент 3 (Deep Learning Math):** [Ханбиков Самат] — нейросетевая модель MLP, обратное распространение ошибки

### 📅 Срок выполнения

Июнь 2026 (6 недель, защита на 7-й неделе)

### 🎯 Цель проекта

Разработка и сравнительный анализ моделей машинного обучения для задачи классификации физической активности человека на основе данных с акселерометра носимых устройств:

#### Датасет: WISDM (Wireless Sensor Data Mining) v1.0

- **Источник:** Fordham University / UCI Repository
- **Задача:** Многоклассовая классификация (6 классов активности)
- **Размер:** ~1 MB, 36 пользователей
- **Частота дискретизации:** 20 Hz
- **Признаки:** Акселерометр (3 оси: X, Y, Z)
- **Классы активности:**
  - Walking (ходьба)
  - Jogging (бег трусцой)
  - Upstairs (подъем по лестнице)
  - Downstairs (спуск по лестнице)
  - Sitting (сидение)
  - Standing (стояние)

В рамках учебной практики выполняется:

- **Предобработка данных:** сегментация временных рядов, фильтрация шумов
- **Извлечение признаков:**
  - Временная область: среднее, дисперсия, энергия сигнала, max, min
  - Частотная область: ДПФ, доминирующая частота, спектральная энергия
- **Разработка моделей:**
  - Базовая модель: Логистическая регрессия (One-vs-Rest)
  - Нейросетевая модель: MLP (2 скрытых слоя)
- **Оптимизация:** подбор гиперпараметров (GridSearch, RandomSearch)
- **Сравнительный анализ:** метрики качества, время инференса

## 📁 Предварительная Структура проекта

```
Practice_Human-Activity-Recognition_Classifier/
│
├── data/ # Данные (не загружаются в Git) ← СОЗДАЙТЕ ПАПКУ
│ ├── raw/ # Исходные данные WISDM ← СОЗДАЙТЕ ПАПКУ
│ ├── processed/ # Обработанные данные ← СОЗДАЙТЕ ПАПКУ
│ │ ├── segmented_data.pkl
│ │ └── features_matrix.csv
│ └── README.md # Описание датасета
│
├── notebooks/ ← СОЗДАЙТЕ ПАПКУ
│ ├── 01_EDA_and_Preprocessing.ipynb # Разведочный анализ, сегментация
│ ├── 02_Feature_Extraction_Time.ipynb # Признаки временной области
│ ├── 03_Feature_Extraction_Freq.ipynb # ДПФ, частотные признаки
│ ├── 04_Logistic_Regression.ipynb # LR модель, One-vs-Rest
│ ├── 05_MLP_Model.ipynb # Нейросетевая модель
│ ├── 06_Hyperparameter_Tuning.ipynb # Оптимизация гиперпараметров
│ ├── 07_Comparison_Analysis.ipynb # Сравнительный анализ
│ └── utils.py # Вспомогательные функции
│
├── models/ # Сохраненные модели ← СОЗДАЙТЕ ПАПКУ
│ ├── lr_model.pkl
│ ├── mlp_model.pkl
│ └── scaler.pkl
│
├── reports/ ← СОЗДАЙТЕ ПАПКУ
│ ├── figures/ # Графики и визуализации
│ │ ├── time_series_samples.png
│ │ ├── frequency_spectrum.png
│ │ ├── confusion_matrix_lr.png
│ │ ├── confusion_matrix_mlp.png
│ │ └── comparison_metrics.png
│ ├── final_report.pdf # Итоговый отчет
│ └── presentation.pptx # Презентация для защиты
│
├── requirements.txt # Зависимости
├── README.md # Описание проекта
└── .gitignore # Что игнорировать в Git
```

## 📥 Установка

### 1. Клонирование репозитория
```bash
git clone https://github.com/elena-kornaeva/Practice_Human-Activity-Recognition_Classifier.git
cd Practice_Human-Activity-Recognition_Classifier
```
или через GitHubDesktop (рекомендуется): File -> Clone Repository

### 2. Установка зависимостей

```bash
pip install -r requirements.txt
```

или используя Anaconda Prompt (не обычный Command Prompt!):
```bash
conda install -r requirements.txt
```

## Загрузка данных
Скачайте датасеты с Kaggle и поместите их в предварительно созданную папку data/raw/:

https://www.kaggle.com/datasets/wangboluo/mcm2024/data

## Последовательность работы:
* 01_EDA_and_Preprocessing.ipynb — Загрузка данных, визуализация, сегментация на окна
* 02_Feature_Extraction_Time.ipynb — Извлечение признаков временной области
* 03_Feature_Extraction_Freq.ipynb — ДПФ, частотные признаки, анализ спектров
* 04_Logistic_Regression.ipynb — Обучение LR, One-vs-Rest, анализ весов
* 05_MLP_Model.ipynb — Построение нейросети, прямой и обратный проход
* 06_Hyperparameter_Tuning.ipynb — Оптимизация гиперпараметров, матрицы ошибок
* 07_Comparison_Analysis.ipynb — Сравнение моделей, время инференса, выводы

## 🔬 Методы и алгоритмы
Основные алгоритмы:
* Сегментация: Sliding Window (окно 2-3 секунды, overlap 50%).
* Временные признаки, например:
 - Mean (среднее значение)
 - Variance (дисперсия)
 - Energy (энергия сигнала: sum of squares)
 - Max/Min (экстремумы)
 - Zero Crossing Rate (пересечение нуля)
* Частотные признаки (ДПФ):
 - Discrete Fourier Transform (numpy.fft.rfft)
 - Dominant Frequency (доминирующая частота)
 - Nyquist Frequency (частота Найквиста: 10 Hz для 20 Hz дискретизации)
* Модели:
 - Logistic Regression: One-vs-Rest стратегия, L2 регуляризация
 - MLP (Multi-Layer Perceptron): 2 скрытых слоя, ReLU активация, Softmax выход
  - Optimizers: Adam, SGD

  ## Метрики качества:
Для многоклассовой классификации:
* Accuracy (доля верных ответов)
* Precision, Recall, F1-Score (macro и micro averaging)
* Confusion Matrix (матрица ошибок)
* Inference Time (время предсказания одного окна)

 ## Дополнительные техники:
* StandardScaler: масштабирование признаков
* One-Hot Encoding: кодирование целевой переменной
* Cross-Validation: StratifiedKFold (k=5)
* Hyperparameter Tuning: GridSearchCV, RandomizedSearchCV
* Feature Importance: анализ весов логистической регрессии

## 📈 Ожидаемые результаты
по метрикам:
* Accuracy> 0.85, 
* F1-Score(macro) > 0.80
* Время инференса: < 1 мс на одно окно