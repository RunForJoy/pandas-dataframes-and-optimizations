# Pandas: Data Wrangling, Aggregations & Performance Optimizations

[English](#english) | [Русский](#русский)

---

## English

A comprehensive set of Jupyter Notebooks mastering **Pandas** for real-world data engineering and analytics tasks. The project progresses from raw log ingestion and data cleaning to complex relational joins, pivot tables, and low-level speed and RAM optimization benchmarks.

### 🛠 Tech Stack & Tools
* **Core Libraries:** `pandas`, `numpy`, `gc`
* **Environment:** Jupyter Notebook (`%%timeit` magic benchmarking)
* **Data Formats:** Custom delimited logs (`.log`), `CSV`, `JSON`

###  Project Structure (`src/`)

* **`ex00/load_and_save.ipynb`** — **Data Ingestion & Export:** Loading raw server log files with `read_csv`, filtering corrupted header/footer records (`skiprows`, `skipfooter`), indexing timestamps, renaming columns, and exporting with custom delimiters.
* **`ex01/basic_operations.ipynb`** — **Datetime & Descriptive Analytics:** Parsing `datetime64[ns]`, extracting temporal components, binning hours into time-of-day categories via `pd.cut()`, multi-column sorting, computing modes, top/bottom extremes (`nsmallest`, `nlargest`), and calculating the Interquartile Range (`IQR`) from `describe()`.
* **`ex02/preprocessing.ipynb`** — **Data Cleaning Pipeline:** Deduplicating records (`keep='last'`), handling missing values via threshold column dropping (`thresh`), forward-filling (`ffill`), and mean imputation, parsing composite strings with `.apply()`, and exporting structured `JSON`.
* **`ex03/selects_n_aggs.ipynb`** — **Filtering & GroupBy Aggregations:** Multi-condition indexing, multi-level `groupby` aggregations (`median`, `count`, `min`, `max`, `std`) across vehicle brands/models, and identifying repeat traffic offenders.
* **`ex04/enrichment.ipynb`** — **Data Enrichment, Joins & Pivot Tables:** Generating synthetic samples (`random_state=21`), enriching datasets with external surname records, performing all four relational join types (`inner`, `outer`, `left`, `right`), and constructing multi-year `pivot_table` summaries.
* **`ex05/optimizations.ipynb`** — **Speed & Memory Optimization Benchmarks:**
  * *Execution speed (`%%timeit`):* Comparing `iloc` loops, `iterrows()`, `.apply()`, vectorized `Series` operations, and raw NumPy `.values` arrays.
  * *Lookup speed:* Benchmarking unindexed filtering versus hash-indexed (`set_index`) lookups.
  * *Memory footprint (`memory_usage='deep'`):* Reducing RAM consumption by 2–3x via numeric downcasting (`float64` $\rightarrow$ `float32`, minimal `int`), converting `object` strings to `category`, and explicit garbage collection (`gc` / `%reset_selective`).

###  Usage
* Open any notebook in Jupyter Lab / Jupyter Notebook or VS Code: `jupyter notebook src/ex05/optimizations.ipynb`

---

## Русский

Серия аналитических ноутбуков на базе библиотеки **Pandas**, охватывающая полный цикл подготовки и оптимизации табличных данных. Проект проходит путь от загрузки сырых логов и очистки пропусков до реляционных объединений, сводных таблиц и бенчмарков ускорения вычислений и снижения потребления памяти.

###  Стек и инструменты
* **Библиотеки:** `pandas`, `numpy`, `gc`
* **Среда разработки:** Jupyter Notebook (замеры производительности через `%%timeit`)
* **Форматы данных:** Лог-файлы с нестандартными разделителями (`.log`), `CSV`, `JSON`

###  Структура проекта (`src/`)

* **`ex00/load_and_save.ipynb`** — **Загрузка и сохранение данных:** Чтение сырых логов через `read_csv`, отсечение некорректных строк в начале и конце файла (`skiprows`, `skipfooter`), индексация временных меток, переименование столбцов и экспорт с новым разделителем.
* **`ex01/basic_operations.ipynb`** — **Работа с датами и описательная статистика:** Приведение к типу `datetime64[ns]`, извлечение компонентов времени, разбиение часов на интервалы времени суток через `pd.cut()`, одновременная сортировка по нескольким столбцам, расчёт мод, экстремумов (`nsmallest`, `nlargest`) и интерквартильного размаха (`IQR`) на основе `describe()`.
* **`ex02/preprocessing.ipynb`** — **Предобработка и очистка данных:** Удаление дубликатов (`keep='last'`), обработка пропусков (удаление столбцов по порогу `thresh`, заполнение предыдущим значением `ffill` и средним), парсинг составных строк через `.apply()` и экспорт в `JSON`.
* **`ex03/selects_n_aggs.ipynb`** — **Выборки и агрегации:** Фильтрация по сложным условиям, многоуровневая группировка `groupby` (`median`, `count`, `min`, `max`, `std`) по маркам и моделям автомобилей, выявление главных нарушителей по числу и сумме штрафов.
* **`ex04/enrichment.ipynb`** — **Обогащение данных, объединения и сводные таблицы:** Генерация синтетических выборок (`random_state=21`), объединение с внешней таблицей владельцев всеми четырьмя способами (`inner`, `outer`, `left`, `right`) и построение сводных таблиц (`pivot_table`) по годам.
* **`ex05/optimizations.ipynb`** — **Оптимизация скорости и оперативной памяти:**
  * *Скорость вычислений (`%%timeit`):* Сравнение циклов с `iloc`, `iterrows()`, `.apply()`, векторизованных операций над `Series` и прямых вычислений через массивы NumPy `.values`.
  * *Скорость поиска:* Сравнение обычной фильтрации и поиска по индексу (`set_index`).
  * *Оптимизация памяти (`memory_usage='deep'`):* Снижение потребления RAM в 2–3 раза за счёт понижения разрядности чисел (`float64` $\rightarrow$ `float32`, минимальный `int`), перевода строковых столбцов в тип `category` и ручной очистки памяти (`gc` / `%reset_selective`).

###  Запуск
* Откройте нужный ноутбук в Jupyter Notebook / Jupyter Lab или VS Code: `jupyter notebook src/ex05/optimizations.ipynb`
