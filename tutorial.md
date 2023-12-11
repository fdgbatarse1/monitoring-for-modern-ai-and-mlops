# Основы ML мониторинга для Data Science

# Тьюториал: ****Основы ML мониторинга для Data Science****

## **👀 Overview**

🎓 **Что это такое?** Представляем вашему вниманию тьюториал "Основы ML мониторинга для Data Science". Это ваш путеводитель в мире мониторинга ML моделей и данных. Мы не просто покажем вам, как это делается, но и расскажем о популярных инструментах в этой области, таких как Evidently, Great Expectations и Grafana.

👩🏻‍💻 **Для кого этот тьюториал?** Если вы Data Scientist или начинающий ML инженер, этот курс идеально подойдет для вас. Мы начнем с основ и постепенно перейдем к более продвинутым темам.

**🎯 Что вас ждет в этом тьюториале?**

- Знакомство с задачами и инструментами ML мониторинга.
- Настройка мониторинга моделей и данных с помощью Evidently.
- Изучение мониторинга данных с Great Expectations.
- Освоение мониторинга ML сервисов в Grafana.

🔍 **Как это устроено?** Вам не придется долго искать нужную информацию. Тьюториал содержит исчерпывающие примеры кода и пошаговые инструкции в формате Markdown.

⏱️ **Сколько времени потребуется?** Вам понадобится всего 40 минут, чтобы погрузиться в мир ML мониторинга и выйти оттуда уже готовым к применению новых знаний.

