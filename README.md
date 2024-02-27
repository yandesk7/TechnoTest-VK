# 🚀 TechnoTest-VK: Синтаксис SQL и База данных

## 📚 Введение

В данном проекте мы рассмотрим модуль  7, который включает в себя работу с SQL и базой данных. Основное внимание будет уделено двум основным таблицам: `orders` и `products`.

## 📂 Таблицы

### 📝 Таблица `products`

- `product_id`: Уникальный идентификатор продукта (первичный ключ).
- `product_name`: Название продукта.

### 📝 Таблица `orders`

- `order_id`: Уникальный идентификатор заказа (первичный ключ).
- `product_id`: Идентификатор продукта, связанный с заказом (внешний ключ, ссылается на `product_id` в таблице `products`).
- `quantity`: Количество заказанного продукта.

## 🔗 Связь между таблицами

Связь между таблицами `orders` и `products` реализована через поле `product_id`, которое является внешним ключом в таблице `orders` и ссылается на поле `product_id` в таблице `products`. Это позволяет связывать информацию о заказах с соответствующими продуктами.

## 🎯 Задача 1

Найти продукт с наибольшим количеством заказов.

## 📝 Запрос SQL

SELECT products.product_name,
       SUM (quantity),
       orders.product_id
  FROM orders
  JOIN products ON orders.product_id = products.product_id
GROUP BY orders.product_id
order BY SUM (quantity) DESC
LIMIT 1


## 🎯 Задача 2

Общая выручка с точностью до  1 знака перед запятой.

## 📝 Запрос SQL

SELECT ROUND(SUM(price * quantity),  1)  AS total_revenue
  FROM orders
  JOIN products ON orders.product_id = products.product_id;

