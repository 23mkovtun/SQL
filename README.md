create table if not exists genre (
	id serial primary key,
	genre_name varchar(50) not null unique
);

create table if not exists performer (
	id serial primary key,
	performer_name varchar(50) not null	
);

create table if not exists album (
	id serial primary key,
	album_name varchar(100) not null,
	year_of_release integer not null
);

create table if not exists track (
	id serial primary key,
	track_name varchar(100) not null unique,
	duration integer not null,
	album_id integer references album(id)
);

create table if not exists collection (
    id serial primary key,
    collection_name varchar(100) not null unique,
    year_of_release integer not null
);

create table if not exists genre_performer (
    genre_id integer references genre(id),
    performer_id integer references performer(id),
    constraint genre_performer_pk primary key (genre_id, performer_id)
);

create table if not exists performer_album (
    performer_id integer references performer(id),
    album_id integer references album(id),
    constraint performer_album_pk primary key (performer_id, album_id)
);


create table if not exists collection_track (
    collection_id integer references collection(id),
    track_id integer references track(id),
    constraint collection_track_pk primary key (collection_id, track_id)
);
