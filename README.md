# 1. Инфо:
Киселёв Андрей Вадимович
гр. 153501
Площадка для продажи транспортных средств
PostgreSQL

# 2. Функциональные требования:
1. Авторизация пользователя
2. Управление пользователями (CRUD)
3. Система ролей
4. Журналирование действий пользователя
5. Создание объявлений(CRUD)
6. Администрирование объявлений

# 3. Сущности
	User:
		id uuid
		login text
		password text
		first_name text
		last_name text
		phone_nymber text
		email text
  
	UserHistory:
		id uuid
		foreign key user_id references user(id)
		foreign key operation_id references operation(id)
		datetime timestamp
		
	Operation:
		id uuid
		type text

	UserRole:
		id uuid
		foreign key user_id references user(id)
		foreign key role_id references role(id)

	Role:
		id uuid
		type text

 	Offer:
		id uuid
		foreign key user_id references user(id)
		foreign key vehicle_id references vehicle(id)
		publication_date timestamp
		description text
		price decimal
		location text

 	Vehicle:
		id uuid
		foreign key producer_id references producer(id)
		foreign key vehicle_type_id references vehicle_type(id)
		foreign key wheel_drive_type_id references wheel_drive_type(id)
		foreign key transmission_type_id references transmission_type(id)
		model text
		mileage decimal
		engine_displacement decimal
		horsepower int
		production_year date

	SuitableWheels:
 		id uuid
		foreign key wheel_id references wheel(id)
		foreign key vehicle_id references vehicle(id)

 	Wheel:
		id uuid
		tread_width int
		profile_height int
		radius int

 	Producer:
		id uuid
		country text
		name text

 	VehicleType:
		id uuid
		type text

 	WheelDriveType:
		id uuid
		type text

	TransmissionType:
		id uuid
		type text
 	
	
 
