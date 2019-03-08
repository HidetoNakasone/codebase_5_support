
・前準備に、ターミナルを開いて以下のコードを貼り付け

mysql -u root

create database modoki;
use modoki;

create table users (id int(10) auto_increment, name varchar(20), pass varchar(20), profile varchar(100), icon_img_path varchar(50) , primary key(id));

create table posts (id int(10) auto_increment, creater_id int(10), img_path varchar(50), msg varchar(200), created_at timestamp not null default current_timestamp, updated_at timestamp not null default current_timestamp on update current_timestamp, primary key(id));

create table follows (id int(10) auto_increment, from_user_id int(10), to_user_id int(10), primary key(id));

create table likes (id int(10) auto_increment, from_user_id int(10), to_post_id int(10), primary key(id));

create view view_sub as select p.id, p.creater_id, u.name, p.img_path, p.msg, p.created_at, p.updated_at from posts p left outer join users u on p.creater_id = u.id;
