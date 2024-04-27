### Домашнее задание к лекции «Работа с SQL. Создание БД»

## Задание

## Обязательная часть

Будем развивать схему для музыкального сервиса.

Ранее существовало ограничение, что каждый исполнитель поёт строго в одном жанре, пора его убрать. Исполнители могут петь в разных жанрах, как и одному жанру могут принадлежать несколько исполнителей.

Аналогичное ограничение было и с альбомами у исполнителей — альбом мог выпустить только один исполнитель. Теперь альбом могут выпустить несколько исполнителей вместе. Как и исполнитель может принимать участие во множестве альбомов.

С треками ничего не меняем, всё так же трек принадлежит строго одному альбому.

Но появилась новая сущность — сборник. Сборник имеет название и год выпуска. В него входят различные треки из разных альбомов.

Обратите внимание: один и тот же трек может присутствовать в разных сборниках.

Задание состоит из двух частей

1. Спроектировать и нарисовать схему, как в первой домашней работе. Прислать изображение со схемой.
2. Написать SQL-запросы, создающие спроектированную БД. Прислать ссылку на файл, содержащий SQL-запросы.
   
Примечание: можно прислать сначала схему, получить подтверждение, что схема верная, и после этого браться за написание запросов.

## Ответ 

![image](https://github.com/bezymel/py-homeworks-db/assets/129361495/0f2d6d16-2ac2-4477-aeaa-33a21d273c3a)


CREATE TABLE Artists (
    ID_Artists INT PRIMARY KEY,
    NAME VARCHAR(255)
);

CREATE TABLE Albums (
    ID_Albums INT PRIMARY KEY,
    NAME VARCHAR(255),
    YEAR INT
);

CREATE TABLE Collections (
    ID_Collections INT PRIMARY KEY,
    NAME VARCHAR(255),
    YEAR INT
);

CREATE TABLE Genres (
    ID_Genres INT PRIMARY KEY,
    NAME VARCHAR(255)
);

CREATE TABLE Artists_Genres (
    ID_Artists INT,
    ID_Genres INT,
    FOREIGN KEY (ID_Artists) REFERENCES Artists(ID_Artists),
    FOREIGN KEY (ID_Genres) REFERENCES Genres(ID_Genres)
);

CREATE TABLE Artists_Albums (
    ID_Artists INT,
    ID_Albums INT,
    FOREIGN KEY (ID_Artists) REFERENCES Artists(ID_Artists),
    FOREIGN KEY (ID_Albums) REFERENCES Albums(ID_Albums)
);

CREATE TABLE Tracks_Collections (
    ID_Tracks INT,
    ID_Collections INT,
    FOREIGN KEY (ID_Tracks) REFERENCES Tracks(ID_Tracks),
    FOREIGN KEY (ID_Collections) REFERENCES Collections(ID_Collections)
);

CREATE TABLE Tracks (
    ID_Tracks INT PRIMARY KEY,
    NAME VARCHAR(255),
    DURATION TIME
);
