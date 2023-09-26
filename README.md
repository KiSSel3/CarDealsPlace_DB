#1.Инфо:
Киселёв Андрей Вадимович
гр. 153501
Площадка для продажи транспортных средств
PostgreSQL

#2.Функциональные требования:
1.Авторизация пользователя
2.Управление пользователями (CRUD)
3.Система ролей
4.Журналирование действий пользователя
5.Создание объявлений(CRUD)
6.Администрирование объявлений

#3 Сущности
  User
    id uuid
    login text
    password text
    first_name text
    last_name text
    phone_nymber text
    email text
  
  UserHistory
    id uuid
    foreign key user_id references user(id)
    foreign key operation_id references operation(id)
    datetime timestamp

  Operation
