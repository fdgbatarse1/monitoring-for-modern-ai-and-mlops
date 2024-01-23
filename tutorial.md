![Основы ML мониторинга для Data Science](docs/images/monitoring-banner-1.png)

# Тьюториал: Основы ML мониторинга для Data Science

## 👀 Overview

🎓 **Что это такое?** Представляем вашему вниманию тьюториал "Основы ML мониторинга для Data Science". Это ваш путеводитель в мире мониторинга ML моделей и данных. Мы не просто покажем вам, как это делается, но и расскажем о популярных инструментах в этой области, таких как Evidently, Great Expectations и Grafana.

👩🏻‍💻 **Для кого этот тьюториал?** Если вы Data Scientist или начинающий ML инженер, этот курс идеально подойдет для вас. Мы начнем с основ и постепенно перейдем к более продвинутым темам.

**🎯 Что вас ждет в этом тьюториале?**

- Знакомство с задачами и инструментами ML мониторинга.
- Настройка мониторинга моделей и данных с помощью Evidently.
- Изучение мониторинга данных с Great Expectations.

🔍 **Как это устроено?** Вам не придется долго искать нужную информацию. Тьюториал содержит исчерпывающие примеры кода и пошаговые инструкции в формате Markdown.

⏱️ **Сколько времени потребуется?** Вам понадобится всего 40 минут, чтобы погрузиться в мир ML мониторинга и выйти оттуда уже готовым к применению новых знаний.


