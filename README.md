# Предсказание вероятностей склонности к оттоку для клиентов сети розничных продуктовых магазинов

## Содержание ноутбука:

**0. Выгрузка данных**

*Выгрузка сырых данных в pandas-датафреймы, заполнение пропусков и склейка датафреймов в единый датафрейм с транзакциями, аггрегация датафрейма с транзакциями по чекам*

**1. Глубокий EDA**

*Предварительный анализ данных о чеках*

**2. Создание таргетной переменной и подготовка данных к обучению**

**3. Обучение и интерпретация моделей**

*Обучение нескольких моделей, которые имеют возможность предсказывать вероятности:*

*Логистическая регрессия с l1-регуляризацией, Random Forest, Градиентный бустинг catboost*


## Описание данных:

**`transactions.parquet` - чековые данные**

- `chq_id` - id чека
- `plant` - id магазина
- `chq_date` - дата транзакции
- `chq_position` - номер позиции товара в чеке
- `client_id` - id клиента
- `material` - id товара
- `sales_count` - кол-во товара в чеке
- `sales_sum` - стоимость указанных единиц товара в чеке
- `is_promo` - был ли товар на промо-акции

**`materials.csv` - справочник товаров**

- `material` - id товара
- `hier_level_1` - категория товара 1(еда/не еда)
- `hier_level_2` - категория товара 2(зашифрован)
- `hier_level_3` - категория товара 3(зашифрован)
- `hier_level_4` - категория товара 4(зашифрован)
- `vendor` - id производителя
- `is_private_label` - принадлежность товара к внутреннему бренду
- `is_alco` - принадлежность товара к алкогольной продукции

**`plants.csv` - справочник магазинов**

- `plant` - id магазина
- `plant_type` - тип магазина (супермаркет или гипермаркет)
- `city` - город, где расположен магазин

**`clients.csv` - справочник клиентов**

- `client_id` - id клиента
- `gender` - пол клиента
- `city` - город, где клиент совершает покупки чаще всего
- `birthyear` - год рождения клиента
