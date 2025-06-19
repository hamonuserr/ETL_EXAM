# ETL_EXAM
Этапы проекта:
1. Установка Yandex CLI, YDB CLI, настройка авторизации, создание ydb, перенос данных в s3.
2.
3.
4.
## TASK_01:
- Выполнена установка Yandex CLI + YDB CLI (version 2.19, 2.20+ is not working)
- Настроена авторизация через oauth-token + iam-token для подключения к YDB
- Создана БД ydb-spot-you(для прошлого битого датасета :disappointed_relieved::disappointed_relieved::disappointed_relieved:)
- Написан SQL-скрипт для создания таблицы:
```
create table transactions_v2 (
  msno Utf8,
  payment_method_id Int32,
  payment_plan_days Int32,
  plan_list_price Int32,
  actual_amount_paid Int32,
  is_auto_renew Int8,
  transaction_date Utf8,
  membership_expire_date Utf8,
  is_cancel Int8,
  PRIMARY KEY (msno);
```
(Стоит отметить, что выбор msno primary key нецелесообразен, так как при потенциальном использовании таблицы для присодинения к другим по этому ключу будут вызваны задержки в работе JOIN-ов)

- Использована утилита Yandex Data Transfer для переноса таблицы в s3 storage:
![Скриншот](task_01/ydt_work.png)
