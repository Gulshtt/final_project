CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(200) not NULL,
    password VARCHAR(200) not NULL,
    full_name VARCHAR(200) not null,
    role_id VARCHAR(2) not NULL
);
CREATE TABLE news_categories  (
	id SERIAL PRIMARY KEY,
	"name" varchar(255) NULL
);
CREATE TABLE news (
	id serial NOT null PRIMARY KEY,
	post_date timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
	category_id integer NOT NULL,
	title text NOT NULL,
	column1 text null,
	CONSTRAINT fk_category_id
      FOREIGN KEY(category_id) 
        REFERENCES news_categories(id)
);
CREATE TABLE "comments" (
	id serial NOT null PRIMARY KEY,
	"comment" text NOT NULL,
	post_date timestamp NOT null DEFAULT CURRENT_TIMESTAMP,
	user_id integer NOT NULL,
	news_id integer NOT null,
	CONSTRAINT fk_user_id
      FOREIGN KEY(user_id) 
        REFERENCES users(id),
    CONSTRAINT fk_news_id
      FOREIGN KEY(news_id) 
        REFERENCES news(id)
);


INSERT INTO public.users
(id, email, "password", full_name, role_id)
VALUES(11, 'admin@mail.ru', '12345', 'Admin', '2');
