# KPSS
# Диаграммы для проекта "Магазин игровой валюты"

## 1. Структура функциональных возможностей (Mind Map)

```mermaid
mindmap
  root((Магазин игровой валюты))
    Клиент
      Оплата
        Банковская карта
          Visa
          MasterCard
        Электронный кошелек
          PayPal
          Яндекс.Деньги
        Криптовалюта
          Bitcoin
          Ethereum
      Просмотр каталога
        Поиск
          По названию
          По категории
        Фильтр
          Цена
          Популярность
        Сортировка
          Убывающая цена
          Возрастающая цена
      Покупка
        Добавление в корзину
          Проверка доступности
        Оформить заказ
          Ввод личных данных
          Утверждение условий
      Кабинет пользователя
        История покупок
          Поиск в истории
          Повторить заказ
        Настройки
          Изменение пароля
          Настройка уведомлений
        Баланс
          Пополнение средств
          Проверка остатка
    Сервер
      Авторизация
        Регистрация
          Проверка email
          Проверка пароля
        Вход
          Обычный логин
          Логин через социальные сети
        Двухфакторная аутентификация
          Email-код
          SMS-код
      Управление контентом
        Управление складом
          Проверка доступности
          Изменение цен
      Обработка заказов
        Проверка корзины
          Проверка доступности товара
        Создание заказа
          Валидация данных
          Генерация номера заказа
        Обработка оплаты
          Проверка платёжной системы
          Обновление статуса
```


---

## 2. Диаграмма путешествия пользователя (User Journey Diagram)
```mermaid
journey
    title Путешествие пользователя в магазине игровой валюты
    section Регистрация
      Пользователь заходит на сайт: 5: Пользователь
      Пользователь заполняет форму регистрации: 4: Пользователь
      Пользователь подтверждает email или номер телефона: 4: Пользователь
      Система подтверждает успешную регистрацию: 5: Система
    section Просмотр каталога валют
      Пользователь переходит в каталог валют: 5: Пользователь
      Пользователь настраивает фильтры (валюта, игра, цена): 4: Пользователь
      Система отображает доступные валюты на основе фильтров: 5: Система
      Пользователь выбирает интересующую валюту: 4: Пользователь
      Система отображает страницу с детальной информацией о валюте: 5: Система
    section Добавление в корзину
      Пользователь добавляет выбранную валюту в корзину: 5: Пользователь
      Система проверяет доступность покупки игровой валюты: 5: Система
      Система обновляет содержимое корзины: 5: Система
      Пользователь вводит количество игровой валюты, которое он хочет купить: 4: Пользователь
    section Оформление заказа
      Пользователь переходит к оформлению заказа: 5: Пользователь
      Пользователь выбирает способ оплаты: 4: Пользователь
      Система показывает итоговую сумму и отправляет данные в платёжную систему: 5: Система
      Платёжная система обрабатывает платёж: 5: Платёжная система
      Система подтверждает успешную транзакцию: 5: Система
      Система обновляет статус заказа (оплачен): 5: Система
      Пользователь получает уведомление о выполнении заказа: 5: Пользователь
      Пользователь получает доступ к купленной валюте (код/перевод внутриигровой валюты): 5: Пользователь
```


---

## 3. Квадрант-граф (Приоритизация функций)
```mermaid
quadrantChart
    title Стоимость и время разработки функций системы
    x-axis Низкая стоимость --> Высокая стоимость
    y-axis Низкое время разработки --> Высокое время разработки
    quadrant-1 Высокая стоимость / Высокое время
    quadrant-2 Низкая стоимость / Высокое время
    quadrant-3 Высокая стоимость / Низкое время
    quadrant-4 Низкая стоимость / Низкое время
    
    Двухфакторная аутентификация: [0.8, 0.9]
    Интеграция с несколькими платёжными системами: [0.85, 0.85]
    Функционал оформления заказа: [0.75, 0.8]
    Гибкие фильтры и сортировка: [0.4, 0.75]
    Поддержка API для начисления игровой валюты: [0.5, 0.7]
    Система рекомендаций: [0.9, 0.4]
    Интеграция с системой уведомлений: [0.85, 0.35]
    Функционал избранного: [0.6, 0.5]
    Базовая функциональность корзины: [0.3, 0.3]
    Простая авторизация: [0.2, 0.25]
```

---

## 4. Гит-граф (Gitgraph)
```mermaid
gitGraph
  commit id: "Инициализация проекта"
  
  branch auth_service
  commit id: "Создание API для регистрации пользователя"
  commit id: "Двухфакторная аутентификация"
  
  checkout main
  branch catalog_service
  commit id: "Создание библиотеки поиска по названию"
  commit id: "Добавление фильтров"
  
  checkout main
  branch cart_service
  commit id: "Создание репозитория корзины"
  commit id: "Подключение сессий пользователей"
  merge auth_service
  
  checkout main
  branch order_service
  commit id: "Формирование структуры заказа"
  commit id: "Валидация данных заказа"
  merge catalog_service
  commit id: "Интеграция с фильтрами каталога"
  
  checkout main
  branch payment_service
  commit id: "Создание методов работы через Payment API"
  commit id: "Обработка успешно завершённых транзакций"
  merge cart_service
  merge order_service
  
  checkout main
  merge payment_service
  commit id: "Сборка релизной версии проекта"
```