## **👩‍💻 Установка**

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
pip install -r requirements-dev.txt
```

3.  **Загрузите данные** 

Этот шаг подготовки включает загрузку данных из [набора данных по аренде велосипедов](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset) в директорию **`data/`**.

```bash
python src/load_data.py
```

**4. Запустите MLflow UI**

To start the MLflow UI, run:

```bash
mlflow ui
```

And then navigate to [http://localhost:5000](http://localhost:5000) in your browser

**5. Запустите Jupyter Lab or Jupyter Notebook**

```bash
jupyter lab
```

## 1 - Задачи и инструменты ML мониторинга для Data Science

### Типичный ML пайплайн для Batch Scoring

![Untitled](docs/images/Untitled.png)

Прежде чем говорить о мониторинге, давайте разберем типичный ML пайплайн для batch scoring. Этот процесс включает в себя несколько ключевых этапов:

1. **T - 1 (Тренировка на Исторических Данных)**: На этом этапе модель обучается на исторических данных (History / Reference Data). Эти данные представляют собой прошлые наблюдения, которые помогают модели учиться на реальных примерах.
2. **T = 0 (Прогнозирование)**: На этом этапе модель используется для прогнозирования на текущих данных (Current Data). Это ключевой момент, когда модель применяется для получения предсказаний.
3. **T + 1 (Мониторинг и Оценка)**: После прогнозирования следует этап мониторинга. Здесь данные о реальных результатах (Ground Truth Data) сравниваются с предсказаниями модели. Это позволяет оценить качество и точность модели.

### Задачи мониторинга в ML

- **Состояние системы (программное обеспечение):** На базовом уровне находится мониторинг бэкенда, который включает в себя проверку успешности выполнения задач предсказания и производительности сервиса.
- **Данные:** Следующий уровень фокусируется на качестве и целостности данных. Важно отслеживать, подходят ли данные для создания предсказаний и обучения модели.
- **ML Модель:**  На этом уровне происходит мониторинг самой модели ML. Оценивается точность предсказаний, соответствие модели задачам и ее доверие.
- **Бизнес или продуктовые KPI:** На вершине пирамиды находятся ключевые показатели эффективности, связанные с бизнес-целями и влиянием модели на продукт.

![Source: [https://www.evidentlyai.com/blog/ml-monitoring-metrics](https://www.evidentlyai.com/blog/ml-monitoring-metrics) ](docs/images/Untitled%201.png)

Source: [https://www.evidentlyai.com/blog/ml-monitoring-metrics](https://www.evidentlyai.com/blog/ml-monitoring-metrics) 

В контексте мониторинга ML пайплайнов ключевые задачи включают в себя:

1. **Мониторинг модели (Monitor Model)**: Оценка производительности модели на новых данных, анализ ее стабильности и точности со временем.
2. **Мониторинг данных (Monitor Data)**: Отслеживание изменений в характеристиках входных данных (таких как распределение или возникновение новых паттернов), которые могут повлиять на работу модели.
3. **Мониторинг смещения предсказаний (Monitor Prediction Drift)**: Анализ изменений в предсказаниях модели со временем, выявление смещения и ухудшения качества прогнозов.

### Инструменты для ML мониторинга

![Untitled](docs/images/Untitled%202.png)

Для эффективного мониторинга пайплайнов ML существует ряд инструментов. В данном тьюториале рассмотрим три из них:

- **Evidently**: Позволяет анализировать качество модели и данных, обнаруживать смещения в прогнозах и многое другое.
- **Great Expectations**: Помогает валидировать качество данных, обеспечивая их соответствие определенным критериям.
- **Grafana**: Инструмент визуализации данных, который может использоваться для создания информативных дашбордов, отслеживающих производительность модели и данных в реальном времени.

## 2 - Быстрый старт метриками и отчетами Evidently

<aside>
💡 Jupyter Notebook with the example:  `1-getting-started-tutorial.ipynb`

</aside>

Идея Evidently очень проста: представить API для расчета рассчитывает множество метрик для данных и моделей, и организовать их в удобные отчеты. Отчеты являются наиболее эффективным способом визуального анализа и отладки ваших моделей и данных. Вы можете сохранять отчеты в форматах HTML или JSON (снимки). Это позволяет использовать Evidently для множества сценариев валидации и мониторинга в приложениях машинного обучения [для online инференса](https://evidentlyai.com/blog/fastapi-tutorial) и [batch скоринга](https://www.evidentlyai.com/blog/batch-ml-monitoring-architecture):

- сохранять отчеты мониторинга в файлах HTML и использовать их для анализа и отладки моделей и данных,
- получать значения конкретных метрик и записывать их во внешние базы данных (например, PostgreSQL) и инструменты для создания дашбордов (например, Grafana),
- сохранять отчеты мониторинга (как снимки) в файлах JSON со временем и запускать [Панель мониторинга Evidently](https://docs.evidentlyai.com/user-guide/monitoring/monitoring_overview) для непрерывного мониторинга.

![Untitled](docs/images/Untitled%203.png)

В этом разделе вы познакомитесь  Evidently для мониторинга ML моделей и данных.   Для завершения раздела вам понадобятся базовые знания Python. Вы должны справиться примерно за 15 минут.

### Шаг 1: Импорт Evidently

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

### Шаг 2: Подготовка данных

В примерах тьюториала вы работаете с готовым набором данных. На практике вы должны использовать логи предсказаний модели. Они могут включать входные данные, предсказания модели и истинные метки или фактические данные, если они доступны.

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

![Untitled](docs/images/Untitled%204.png)

Разделите набор данных, взяв 5000 объектов для эталонных и текущих наборов данных.

```python
reference = housing_data.sample(n=5000, replace=False)
current = housing_data.sample(n=5000, replace=False)

```

Первый `reference` датасет - это эталонный набор данных. В качестве `reference`   обычно используют данные для обучения модели или выборку из истории *production* данных. Второй `current` набор данных - это текущие *production* данные, которые вы хотите  сравнить с эталоном.

В большинстве случает Evidently использует два датасета ( `reference` и `current` ) для расчета метрик и генерации отчетов. 

![Original image: [https://docs.evidentlyai.com/user-guide/input-data/data-requirements](https://docs.evidentlyai.com/user-guide/input-data/data-requirements) ](docs/images/Untitled%205.png)

Original image: [https://docs.evidentlyai.com/user-guide/input-data/data-requirements](https://docs.evidentlyai.com/user-guide/input-data/data-requirements) 

<aside>
💡 Практические рекомендации: 
- Для своего проекта вы можете подготовить два набора данных с одинаковой схемой. 
- Вы также можете взять один набор данных и явно указать строки для эталонных и текущих данных.
- Вы можете иметь несколько `reference` датасетов

</aside>

### Шаг 3: Построение Data Drift отчетов

Отчеты **Evidently** помогают исследовать и устранять проблемы качества данных и моделей. Они рассчитывают различные метрики и генерируют панель управления с богатыми визуализациями. Для начала вы можете использовать **Metric Presets** - ****шаблонные наборы метрик и отчеты для определенных задач. 

Давайте начнем с **Data Drift.** Этот пресет сравнивает распределения признаков модели и показывает, какие из них изменились. 

Чтобы получить отчет, создайте соответствующий объект `Report`, перечислите включаемый пресет и укажите на созданные ранее эталонные и текущие наборы данных:

```python
# Созадим отчет с нужным набором метрик или пресетом
report = Report(metrics=[
    DataDriftPreset(),
])