## 📖 Содержание
- [Тьюториал: Основы ML мониторинга для Data Science](#тьюториал-основы-ml-мониторинга-для-data-science)
  - [👀 Overview](#overview)
  - [📖 Содержание](#-содержание)
  - [👩‍💻 1 - Установка](#1-установка)
  - [🛠️ 2 - Задачи и инструменты ML мониторинга для Data Science](#️-2-задачи-и-инструменты-ml-мониторинга-для-data-science)
    - [Задачи мониторинга в ML](#задачи-мониторинга-в-ml)
    - [Инструменты для ML мониторинга](#инструменты-для-ml-мониторинга)
  - [🏎️ 3 - Evidently для метрик качества моделей и данных](#️-3-evidently-для-метрик-качества-моделей-и-данных)
    - [Шаг 1 - Импорт Evidently](#шаг-1-импорт-evidently)
    - [Шаг 2 - Подготовка данных](#шаг-2-подготовка-данных)
    - [Шаг 3 - Построение Data Drift отчетов](#шаг-3-построение-data-drift-отчетов)
    - [Шаг 4 - Кастомизация и сохранение отчетов](#шаг-4-кастомизация-и-сохранение-отчетов)
  - [🤝 4 - Мониторинг моделей и данных с Evidently и MLflow](#-4-мониторинг-моделей-и-данных-с-evidently-и-mlflow)
    - [Шаг 1 - Загрузка данных](#шаг-1-загрузка-данных)
    - [Шаг 2 - Определение структуры данных](#шаг-2-определение-структуры-данных)
    - [Шаг 3 - Обучение модели](#шаг-3-обучение-модели)
    - [Шаг 4 - Подготовка  *reference* датасета](#шаг-4-подготовка-reference-датасета)
    - [Шаг 5 - Подготовка  *current* датасета](#шаг-5-подготовка-current-датасета)
    - [Шаг 6 - Построение отчета о качестве модели](#шаг-6-построение-отчета-о-качестве-модели)
    - [Шаг 7 - Извлеките метрики качестве модели и отчета Evidently](#шаг-7-извлеките-метрики-качестве-модели-и-отчета-evidently)
    - [Шаг 8 - Логирование и визуализация отчета о модели в MLflow](#шаг-8-логирование-и-визуализация-отчета-о-модели-в-mlflow)
  - [🎱 5 - Мониторинг данных с Great Expectations (GX)](#-5-мониторинг-данных-с-great-expectations-gx)
    - [Шаг 1 - Загрузите данные](#шаг-1-загрузите-данные)
    - [Шаг 2 - Создайте Data Context](#шаг-2-создайте-data-context)
    - [Шаг 3 - Подключите данные и создайте Validator](#шаг-3-подключите-данные-и-создайте-validator)
    - [Шаг 4 - Создание ожиданий (Expectations)](#шаг-4-создание-ожиданий-expectations)
    - [Шаг 5 - Сохраните набор ожиданий (Expectation Suite)](#шаг-5-сохраните-набор-ожиданий-expectation-suite)
    - [Шаг 6 - Валидация новых данных с Great Expectations](#шаг-6-валидация-новых-данных-с-great-expectations)
  - [📊 6 - Мониторинг данных с Grafana и PostgreSQL](#-6-мониторинг-данных-с-grafana-и-postgresql)
    - [Шаг 1 - Запуск Grafana и PostgreSQL](#шаг-1-запуск-grafana-и-postgresql)
    - [Шаг 2 - Расчет метрик мониторинга](#шаг-2-расчет-метрик-мониторинга)
    - [Шаг 3 - Подготовка базы данных для мониторинга](#шаг-3-подготовка-базы-данных-для-мониторинга)
    - [Шаг 4 - Мониторинг качества модели](#шаг-4-мониторинг-качества-модели)
    - [Шаг 5 - Настройка дашборда](#шаг-5-настройка-дашборда)
    - [Шаг 6 - Кастомизация дашборда для вашего проекта](#шаг-6-кастомизация-дашборда-для-вашего-проекта)
  - [🔗 Дополнительные ресурсы](#-дополнительные-ресурсы)

## 👩‍💻 1 - Установка

Этот раздел руководства поможет вам настроить среду для работы с тьюториалом по ML мониторингу.

**1. Сделайте форк / клонируйте этот репозиторий**

Клонируйте репозиторий с примером кода. Этот репозиторий предоставляет необходимые файлы и скрипты для тьюториала.

```bash
git clone https://gitlab.com/risomaschool/tutorials-raif/monitoring-1-get-started.git
cd monitoring-1-get-started
```

**2. Создайте виртуальное окружение** 

Для этого примера требуется Python версии 3.9 или выше. Создайте и активируйте виртуальное окружение:

```bash
python3 -m venv .venv
echo "export PYTHONPATH=$PWD" >> .venv/bin/activate
source .venv/bin/activate
pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
```

**3. Загрузите данные** 

Вам потребуется два датасета. 

1. Загрузите [набор данных по аренде велосипедов](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset) в директорию `data/`.

```bash
python src/load_data.py
```

2. Загрузите [набор данных по поездкам на такси в Нью-Йорке в январе 2019 года](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page) в директорию `data/`.

```bash
wget https://d37ci6vzurychx.cloudfront.net/trip-data/yellow_tripdata_2019-01.parquet -O data/yellow_tripdata_2019-01.parquet
```

**4. Запустите MLflow UI**

To start the MLflow UI, run:

```bash
mlflow ui
```

And then navigate to [http://localhost:5000](http://localhost:5000) in your browser

**5. Запустите Docker сервисы**

```bash
docker compose up
```

будут запущены сервисы:
- *monitoring-db*: база данных (PostgreSQL) мониторинга - для сбора метрик модели
- *grafana*: сервис (инструмент) для визуализации метрик

Откройте в браузере [Grafana UI](http://localhost:3000).

**6. Запустите Jupyter Lab или Jupyter Notebook**

```bash
jupyter lab
```

## 🛠️ 2 - Задачи и инструменты ML мониторинга для Data Science

### Задачи мониторинга в ML

Что вы имеете в виду, когда говорите "мониторинг в машинном обучении"? Точность модели? Качество данных? Или доля клиентов, которые которые выбирают рекомендованный товар/услугу? Скорее всего - комбинацию нескольких метрик!

Давайте попробуем структурировать компоненты мониторинга системы ML:

1. **Состояние (здоровье) системы:** На базовом уровне находится мониторинг бэкенда ПО, который включает в себя проверку успешности выполнения задач прогнозирования и производительности сервиса.
2. **Данные:** Следующий уровень фокусируется на качестве и целостности данных. Важно отслеживать, подходят ли данные для создания прогнозов и обучения модели.
3. **ML Модель:**  На этом уровне происходит мониторинг самой модели ML. Оценивается точность прогнозов, соответствие модели задачам и ее "честность".
4. **Бизнес или продуктовые KPI:** На вершине пирамиды находятся ключевые показатели эффективности, связанные с бизнес-целями и влиянием модели на продукт.

![Задачи мониторинга в ML](docs/images/Untitled%201.png){width=800}
*Источник: [https://www.evidentlyai.com/blog/ml-monitoring-metrics](https://www.evidentlyai.com/blog/ml-monitoring-metrics)*

Все компоненты мониторинга взаимосвязаны. Например, если вы обнаружите, что точность модели ухудшается, вы можете проверить, не изменились ли данные, или не изменилась ли бизнес-логика.

С другой стороны, можно говорить о мониторинге, в контексте ML пайплайна, например, для задач батч-скоринга (batch scoring). Этот процесс включает в себя несколько ключевых этапов:

- **T - 1 (Тренировка)**: На этом этапе модель обучается на исторических данных (History / Reference Data). Это может быть ежедневный процесс, который обновляет модель каждый день, или более редкий процесс, который обновляет модель раз в неделю или месяц.
- **T = 0 (Прогнозирование)**: На этом этапе модель используется для прогнозирования на текущих данных (Current Data).
- **T + 1 (Мониторинг)**: После прогнозирования следует этап мониторинга. Здесь данные о реальных результатах (Ground Truth Data) сравниваются с прогнозами модели для оценки качества и точности модели.

![Untitled](docs/images/Untitled.png){width=800}

В контексте мониторинга ML пайплайнов ключевые задачи включают в себя:

1. **Мониторинг модели (Monitor Model)**: Оценка производительности модели на новых данных, анализ ее стабильности и точности со временем.
2. **Мониторинг данных (Monitor Data)**: Отслеживание изменений в характеристиках входных данных (таких как распределение или возникновение новых паттернов), которые могут повлиять на работу модели.
3. **Мониторинг смещения прогнозов (Monitor Prediction Drift)**: Анализ изменений в прогнозированиях модели со временем, выявление смещения и ухудшения качества прогнозов.

### Инструменты для ML мониторинга

![Untitled](docs/images/Untitled%202.png){width=800}

В данном тьюториале рассмотрим два популярных инструмента для мониторинг моделей и данных:

- **Evidently**: Позволяет анализировать качество модели и данных, обнаруживать смещения в прогнозах и многое другое.
- **Great Expectations**: Помогает валидировать качество данных, обеспечивая их соответствие определенным критериям.


## 🏎️ 3 - Evidently для метрик качества моделей и данных 

> 💡 Откройте пример в  `notebooks/1-getting-started-tutorial.ipynb`

Идея Evidently очень проста: представить API для расчета рассчитывает множество метрик для данных и моделей, и организовать их в удобные отчеты. Отчеты являются наиболее эффективным способом визуального анализа и отладки ваших моделей и данных. Вы можете сохранять отчеты в форматах HTML или JSON (snapshots).
Это позволяет использовать Evidently для множества сценариев валидации и мониторинга в приложениях машинного обучения [для online инференса](https://evidentlyai.com/blog/fastapi-tutorial) и [batch скоринга](https://www.evidentlyai.com/blog/batch-ml-monitoring-architecture):

- анализ и отладка ML моделей и данных,
- генерация динамических отчетов мониторинга через [Панель мониторинга Evidently](https://docs.evidentlyai.com/user-guide/monitoring/monitoring_overview).
- интеграция результатов мониторинга с другими системами для хранения (например, в PostgreSQL) и или визуализации (например, в Grafana).

![Untitled](docs/images/Untitled%203.png){width=800}

### Шаг 1 - Импорт Evidently

Для начала, импортируйте Evidently, а также pandas, numpy и пример датасета `california_housing`. 

```python
import pandas as pd
import numpy as np

from sklearn.datasets import fetch_california_housing

from evidently import ColumnMapping

from evidently.report import Report
from evidently.metrics.base_metric import generate_column_metrics
from evidently.metric_preset import DataDriftPreset, TargetDriftPreset
from evidently.metrics import *

from evidently.test_suite import TestSuite
from evidently.tests.base_test import generate_column_tests
from evidently.test_preset import DataStabilityTestPreset, NoTargetPerformanceTestPreset
from evidently.tests import *

```

### Шаг 2 - Подготовка данных

В примерах тьюториала вы работаете с готовым набором данных. На практике вы должны использовать логи прогнозов модели. Они могут включать входные данные, прогнозирования модели и истинные метки или фактические данные, если они доступны.

Для подготовки данных к анализу создайте pandas.DataFrame:

```python
data = fetch_california_housing(as_frame=True)
housing_data = data.frame
```

Переименуйте одну из колонок в "target" и создайте колонку "prediction". Таким образом, набор данных будет похож на логи применения модели с известными метками.

```python
housing_data.rename(columns={'MedHouseVal': 'target'}, inplace=True)
housing_data['prediction'] = housing_data['target'].values + np.random.normal(0, 5, housing_data.shape[0])

```
![Untitled](docs/images/Untitled%204.png){width=800}

В большинстве случает Evidently использует два датасета ( `reference` и `current` ) для расчета метрик и генерации отчетов.
- Первый **reference** датасет - это эталонный набор данных. В качестве `reference`   обычно используют данные для обучения модели или выборку из истории *production* данных. 

- Второй **current** набор данных - это текущие *production* данные, которые вы хотите  сравнить с эталоном.

![Original image: [https://docs.evidentlyai.com/user-guide/input-data/data-requirements](https://docs.evidentlyai.com/user-guide/input-data/data-requirements) ](docs/images/Untitled%205.png)

> ℹ️ Источник: [https://docs.evidentlyai.com/user-guide/input-data/data-requirements](https://docs.evidentlyai.com/user-guide/input-data/data-requirements) 

Разделите набор данных, взяв 5000 объектов для эталонных и текущих наборов данных.

```python
reference = housing_data.sample(n=5000, replace=False)
current = housing_data.sample(n=5000, replace=False)
```

> **🔌 Практические рекомендации:**
>
> 1. Для своего проекта вы можете подготовить два набора данных с одинаковой схемой. 
> 2. Вы также можете взять один набор данных и явно указать строки для эталонных и текущих данных.
> 3. Вы можете иметь несколько `reference` датасетов

### Шаг 3 - Построение Data Drift отчетов

Отчеты **Evidently** помогают исследовать и устранять проблемы качества данных и моделей. Они рассчитывают различные метрики и генерируют панель управления с богатыми визуализациями. Для начала вы можете использовать **Metric Presets** - шаблонные наборы метрик и отчеты для определенных задач. 

Давайте начнем с **Data Drift.** Этот пресет сравнивает распределения признаков модели и показывает, какие из них изменились. 

Чтобы получить отчет, создайте соответствующий объект `Report`, перечислите включаемый пресет и укажите на созданные ранее эталонные и текущие наборы данных:

```python
# Создадим отчет с нужным набором метрик или пресетом
report = Report(metrics=[
    DataDriftPreset(),
])

# Запустим генерацию отчета
report.run(reference_data=reference, current_data=current)

# Для визуализации отчета в Jupyter Notebook
report.show(mode='inline')
```

![Untitled](docs/images/Untitled%206.png){width=800}

Если вы кликнете на отдельные признаки в отчете, вы увидите дополнительные графики для анализа. Например, распределение таргет переменной.

![Untitled](docs/images/Untitled%207.png){width=800}

### Шаг 4 - Кастомизация и сохранение отчетов

Вы можете кастомизировать отчеты Evidently и явно указать, какие метрики включить и как их рассчитывать.

Например, вот так можно перечислить несколько метрик, рассчитывающих статистики для определенного столбца:

```python
report = Report(metrics=[
    ColumnSummaryMetric(column_name='AveRooms'),
    ColumnQuantileMetric(column_name='AveRooms', quantile=0.25),
    ColumnDriftMetric(column_name='AveRooms')
])

report.run(reference_data=reference, current_data=current)
```

Вы получите примерно такой отчет:

![Untitled](docs/images/Untitled%208.png){width=800}

> 💡 Больше примеров метрик и отчетов можно найти в официальной документации: [Quickstart for Reports and Tests](https://docs.evidentlyai.com/get-started/tutorial#4.-get-the-data-drift-report)

Вы можете конвертировать сгенерированные отчеты в словарь Python или JSON или сохранить как HTML файл.

```python
report.as_dict()              # Удобно для парcинга отчета и получения отдельных метрик
report.save_html("file.html") # Удобно открыть и посмотреть в браузере 
```

Вы также можете сохранить вывод в виде Snapshot JSON. Это позволит вам визуализировать качество модели или данных в динамике с помощью [ML Evidently Dashboards](https://docs.evidentlyai.com/get-started/tutorial-monitoring)

```python
report.save("snapshot.json")
```

## 🤝 4 - Мониторинг моделей и данных с Evidently и MLflow

> 💡 Пример в Jupyter Notebook `notebooks/2-monitor-model.ipynb`

### Шаг 1 - Загрузка данных

Загрузите данные из [репозитория UCI](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset) и сохраните их локально. Эти данные будем использовать как входные для модели в реальном времени. 

```bash
# Download original dataset with: python src/pipelines/load_data.py 
raw_data = pd.read_csv(f"../{DATA_DIR}/{FILENAME}")

# Set datetime index 
raw_data = raw_data.set_index('dteday')

raw_data.head()
```

![Untitled](docs/images/Untitled%209.png){width=800}

### Шаг 2 - Определение структуры данных

Укажите категориальные и числовые признаки, чтобы Evidently корректно проводил статистический анализ для каждого из них. Хотя Evidently может автоматически анализировать структуру данных, явное указание типа колонок - хорошая практика.

```python
# Определение признаков
target = 'cnt'
prediction = 'prediction'
numerical_features = ['temp', 'atemp', 'hum', 'windspeed', 'mnth', 'hr', 'weekday']
categorical_features = ['season', 'holiday', 'workingday']

# Создание объекта column_mapping
column_mapping = ColumnMapping()
column_mapping.target = target
column_mapping.prediction = prediction
column_mapping.numerical_features = numerical_features
column_mapping.categorical_features = categorical_features
```

### Шаг 3 - Обучение модели

Подготовьте train и test датасеты, и обучите модель с помощью алгоритма `RandomForestRegressor`.

```python
# Разделение данных
sample_data = raw_data.set_index('dteday').loc['2011-01-01 00:00:00':'2011-01-28 23:00:00']

X_train, X_test, y_train, y_test = model_selection.train_test_split(
    sample_data[numerical_features + categorical_features],
    sample_data[target],
    test_size=0.3
)
regressor = ensemble.RandomForestRegressor(random_state = 0, n_estimators = 50)
regressor.fit(X_train, y_train)
```

### Шаг 4 - Подготовка  *reference* датасета

Для создания отчета о валидации модели сначала подготовьте *reference* датасет. В этом примере мы возьмем данные за 2011 год и сделаем прогнозы для каждого часа.

```python
reference_data = raw_data.loc[train_dates[0]:train_dates[1]]
reference_data['prediction'] = regressor.predict(reference_data[FEATURE_COLUMNS])
reference_data = reference_data.reset_index(drop=True)
```

### Шаг 5 - Подготовка  *current* датасета

Для создания отчета о качестве модели за одну неделю (week 1) подготовьте *current* датасет. В этом примере мы возьмем данные с `2011-03-07 00:00:00` по `2011-03-13 23:00:00`.

```python
# Выборка данных для week 1
current_dates = prediction_batches[0]
current_data = raw_data.loc[current_dates[0]:current_dates[1]]  

# Расчет прогнозов для `current` датасета
current_prediction = regressor.predict(current_data[numerical_features + categorical_features])
current_data['prediction'] = current_prediction
current_data = current_data.reset_index(drop=True)
```

### Шаг 6 - Построение отчета о качестве модели

Теперь можно сгенерировать отчет о качестве модели. Включим в отчет только несколько метрик.

```python
model_report = Report(metrics=[
    RegressionQualityMetric(),
    RegressionErrorPlot(),
    RegressionErrorDistribution()
])
model_report.run(...)
```

Можно визуализировать отчет прямо в Jupyter Notebook используя команду 

```bash
model_report.show(mode='inline')
```

![Untitled](docs/images/Untitled%2010.png){width=800}

### Шаг 7 - Извлеките метрики качестве модели и отчета Evidently

Для получения метрик, таких как средняя ошибка (ME) и средняя абсолютная ошибка (MAE), из отчета, приходится немного "покопаться" в отчете.

> ℹ️ В момент написания тьюториала нет удобного API для извлечения метрик из отчета. В будущем, возможно, это изменится.

Для тьюториала мы создали функцию `get_metrics_from_report`, которая извлекает метрики из отчета и возвращает словарь с результатами.

```python

def get_model_monitoring_metrics(
    regression_quality_report: Report
) -> Dict:

    metrics = {} 
    report_dict = regression_quality_report.as_dict()
    
    metrics['me'] = report_dict['metrics'][0]['result']['current']['mean_error']
    metrics['mae'] = report_dict['metrics'][0]['result']['current']["mean_abs_error"]
    metrics['rmse'] = report_dict['metrics'][0]['result']['current']["rmse"]
    metrics['mape'] = report_dict['metrics'][0]['result']['current']["mean_abs_perc_error"]
    
    return metrics
```

### Шаг 8 - Логирование и визуализация отчета о модели в MLflow 

Теперь, когда у вас есть отчет о качестве модели, вы можете сохранить его в MLflow. Это позволит вам визуализировать отчет в MLflow UI и сравнивать качество моделей в MLflow Experiments.

Покажем, как описанные выше шаги мониторинга можно применить для каждого периода.  Для этого мы разобьем данные на батчи по неделям и будем запускать мониторинг для каждого батча.

```python

# Запуск мониторинга для каждого батча
for current_dates in prediction_batches:

    # Создание нового MLflow Run для каждого батча
    # Дату окончания батча можно использовать как название Run
    with mlflow.start_run(run_name=current_dates[1]) as run: 
        
        # Даты начала и окончания батча можно сохранить как параметры
        mlflow.log_param("begin", current_dates[0])
        mlflow.log_param("end", current_dates[1])
        
        # Подготовка `current` датасета и отчета для батча 
        # Предполагаем, что `reference` датасет уже подготовлен
        current_data = ...  # см. Шаг 5 - Подготовка  *current* датасета
        model_report = ...  # см. Шаг 6 - Построение отчета о качестве модели
        
        # Подготовка метрик для MLflow 
        # см. Шаг 7 - Извлеките метрики качестве модели из отчета Evidently
        model_metrics = get_model_monitoring_metrics(model_report)

        # Логирование отчета в MLflow
        mlflow.log_metrics(model_metrics)
        
        # Логирование HTML отчета в MLflow
        monitoring_report_path = f"../{REPORTS_DIR}/model_monitoring_report.html"
        model_report.save_html(monitoring_report_path)
        mlflow.log_artifact(monitoring_report_path)
```

В результате в MLflow UI ([http://127.0.0.1:5000/](http://127.0.0.1:5000/)) вы увидите результаты запуска мониторинг и отчеты внутри.

![mlflow](docs/images/4-8-mlflow.png){width=800}

> ⚠️ В предыдущих версиях MLflow отчеты открывались полностью. В последних версиях область прокрутки отчетов очень узкая. Надеемся, это скоро починят.

## 🎱 5 - Мониторинг данных с Great Expectations (GX)

Great Expectations - это инструмент для управления качеством данных, который позволяет устанавливать и проверять "ожидания" относительно ваших данных.

![Great Expectations](docs/images/5-gx-about-1.png){width=800}
> ℹ️ Источник: [About Great Expectations OSS](https://docs.greatexpectations.io/docs/oss/about/)

**Зачем использовать Great Expectations?**

> 💡 Expectation это, по сути, модульные тесты для ваших данных

- Тестирование и валидация данных
- Проверка корректности трансформаций данных
- Мониторинг качества данных
- Проверка соответствия данных бизнес-правилам
- Документация данных

### Шаг 1 - Загрузите данные

> 💡 Откройте пример в `notebooks/3-great-expectations.ipynb`

Для начала работы необходимо импортировать Great Expectations и загрузить данные.

```python
import great_expectations as gx
```

В качестве данных для примера используется набор данных по поездкам на такси в Нью-Йорке. Данные можно скачать с [Amazon S3](https://d37ci6vzurychx.cloudfront.net/trip-data/yellow_tripdata_2019-01.parquet).

> ℹ️ Инструкция как скачать датасет в разделе [👩‍💻 1 - Установка](#1-установка)

Можно заглянуть внутрь файла и посмотреть на данные:

```python
df = pd.read_parquet('../data/yellow_tripdata_2019-01.parquet').sample(10000)
df.info()
```

Датасет содержит 19 столбцов четырех типов данных `datetime64[ns]`, `float64`, `int64`, `object`.

![Data Overview](docs/images/5-1-data-overview.png){width=800}

### Шаг 2 - Создайте Data Context

Data Context - это основной интерфейс для работы с Great Expectations. Он позволяет создавать и управлять наборами ожиданий (suites), источниками данных (datasources), а также проверять качество данных.

![Data Context](docs/images/5-2-gx-data_context_does_for_you.png){width=800}

Создайте Data Context

```python
context = gx.get_context(project_root_dir="..")
```

При указании `project_root_dir` аргумента:

- В корне репозитория создается директория `gx` (Great Expectations использует эту директорию для хранения конфигураций)
- Конфигурация Data Context сохраняется в файл `gx/great_expectations.yml`

> ℹ️ Подробнее о Data Context: [Instantiate a Data Context](https://docs.greatexpectations.io/docs/oss/guides/setup/configuring_data_contexts/instantiating_data_contexts/instantiate_data_context)

### Шаг 3 - Подключите данные и создайте Validator

Валидатор (`Validator`) - это объект, ответственный за выполнение набора валидации (`Expectation Suite`) на наборе данных из датасета (`Batch Request`). 

Рассмотрим два способа создания `Validator`.

**Способ 1 - Для этого тьюториала и простых кейсов**

Запустите следующую команду, чтобы подключиться к загруженным данным в `.parquet`, и создать объект `Validator`:

```python
validator = context.sources.pandas_default.read_parquet(
    '../data/yellow_tripdata_2019-01.parquet', 
)
```

В этом примере кода используется стандартный `Data Source` внутри уже созданного `Data Context` для Pandas, чтобы получить доступ к данным из файла.

**Способ 2 - Для практического применения**
Другой способ - это создание использовать метод `get_validator` объекта `Data Context`. Он предполагает следующий алгоритм: 

1. Создание `Data Source` для доступа к данным
2. Создание `Asset` для доступа к конкретному файлу или таблице
3. Создание `Batch Request` для запроса данных
4. Создание `Validator` для валидации данных

Разберем этот пример, используя код ниже. 

1. **Определение источника данных**:
   Источник данных (Data Source) обеспечивает стандартный API для доступа и взаимодействия с данными из разнообразных источников.

   ```python
   datasource = context.sources.add_pandas_filesystem(
       name='local_dir',               # Имя источника данных (произвольное)
       base_directory="../data"        # Путь к директории с данными
   )
   ```

   Здесь создается новый источник данных, работающий с файлами, находящимися в локальной директории `../data`.

2. **Добавление актива (Asset) к источнику данных**:
   `Asset`` представляет собой специфичную для источника данных сущность, например, таблицу в базе данных или файл в файловой системе.

   ```python
   # Регулярное выражение должно соответствовать именам файлов в директории данных
   asset = datasource.add_parquet_asset(
       name="parquet_asset",
       batching_regex=r"yellow_tripdata_(?P<year>\d{4})-(?P<month>\d{2}).parquet",
       order_by=["year", "month"],
   )
   ```

   Здесь создается актив для работы с файлами `.parquet`. Используется регулярное выражение для идентификации файлов по шаблону имени и группировки их по году и месяцу.

3. **Создание запроса на пакет данных (Batch Request)**:
   `Batch Request` используется для запроса пакета данных для валидации.

   ```python
   batch_request = asset.build_batch_request(options={"year": "2019", "month": "01"})
   ```

   В этом примере создается запрос на пакет данных, соответствующий файлу за январь 2019 года. Это делается путем указания опций, соответствующих году и месяцу в названии файла.

4. **Создание Validator**:
    Создайте объект `Validator` с помощью метода `get_validator(...)` у объекта Data Context. 

   ```python
   validator = context.get_validator(
        datasource_name="local_dir",
        data_asset_name="yellow_tripdata_2019-01.parquet",
        batch_request=batch_request
    )
   ```

    Параметры метода get_validator:

    - `datasource_name="local_dir"`: указывает на имя источника данных (Datasource), который используется для доступа к данным.
    - `data_asset_name="yellow_tripdata_2019-01.parquet"`: имя конкретного актива данных (Data Asset), к которому применяется валидация.
    - `batch_request=batch_request`: объект Batch Request, который определяет, какие именно данные должны быть загружены для валидации. 

    Этот код полезен для создания настраиваемых конвейеров обработки и валидации данных в Great Expectations, особенно когда работа идет с большим количеством файлов, имеющих структурированные названия.

Созданный любым способом Validator является центральным компонентом в процессе валидации данных с использованием Great Expectations. Он позволяет не только проверять данные на соответствие заранее заданным критериям, но и документировать результаты этих проверок.

### Шаг 4 - Создание ожиданий (Expectations)

Great Expectations позволяет создавать Expectations и организовывать их в Expectations Suites, которые содержат правила или условия, применяемые к вашим данным.

```bash
validator.expect_column_values_to_be_between(column='payment_type', min_value=0, max_value=3, mostly=0.9)
validator.expect_column_values_to_be_of_type(column='payment_type', type_='int64')
```

В данном примере мы устанавливаем ожидание, что значения столбца `payment_type` будут находиться в определенном диапазоне и иметь определенный тип данных. Эти ожидания помогут нам убедиться, что данные соответствуют определенным критериям качества.

### Шаг 5 - Сохраните набор ожиданий (Expectation Suite)

Expectation Suite можно сохранять и использовать для проверки качества данных в будущем.

Создайте набор ожиданий и добавьте к нему правила:

```python
validator.save_expectation_suite('../gx/expectations/first_expectation_suite.json')
```

В результате создается файл `first_expectation_suite.json` в директории `gx/expectations`. Этот файл содержит набор ожиданий, который можно использовать для проверки качества данных в будущем.

### Шаг 6 - Валидация новых данных с Great Expectations

В этом шаге мы рассмотрим, как использовать Great Expectations для валидации новых данных. Мы будем использовать ранее сохранённый набор ожиданий (expectation suite) и применим его к новому набору данных.

1. **Получение Data Context**:
   Инициализируем контекст валидации, указав корневой каталог, где хранятся настройки Great Expectations. Назовем его `validation_context`, чтобы отличать от `context`, который мы использовали ранее.

   ```python
   validation_context = gx.get_context(context_root_dir="../gx")
   ```

2. **Список сохранённых Expectation Suites**:
   Получаем список всех сохранённых наборов ожиданий.

   ```python
   validation_context.list_expectation_suite_names()
   ```

   Эта команда выведет только сохраненный ранее набор ожиданий:

   ```bash
   ['first_expectation_suite']
   ```

3. **Загрузка Expectation Suite**:
   Загружаем определённый набор ожиданий, который будет использоваться для валидации.

   ```python
   validation_suite = validation_context.get_expectation_suite("first_expectation_suite")
   ```

4. **Загрузка данных для валидации**:
   Загружаем тестовые данные из CSV-файла.

   ```python
   test = pd.read_csv("../data/test.csv")
   ```

5. **Создание валидатора для тестовых данных**:
   Создаём валидатор для тестовых данных, используя ранее определённый набор ожиданий.

   ```python
   test_data_validator = (
        validation_context.sources.add_pandas("taxi_test_datasource")
        .read_dataframe(
            test, 
            asset_name="taxi_test", 
            batch_metadata={"type": "test"})
        )
   test_data_validator.expectation_suite_name = "first_expectation_suite"
   ```

6. **Запуск валидации**:
   Добавляем или обновляем чекпоинт, который связывает валидатор и набор ожиданий.

   ```python
   checkpoint = validation_context.add_or_update_checkpoint(
       name="my_taxi_validator_checkpoint", 
       validator=test_data_validator,
       expectation_suite_name="first_expectation_suite"
   )
   ```

   Запускаем чекпоинт для выполнения валидации.

   ```python
   checkpoint_result = checkpoint.run()
   ```

7. **Просмотр результатов валидации**:
   Открываем Data Docs для просмотра результатов валидации.

   ```python
   validation_context.open_data_docs()
   ```

   ![Data Docs](docs/images/5-6-results.png){width=800}

Этот процесс позволяет систематически проверять новые данные на соответствие установленным ожиданиям, обеспечивая тем самым их качество и надёжность.


## 📊 6 - Мониторинг данных с Grafana и PostgreSQL

> 💡 Откройте пример в  `notebooks/4-monitor-model-with-grafana.ipynb`

[Grafana](https://grafana.com/oss/grafana/) - популярный инструмент визуализации данных, который может использоваться для создания информативных дашбордов, отслеживающих качество модели и ML сервисов в реальном времени.

В этом разделе рассмотрим пример, как настроить систему мониторинга данных и моделей, используя Grafana и PostgreSQL.

### Шаг 1 - Запуск Grafana и PostgreSQL

> 💡 Можно пропустить этот шаг, если вы выполнили его на этапе установки в разделе [👩‍💻 1 - Установка](#1-установка)

Запустить оба сервиса Grafana и PostgreSQL можно с помощью Docker Compose:

```bash
docker compose up
```

Откройте в браузере Grafana UI по адресу [http://localhost:3000](http://localhost:3000).

> ⚠️ При первом запуске Grafana попросит ввести логин и пароль. По умолчанию это `admin` и `admin`. После входа в систему можно изменить пароль

![Data Docs](docs/images/6-1-welcome.png){width=800}

Перейдите в список дашбордов: 

![Data Docs](docs/images/6-2-browse-dashboard.png){width=800}

Откройте дашборд `Model Performance (Regression)`:

![Data Docs](docs/images/6-3-open-dashboard.png){width=800}

Вы увидите пустой дашборд без данных и это нормально! На следующих шагах мы добавим данные и настроим дашборд.

![Data Docs](docs/images/6-4-no-data-1.png){width=800}

### Шаг 2 - Расчет метрик мониторинга

Пример в `notebooks/4-monitor-model-with-grafana.ipynb` основа на примере `notebooks/2-monitor-model.ipynb`. Возьмем те же самые данные, ту же модель и отчеты Evidently.

Но, в отличие от предыдущего примера, мы будем сохранять метрики в базу данных PostgreSQL, а не в MLflow. Это позволит нам визуализировать метрики в Grafana.

Для извлечений метрик из отчета Evidently мы будем использовать функцию `get_model_monitoring_metrics`, которую мы создали ранее.

```python
def get_model_monitoring_metrics(
    regression_quality_report: Report
) -> Dict:

    metrics = {} 
    report_dict = regression_quality_report.as_dict()
    
    metrics['me'] = report_dict['metrics'][0]['result']['current']['mean_error']
    metrics['mae'] = report_dict['metrics'][0]['result']['current']["mean_abs_error"]
    metrics['rmse'] = report_dict['metrics'][0]['result']['current']["rmse"]

    # TODO: Uncomment for "6. Add your own metrics"
    # metrics['mape'] = report_dict['metrics'][0]['result']['current']["mean_abs_perc_error"] 
    
    return metrics
```

> ⚠️ Обратите внимание, что здесь и в некоторых других ячейках мы закомментировали код для метрики `mape`.
> НЕ раскомментируйте эти строки! Вы сможете сделать это позже, на Шаге 6 - Кастомизация дашборда для вашего проекта.


### Шаг 3 - Подготовка базы данных для мониторинга

Создайте таблицу `model_performance` в базе данных PostgreSQL для хранения метрик модели.

```python
class ModelPerformanceTable(Base):
    """Implement table for model performance metrics."""

    __tablename__ = "model_performance"
    id = Column(Integer, primary_key=True)
    timestamp = Column(Float)
    me_default_sigma = Column(Float)
    mean_abs_error_default = Column(Float)
    rmse_default = Column(Float)
```

Для создания таблицы выполните вспомогательный скрипт:

```python
create_db(MONITORING_DB_URI)
```

В результате создается база данных `monitoring_db` и таблица `model_performance`, однако она все еще пустая пустая.

![Data Docs](docs/images/6-4-no-data-2.png){width=800}


### Шаг 4 - Мониторинг качества модели

В этом шаге мы реализуем процесс мониторинга качества модели. Используя библиотеку Evidently, мы оцениваем качество модели и сохраняем полученные метрики в базу данных.

```python

# ...Создание объекта SQLAlchemy Session
sqa_session = Session()

for current_dates in prediction_batches:

    # ...подготовка отчета Evidently 
    
    # Извлечение метрик из отчета Evidently
    model_metrics = get_model_monitoring_metrics(model_report)

    # Запись метрик в базу данных
    timestamp = pendulum.parse(batch_end).timestamp()
    model_performance = ModelPerformanceTable(
        timestamp=timestamp,
        me_default_sigma=model_metrics["me"],
        mean_abs_error_default=model_metrics["mae"],
        rmse_default=model_metrics["rmse"],
    )
    sqa_session.add(model_performance)
    sqa_session.commit()

# Закрытие сессии
sqa_session.close()
```

После запуска этого кода в базе данных появятся записи с метриками качества модели. Откройте Grafana и обновите дашборд - вы увидите метрики на графиках! 🎉

![Data Docs](docs/images/6-5-dashboard-1.png){width=800}

Возможно вам придется обновить дашборд и нажать `Zoom to data` для того, чтобы графики отобразились корректно.

![Data Docs](docs/images/6-5-dashboard-2.png){width=800}

Кстати, это нормально, если вы НЕ увидите данных для MAPE метрики. Мы договорились, что вы сможете починить их на шаге 6.

![Data Docs](docs/images/6-5-dashboard-3.png){width=800}

### Шаг 5 - Настройка дашборда

Итак, мы настроили систему мониторинга, но дашборд может выглядеть не очень информативно. Grafana предоставляет мощный инструментарий для кастомизации и настройки дашборда.

Кликнете на выпадающее меню панели метрики `ME` и выберите `Edit`:

![Data Docs](docs/images/6-6-edit-1.png){width=800}

В открывшемся окне вы можете настроить заголовок панели, изменить запрос к БД, добавить новые графики и многое другое.

![Data Docs](docs/images/6-6-edit-2.png){width=800}

Давайте начнем с изменения способа визуализации. Откройте список доступных визуализаций и выберите `Guage` (и затем примените `Apply`).

![Data Docs](docs/images/6-6-edit-3.png){width=800}

Теперь метрика `ME` будет отображаться в виде графика-шкалы (в data-фольклоре "спидометр" 🥸 )

![Data Docs](docs/images/6-6-edit-4.png){width=800}

Теперь, давайте изменим запрос к БД. Нажмите на вкладку `Query` и замените имя поля на `rmse_default`. Затем нажмите кнопку `Run query`. Значение метрики на панели должно измениться на последнее значение RMSE.

![Data Docs](docs/images/6-6-edit-5.png){width=800}

Теперь, попробуем классную фичу - Suggestions. Нажмите на вкладку `Suggestions` и выберите `Auto`. Grafana предложит вам несколько вариантов графиков, которые могут быть полезны для визуализации метрик.

![Data Docs](docs/images/6-6-edit-6.png){width=800}

Для примера, выберете `Bar Chart with color gradient` и установите `Thresholds` на `0`, `75` и `80` процентов. Затем нажмите `Apply`.

Теперь график должен выглядеть примерно так:

![Data Docs](docs/images/6-6-edit-7.png){width=800}

### Шаг 6 - Кастомизация дашборда для вашего проекта

Вы можете добавить дополнительные метрики, специфичные для вашей модели или бизнес-процессов, в систему мониторинга, и отбразать их на дашборде.

Алгоритм добавления новых метрик:

1. Рассчитать новую метрику.
2. Добавить метрики в схему таблицы базы данных.
3. Записать метрики в базу данных.
4. Добавить или обновить панель/дашборд в Grafana.

Предлагаем вам немного попрактиковаться! Добавьте метрику `MAPE` в систему мониторинга и отобразите ее на дашборде.

**TODO: Добавьте метрику `MAPE` в дашборд**

1. Расчет новой метрики:

    > Раскомментируйте и запустите раздел `3.2 Расчет метрик мониторинга`.

2. Добавление метрик в схему таблицы базы данных:

    > Раскомментируйте и запустите ячейки в разделе `4. Подготовка базы данных для мониторинга`.

3. Запись метрик в базу данных:

    > Запустите ячейки в разделе `5. Мониторинг качества модели`.

4. Добавление или обновление панели/дашборда:

    > Обновите дашборд в Grafana, чтобы отобразить новые метрики.

В результате, вы должны увидеть метрику `MAPE` на дашборде.

![Data Docs](docs/images/6-6-edit-8.png){width=800}

## 🔗 Дополнительные ресурсы

- [Monitoring ML systems in production. Which metrics should you track?](https://www.evidentlyai.com/blog/ml-monitoring-metrics)
- [ML serving and monitoring with FastAPI and Evidently](https://www.evidentlyai.com/blog/fastapi-tutorial)
- [Batch ML monitoring blueprint: Evidently, Prefect, PostgreSQL, and Grafana](https://www.evidentlyai.com/blog/batch-ml-monitoring-architecture)
- [Great Expectations: Quickstart](https://docs.greatexpectations.io/docs/oss/tutorials/quickstart)
- [Why data quality is key to successful MLOps](https://greatexpectations.io/blog/ml-ops-data-quality)

![Основы ML мониторинга для Data Science](docs/images/monitoring-notes-1.png)

[⬆️ Содержание](#-содержание)