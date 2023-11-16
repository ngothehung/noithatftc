
CREATE TABLE users
(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    name varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL,
	email varchar(255) NOT NULL,
	username varchar(255) NOT NULL,
	password varchar(255) NOT NULL,
	phone VARCHAR(255) DEFAULT NULL,
	avatar varchar(255) NULL DEFAULT NULL,
	gender VARCHAR(255) DEFAULT null,
	type INT NOT NULL, 
	status INT(2) NOT NULL,
	address VARCHAR(255) DEFAULT NULL,
    birthday timestamp NULL DEFAULT NULL,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);

CREATE TABLE permissions
(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    name varchar(255) NULL DEFAULT NULL,
	guard_name varchar(255) NULL DEFAULT NULL,
	group_name varchar(255) NULL DEFAULT NULL,
	description varchar(255) NULL DEFAULT NULL,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);

CREATE TABLE roles
(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    name varchar(255) NULL DEFAULT NULL,
	guard_name varchar(255) NULL DEFAULT NULL,
	description varchar(255) NULL DEFAULT NULL,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);

CREATE TABLE role_has_permissions
(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    
	role_id INT DEFAULT 0 ,
	permission_id INT DEFAULT 0,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);

CREATE TABLE user_roles
(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
	role_id INT DEFAULT 0,
	user_id INT DEFAULT 0,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);


CREATE TABLE categories
(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    name varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL,
	description varchar(255) NULL DEFAULT NULL,
	avatar varchar(255) NULL DEFAULT NULL,
	slug varchar(255) NOT NULL,
	status INT(2) DEFAULT 0,
	hot INT DEFAULT 0,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);

CREATE TABLE orders
(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    user_id INT NOT NULL DEFAULT 0,
	total_discount float(8) DEFAULT 0,
	total_price float(8) DEFAULT 0,
	note varchar(255)  NULL DEFAULT NULL,
	order_type INT(2) DEFAULT 0,
	status INT(2) DEFAULT 0,
	receiver_name varchar(255) NOT NULL,
	receiver_email VARCHAR(255) NOT NULL,
	receiver_phone VARCHAR(255) NOT NULL,
	receiver_address VARCHAR(255) DEFAULT null,
	type INT  DEFAULT 0, 
	shipping_status INT(2)  DEFAULT 0,
	payment_status INT(2)  DEFAULT 0,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);

CREATE TABLE transactions
(
   	id INT UNSIGNED NOT NULL AUTO_INCREMENT,
   	order_id INT DEFAULT 0,
	product_id INT DEFAULT 0,
    name varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL,
	avatar varchar(255) NOT NULL,
	price float(8) DEFAULT 0,
	discount INT DEFAULT 0,
	quantity INT NOT NULL DEFAULT 0,
	total_price float(8) DEFAULT 0, 
	status INT(2) DEFAULT 0,
	user_id INT DEFAULT 0,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);

CREATE TABLE products
(
   id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    name varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL,
	slug varchar(255) NOT NULL,
	description varchar(255) NULL DEFAULT NULL,
	avatar varchar(255) NOT NULL,
	price float(8) DEFAULT 0,
	sale INT DEFAULT 0,
	number INT DEFAULT 0, 
	category_id INT DEFAULT 0,
	user_id INT DEFAULT 0,
	status INT(2) DEFAULT 0,
	content TEXT NULL DEFAULT NULL,
	total_reviews INT DEFAULT 0,
	total_stars INT DEFAULT 0,
	options json NULL DEFAULT NULL,
	hot INT(2) DEFAULT 0,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);

CREATE TABLE products_images
(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    name varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL,
	path varchar(255) NULL DEFAULT NULL,
	product_id INT(2) DEFAULT 0,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);


CREATE TABLE slides
(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    avatar varchar(255) NULL DEFAULT NULL,
	link varchar(255) NULL DEFAULT NULL,
	name varchar(255) NULL DEFAULT NULL, 
	status INT(2) DEFAULT 0,
	hot INT(2) DEFAULT 0,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);

CREATE TABLE votes
(
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    content varchar(255) NULL DEFAULT NULL,
	number INT(2) DEFAULT 0,
	user_id INT DEFAULT 0,
	product_id INT DEFAULT 0,
    created_at timestamp NULL DEFAULT NULL,
    updated_at timestamp NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
);