# Запустим генерацию отчета
report.run(reference_data=reference, current_data=current)

# Для визуализации отчета в Jupyter Notebook
report.show(mode='inline')
```

![Untitled](docs/images/Untitled%206.png)

Если вы нажмете на отдельные признаки, вы увидите дополнительные графики для анализа. Например, распределение таргет переменной. 

![Untitled](docs/images/Untitled%207.png)

### Шаг 4: Кастомизация и сохранение отчетов

Отчеты Evidently обладают высокой степенью настраиваемости. Вы можете определить, какие метрики включать и как их рассчитывать.

Например, вы можете перечислить несколько метрик, оценивающих индивидуальные статистики для определенного столбца.

```python
report = Report(metrics=[
    ColumnSummaryMetric(column_name='AveRooms'),
    ColumnQuantileMetric(column_name='AveRooms', quantile=0.25),
    ColumnDriftMetric(column_name='AveRooms')
])

report.run(reference_data=reference, current_data=current)
report

```

Вы увидите объединенный отчет, который включает в себя несколько метрик.

![Untitled](docs/images/Untitled%208.png)

<aside>
💡 Больше примеров и кастомизации отчетов в официальном [Quickstart for Reports and Tests](https://docs.evidentlyai.com/get-started/tutorial#4.-get-the-data-drift-report)

</aside>

Вы можете конвертировать сгенерированные отчеты с объект Python или JSON или сохранить HTMД файл. 

```python
report.as_dict() # Удобно для парминга отчета и получения отдельных метрик
report.save_html("file.html") # Удобно открыть и посмотреть в браузере 
```

Вы также можете сохранить вывод в виде snapshot Evidently JSON. Это позволит вам визуализировать качество модели или данных со временем с помощью [ML Evidently Dashboards.](https://docs.evidentlyai.com/get-started/tutorial-monitoring)

```python
report.save("snapshot.json")
```

## 3 - Мониторинга моделей и данных с Evidently и MLflow

<aside>
💡 Jupyter Notebook with the example:  `2-monitor-model.ipynb`

</aside>

### **Шаг 1. Загрузка данных**

Загрузите данные из [репозитория UCI](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset) и сохраните их локально. Эти данные будем использовать как входные для модели в реальном времени. Для работы с продуктивными моделями вам потребуется доступ к логам предсказаний.

```bash
# Download original dataset with: python src/pipelines/load_data.py 
raw_data = pd.read_csv(f"../{DATA_DIR}/{FILENAME}")

# Set datetime index 
raw_data = raw_data.set_index('dteday')

raw_data.head()
```

![Untitled](docs/images/Untitled%209.png)

### Шаг 2. Определение структуры колонок

Укажите категориальные и числовые признаки, чтобы Evidently корректно проводил статистический анализ для каждого из них. Хотя Evidently может автоматически анализировать структуру данных, явное указание типа колонок поможет минимизировать ошибки.

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

### Шаг 3. Обучение модели

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

### Шаг 4. Построение отчета о валидации модели

Для создания отчета о валидации модели сначала рассчитайте предсказания как для обучающего, так и для тестового набора данных, и сгенерируйте стандартный отчет с метриками `RegressionPreset` от Evidently.

```python
# Расчет предсказаний
preds_train = regressor.predict(X_train)
preds_test = regressor.predict(X_test)

