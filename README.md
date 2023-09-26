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
		id uuid primary key not null
		login text unique not null
		password text not null
		first_name text not null
		last_name text not null
		phone_nymber text ~ '+375[0-9]{9}' not null
		email text  ~ '.@.+..' not null
  
	UserHistory:
		id uuid primary key not null
		foreign key user_id references user(id) not null
		foreign key operation_id references operation(id) not null
		datetime timestamp not null
		
	Operation:
		id uuid primary key not null
		type text unique not null

	UserRole:
		id uuid primary key not null
		foreign key user_id references user(id) not null
		foreign key role_id references role(id) not null

	Role:
		id uuid primary key not null not null
		type text unique not null

 	Offer:
		id uuid primary key not null
		foreign key user_id references user(id) not null
		foreign key vehicle_id references vehicle(id) not null
		publication_date timestamp not null
		description text not null
		price decimal not null
		location text not null

 	Vehicle:
		id uuid primary key not null
		foreign key producer_id references producer(id) not null
		foreign key vehicle_type_id references vehicle_type(id) not null
		foreign key wheel_drive_type_id references wheel_drive_type(id) not null
		foreign key transmission_type_id references transmission_type(id) not null
		model text not null
		mileage decimal not null
		engine_displacement decimal not null
		horsepower int not null
		production_year date not null

	SuitableWheels:
		id uuid primary key not null
		foreign key wheel_id references wheel(id) not null
		foreign key vehicle_id references vehicle(id) not null

 	Wheel:
		id uuid primary key not null
		tread_width int not null
		profile_height int not null
		radius int not null

 	Producer:
		id uuid primary key not null
		country text
		name unique text

 	VehicleType:
		id uuid primary key not null
		type text unique not null

 	WheelDriveType:
		id uuid primary key not null
		type text unique not null

	TransmissionType:
		id uuid primary key not null
		type text unique not null
 	
	
 
