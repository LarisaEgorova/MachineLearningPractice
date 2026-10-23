# Определение принадлежности фильмов к категориям детский/недетский

**Задача** — бинарная классификация: по синопсису, жанрам, режиссёрам, актёрам, длительности, студии, году выхода и оценкам зрителей и критиков определить, подходит ли фильм для детей.

| Класс | Рейтинги MPAA | Фильмов | Доля |
|---|---|---|---|
| 1 — детский | G, PG | 2 844 | 23% |
| 0 — не детский | PG-13, R, NC-17 | 9 394 | 77% |

Фильмы без рейтинга (NR) исключены.

Вся работа — в ноутбуке [`kids_rating_classification.ipynb`](kids_rating_classification.ipynb): все пункты задания от описания задачи до выводов.

## Данные

[Rotten Tomatoes movies and critic reviews dataset](https://www.kaggle.com/datasets/stefanoleone992/rotten-tomatoes-movies-and-critic-reviews-dataset) (Kaggle). Файл `rotten_tomatoes_movies.csv` нужно положить в папку `data/`:

```
data/rotten_tomatoes_movies.csv
```

## Основные результаты (тестовая выборка, 3060 фильмов)

| Модель | Ошибка | Precision (детский) | Recall (детский) |
|---|---|---|---|
| Константа «всегда не детский» | 0.232 | — | 0 |
| kNN, k = 21 | 0.148 | 0.79 | 0.50 |
| Логистическая регрессия | 0.135 | 0.79 | 0.57 |
| Случайный лес | 0.140 | 0.84 | 0.49 |
| Градиентный бустинг | 0.132 | 0.80 | 0.58 |

## Запуск

```bash
pip install -r requirements.txt
jupyter notebook kids_rating_classification.ipynb
```