# Добавление предсказаний к наборам данных `train` и `test`
X_train['target'] = y_train
X_train['prediction'] = preds_train
X_test['target'] = y_test
X_test['prediction'] = preds_test

```

После добавления предсказаний в наборы данных сгенерируйте отчет о производительности с помощью `RegressionPreset` из библиотеки Evidently. Этот отчет позволяет анализировать производительность модели, сравнивая ее предсказания с фактическими значениями в тестовом наборе. Затем извлеките ключевые метрики, такие как средняя ошибка (ME) и средняя абсолютная ошибка (MAE), из отчета. Эти метрики дают количественную оценку ошибок предсказания модели. Их логично залогировать в MLflow!

```python
# Создание отчета с RegressionPreset
regression_performance_report = Report(metrics=[
    RegressionPreset(),
])
regression_performance_report.run(
    reference_data=X_train,
    current_data=X_test,
    column_mapping=column_mapping)

# Извлеч ение метрик обучения модели из отчета
train_report_metrics = regression_performance_report.as_dict()
me = train_report_metrics['metrics'][0]['result']['current']['mean_error']
mae = train_report_metrics['metrics'][0]['result']['current']["mean_abs_error"]

```

Можно визуализировать отчет прямо в Jupyter Notebook используя команду 

```bash
regression_performance_report.show(mode='inline')
```

![Untitled](docs/images/Untitled%2010.png)

## 4- Мониторинг данных с Great Expectations

Great Expectations - это инструмент для управления качеством данных, который позволяет устанавливать и проверять "ожидания" относительно ваших данных.

### Шаг 1: Импорт необходимых библиотек

Для начала работы с Great Expectations необходимо импортировать ряд библиотек:

```bash
import datetime
import numpy as np
import pandas as pd

import great_expectations as gx

from matplotlib import pyplot as plt

%matplotlib inline

```

### Шаг 2: Загрузка и подготовка данных

Далее загрузите и подготовьте данные для анализа:

```bash
!wget <https://d37ci6vzurychx.cloudfront.net/trip-data/yellow_tripdata_2019-01.parquet>

df = pd.read_parquet('yellow_tripdata_2019-01.parquet')
sample_df = df.sample(10000)

df_gx = gx.dataset.PandasDataset(sample_df)
df_gx.head(2)

```

### Шаг 3: Обзор набора данных

Проведите первоначальный анализ набора данных:

```bash
df_gx.dtypes
plt.hist(df_gx['payment_type'])
plt.hist(df_gx['passenger_count'])

```

### Шаг 4: Создание ожиданий

Great Expectations позволяет создавать наборы ожиданий (suites), которые содержат правила или условия, применяемые к вашим данным. Эти наборы ожиданий можно сохранять и использовать для проверки качества данных в будущем.

```bash
df_gx.expect_column_values_to_be_between(column='payment_type', min_value=0, max_value=3, mostly=0.9)
df_gx.expect_column_values_to_be_of_type(column='payment_type', type_='int64')

```

В данном примере мы устанавливаем ожидание, что значения столбца `payment_type` будут находиться в определенном диапазоне и иметь определенный тип данных. Эти ожидания помогут нам убедиться, что данные соответствуют определенным критериям качества.

Создайте контекст, который является основным интерфейсом для работы с Great Expectations:

```bash
context = gx.get_context()
```

Загрузите и подготовьте набор данных для анализа:

```bash
df = pd.read_parquet('yellow_tripdata_2019-01.parquet')
train = df.head(1000)
test = df.tail(1000)
train.to_csv('train.csv', index=False)
test.to_csv('test.csv', index=False)

validator = context.sources.pandas_default.read_csv("train.csv")
```

Создайте источник данных и добавьте к нему актив:

```bash
datasource_name = 'tripdata_train'
datasource = context.sources.add_pandas(datasource_name)

asset_name = 'tripdata_asset'
path_to_data = '/content/train.csv'
asset = datasource.add_csv_asset(asset_name, filepath_or_buffer=path_to_data)

batch_request = asset.build_batch_request()

