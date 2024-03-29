Тестовое задание

Задание
- Создайте веб-приложение, с API интерфейсом и админ-панелью.
- Создайте базу данных используя миграции Django.
  
Требования к реализации:
- Необходимо реализовать модель сети по продаже электроники.
  
Сеть должна представлять собой иерархическую структуру из 3 уровней:
- Завод
- Розничная сеть
- Индивидуальный предприниматель.

Каждое звено сети ссылается только на одного поставщика оборудования (не обязательно предыдущего по иерархии). Важно отметить, что уровень иерархии определяется не названием звена, а отношением к остальным элементам сети, т.е. завод всегда находится на 0 уровне, а если розничная сеть относится напрямую к заводу, минуя остальные звенья - её уровень - 1.

В ходе работы было реализовано три модели: 
- Supplier (Поставщик)
- Product (Продукт)
- NetworkLink. (Сетевая связь)
  
Сделан вывод в админ-панели созданных объектов

На странице объекта NetworkLink в панели администрирования присутствует:
- ссылка на «Поставщика»;
- фильтр по названию города;
- «admin action», очищающий задолженность перед поставщиком у выбранных объектов.

Используя DRF, был создан набор представлений:
- CRUD для модели поставщика 
- CRUD для модели продуктов
- CRUD для модели NetworkLink
  - запрещено обновление через API поля «Задолженность перед поставщиком»
  - Добавлена возможность фильтрации объектов по определенной стране.

В проекте реализована авторизация с использованием JSON Web Token, с помощью библиотеки djangorestframework-simplejwt. Доступ к API ограничивается при помощи стандартного класса разрешений IsAuthenticated.

Также реализована автоматически сгенерированная документация на основе сериализаторов при помощи drf-yasg.