```

Извлеките и обработайте партии данных:

```bash
tripdata_asset = context.get_datasource("tripdata_train").get_asset("tripdata_asset")
my_batch_request = tripdata_asset.build_batch_request()
batches = tripdata_asset.get_batch_list_from_batch_request(my_batch_request)

for batch in batches:
    print(batch.batch_spec)

```

### Шаг 5: Сохраните набор ожиданий ( `suite` )

Создайте набор ожиданий и добавьте к нему правила:

```bash
suite = context.add_expectation_suite(expectation_suite_name="taxi_suite")
context.add_or_update_expectation_suite("taxi_suite")

validator = context.get_validator(
    batch_request=batch_request,
    expectation_suite_name="taxi_suite",
)
validator.head()

expectation_validation_result = validator.expect_column_values_to_not_be_null(
    column="VendorID"
)
print(expectation_validation_result)

validator.expect_column_values_to_not_be_null("payment_type")
validator.expect_column_values_to_be_between(column='payment_type', min_value=0, max_value=4)
validator.expect_column_values_to_be_of_type(column='payment_type', type_='int64')
validator.expect_column_values_to_not_be_null(column = "tip_amount", mostly = .9)

validator.save_expectation_suite(discard_failed_expectations=False)

```

Сохраните созданный набор ожиданий в файл JSON для последующего использования:

```bash
import json

with open("taxi_suite.json", "w") as my_file:
    my_file.write(
        json.dumps(suite.to_json_dict())
    )

suite.show_expectations_by_expectation_type()

from great_expectations.core.expectation_suite import ExpectationConfiguration

updated_config = ExpectationConfiguration(
    expectation_type="expect_column_values_to_be_between",
    kwargs={
        "auto": True,
        "column": "passenger_count",
        "domain": "column",
        "min_value": 1,
        "max_value": 4,
        "mostly": 1.0,
    },
)
suite.add_expectation(updated_config)

context.save_expectation_suite(suite)
with open("taxi_suite.json", "w") as my_file:
    my_file.write(
        json.dumps(suite.to_json_dict())
    )

```

Таким образом, вы создаете, настраиваете и сохраняете набор ожиданий, который можно использовать для проверки качества данных в будущем.

### Шаг 6: Валидация новых данных с Great Expectations

После создания и сохранения набора ожиданий (suite), его можно использовать для валидации новых данных. Это позволяет проверить, соответствуют ли новые данные установленным критериям качества.

Загрузите и подготовьте тестовые данные:

```bash
test = pd.read_csv("test.csv")

datasource_name = 'tripdata_test'
datasource = context.sources.add_pandas(datasource_name)

asset_name = 'triptest_asset'
path_to_data = '/content/test.csv'
asset = datasource.add_csv_asset(asset_name, filepath_or_buffer=path_to_data)

batch_request = asset.build_batch_request()
batch_list = asset.get_batch_list_from_batch_request(batch_request)
batch_request_list = [batch.batch_request for batch in batch_list]

```

Создайте проверки (validations), указав запросы на партии данных (batch requests) и имя сохраненного набора ожиданий:

```bash
validations = [
    {"batch_request": batch.batch_request, "expectation_suite_name": "taxi_suite"}
    for batch in batch_list
]
```

Создайте контрольную точку (checkpoint) в Great Expectations, которая будет использовать созданные проверки для валидации данных:

```bash
checkpoint = context.add_or_update_checkpoint(
    name="my_taxi_validator_checkpoint", validations=validations
)

checkpoint_result = checkpoint.run()
```

После запуска контрольной точки вы получите результаты проверки данных в соответствии с установленными ожиданиями. Это позволяет автоматизировать процесс проверки качества данных и гарантировать, что новые данные соответствуют установленным стандартам.

## **🔗 Additional Resources**

- **ML serving and monitoring with FastAPI and Evidently** [https://www.evidentlyai.com/blog/fastapi-tutorial](https://www.evidentlyai.com/blog/fastapi-tutorial)
- ****Batch ML monitoring blueprint: Evidently, Prefect, PostgreSQL, and Grafana****  [https://www.evidentlyai.com/blog/batch-ml-monitoring-architecture](https://www.evidentlyai.com/blog/batch-ml-monitoring-architecture)