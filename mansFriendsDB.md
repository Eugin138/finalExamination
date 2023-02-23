7. В подключенном MySQL репозитории создать базу данных “Друзья
человека”

 CREATE DATABASE MansFriends;
 
8. Создать таблицы с иерархией из диаграммы в БД
 
 USE MansFriends;

CREATE TABLE `mansfriends`.`animals` (
  `idAnimals` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `Animal_species` VARCHAR(45) NULL,
  PRIMARY KEY (`idAnimals`),
  UNIQUE INDEX `Animal_species_UNIQUE` (`Animal species` ASC) VISIBLE);

CREATE TABLE `mansfriends`.`pets` (
  `idPets` INT UNSIGNED NOT NULL,
  `Kind_of_animal` VARCHAR(45) NULL,
  PRIMARY KEY (`idPets`));

  CREATE TABLE `mansfriends`.`packs` (
  `idPacks` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `Kind_of_animal` VARCHAR(45) NULL,
  PRIMARY KEY (`idPacks`));

  CREATE TABLE `mansfriends`.`dogs` (
  `idDogs` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `Name` VARCHAR(45) NOT NULL,
  `Birthday` DATE NOT NULL,
  `Action` INT NOT NULL,
  PRIMARY KEY (`idDogs`));

  CREATE TABLE `mansfriends`.`cats` (
  `idCats` INT NOT NULL,
  `Name` VARCHAR(45) NOT NULL,
  `Birthday` DATE NOT NULL,
  `Action` INT NOT NULL,
  PRIMARY KEY (`idCats`));

  CREATE TABLE `mansfriends`.`hamsters` (
  `idHamsters` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `Name` VARCHAR(45) NOT NULL,
  `Birthday` DATE NOT NULL,
  `Action` INT NOT NULL,
  PRIMARY KEY (`idHamsters`));

  CREATE TABLE `mansfriends`.`horses` (
  `idHorses` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `Name` VARCHAR(45) NOT NULL,
  `Birthday` DATE NOT NULL,
  `Action` INT NOT NULL,
  PRIMARY KEY (`idHorses`));

  CREATE TABLE `mansfriends`.`donkeys` (
  `idDonkeys` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `Name` VARCHAR(45) NOT NULL,
  `Birthday` DATE NOT NULL,
  `Action` INT NOT NULL,
  PRIMARY KEY (`idDonkeys`));

  CREATE TABLE `mansfriends`.`camels` (
  `idCamels` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `Name` VARCHAR(45) NOT NULL,
  `Birthday` DATE NOT NULL,
  `Action` INT NOT NULL,
  PRIMARY KEY (`idCamels`));

  CREATE TABLE `mansfriends`.`action` (
  `idAction` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `Action` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`idAction`));


9. Заполнить низкоуровневые таблицы именами(животных), командами
которые они выполняют и датами рождения


  insert into action (idAction, Action) values (1, 'paw'), (2, 'mew'), (3, 'squeak'), (4, 'gallop'), (5, 'transporting_cargo');

  insert into animals (idAnimals, Animal_species) values (1, 'Pets'), (2, 'Packs');

  insert into packs (idPacks, Kind_of_animal) values (1, 'Horses'), (2, 'Donkeys'), (3, 'Camels');

  insert into pets (idPets, Kind_of_animal) values (1, 'Dogs'), (2, 'Cats'), (3, 'Hamsters');

  ALTER TABLE `mansfriends`.`horses` 
ADD COLUMN `Animals_species` INT NOT NULL AFTER `Action`;

ALTER TABLE `mansfriends`.`camels` 
ADD COLUMN `Animal_species` INT NOT NULL AFTER `Action`;

ALTER TABLE `mansfriends`.`cats` 
ADD COLUMN `Animal_species` INT NOT NULL AFTER `Action`;

ALTER TABLE `mansfriends`.`dogs` 
ADD COLUMN `Animal_species` INT NOT NULL AFTER `Action`;

ALTER TABLE `mansfriends`.`donkeys` 
ADD COLUMN `Animal_species` INT NOT NULL AFTER `Action`;

ALTER TABLE `mansfriends`.`hamsters` 
ADD COLUMN `Animal_species` INT NOT NULL AFTER `Action`;

insert into Camels (idCamels, Name, Birthday, Action, Animal_species) value (1, 'Camel1', '2018-12-12', 5, 2),  (2, 'Camel2', '2019-12-12', 5, 2), (3, 'Camel3', '2020-12-12', 5, 2);

insert into Cats (idCats, Name, Birthday, Action, Animal_species) value (1, 'Cat1', '2018-12-12', 2, 1),  (2, 'Cat2', '2019-12-12', 2, 1), (3, 'Cat3', '2020-12-12', 2, 1);

insert into Dogs (idDogs, Name, Birthday, Action, Animal_species) value (1, 'Dog1', '2018-12-12', 1, 1),  (2, 'Dog2', '2019-12-12', 1, 1), (3, 'Dog3', '2020-12-12', 1, 1);

insert into Donkeys (idDonkeys, Name, Birthday, Action, Animal_species) value (1, 'Donkey1', '2018-12-12', 5, 2),  (2, 'Donkey2', '2019-12-12', 5, 2), (3, 'Donkey3', '2020-12-12', 5, 2);

insert into Hamsters (idHamsters, Name, Birthday, Action, Animal_species) value (1, 'Hamster1', '2018-12-12', 3, 1),  (2, 'Hamster2', '2019-12-12', 3, 1), (3, 'Hamster3', '2020-12-12', 3, 1);

ALTER TABLE `mansfriends`.`horses` 
CHANGE COLUMN `Animals_species` `Animal_species` INT NOT NULL ;

insert into Horses (idHorses, Name, Birthday, Action, Animal_species) value (1, 'Horse1', '2018-12-12', 4, 2),  (2, 'Horse2', '2019-12-12', 4, 2), (3, 'Horse3', '2020-12-12', 4, 2);

ALTER TABLE `mansfriends`.`camels` 
ADD CONSTRAINT `Act`
  FOREIGN KEY (`Action`)
  REFERENCES `mansfriends`.`action` (`idAction`)
  ON DELETE NO ACTION
  ON UPDATE NO ACTION;

select * from cats;
+--------+------+------------+--------+----------------+
| idCats | Name | Birthday   | Action | Animal_species |
+--------+------+------------+--------+----------------+
|      1 | Cat1 | 2018-12-12 |      2 |              1 |
|      2 | Cat2 | 2019-12-12 |      2 |              1 |
|      3 | Cat3 | 2020-12-12 |      2 |              1 |
+--------+------+------------+--------+----------------+
select * from camels;
+----------+--------+------------+--------+----------------+
| idCamels | Name   | Birthday   | Action | Animal_species |
+----------+--------+------------+--------+----------------+
|        1 | Camel1 | 2018-12-12 |      5 |              2 |
|        2 | Camel2 | 2019-12-12 |      5 |              2 |
|        3 | Camel3 | 2020-12-12 |      5 |              2 |
+----------+--------+------------+--------+----------------+
select * from Dogs;
+--------+------+------------+--------+----------------+
| idDogs | Name | Birthday   | Action | Animal_species |
+--------+------+------------+--------+----------------+
|      1 | Dog1 | 2018-12-12 |      1 |              1 |
|      2 | Dog2 | 2019-12-12 |      1 |              1 |
|      3 | Dog3 | 2020-12-12 |      1 |              1 |
+--------+------+------------+--------+----------------+
select * from Donkeys;
+-----------+---------+------------+--------+----------------+
| idDonkeys | Name    | Birthday   | Action | Animal_species |
+-----------+---------+------------+--------+----------------+
|         1 | Donkey1 | 2018-12-12 |      5 |              2 |
|         2 | Donkey2 | 2019-12-12 |      5 |              2 |
|         3 | Donkey3 | 2020-12-12 |      5 |              2 |
+-----------+---------+------------+--------+----------------+
select * from Hamsters;
+------------+----------+------------+--------+----------------+
| idHamsters | Name     | Birthday   | Action | Animal_species |
+------------+----------+------------+--------+----------------+
|          1 | Hamster1 | 2018-12-12 |      3 |              1 |
|          2 | Hamster2 | 2019-12-12 |      3 |              1 |
|          3 | Hamster3 | 2020-12-12 |      3 |              1 |
+------------+----------+------------+--------+----------------+
select * from Horses;
+----------+--------+------------+--------+----------------+
| idHorses | Name   | Birthday   | Action | Animal_species |
+----------+--------+------------+--------+----------------+
|        1 | Horse1 | 2018-12-12 |      4 |              2 |
|        2 | Horse2 | 2019-12-12 |      4 |              2 |
|        3 | Horse3 | 2020-12-12 |      4 |              2 |
+----------+--------+------------+--------+----------------+
select * from Animals;
+-----------+----------------+
| idAnimals | Animal_species |
+-----------+----------------+
|         2 | Packs          |
|         1 | Pets           |
+-----------+----------------+
select * from Action;
+----------+--------------------+
| idAction | Action             |
+----------+--------------------+
|        1 | paw                |
|        2 | mew                |
|        3 | squeak             |
|        4 | gallop             |
|        5 | transporting_cargo |
+----------+--------------------+
select * from Packs;
+---------+----------------+
| idPacks | Kind_of_animal |
+---------+----------------+
|       1 | Horses         |
|       2 | Donkeys        |
|       3 | Camels         |
+---------+----------------+
select * from Pets;
+--------+----------------+
| idPets | Kind_of_animal |
+--------+----------------+
|      1 | Dogs           |
|      2 | Cats           |
|      3 | Hamsters       |
+--------+----------------+
select idCats as id, Name, Birthday, Action, Animal_species from Cats union select * from camels union select * from Dogs union select * from Donkeys union select * from Hamsters union select * from Horses;
+----+----------+------------+--------+----------------+
| id | Name     | Birthday   | Action | Animal_species |
+----+----------+------------+--------+----------------+
|  1 | Cat1     | 2018-12-12 |      2 |              1 |
|  2 | Cat2     | 2019-12-12 |      2 |              1 |
|  3 | Cat3     | 2020-12-12 |      2 |              1 |
|  1 | Camel1   | 2018-12-12 |      5 |              2 |
|  2 | Camel2   | 2019-12-12 |      5 |              2 |
|  3 | Camel3   | 2020-12-12 |      5 |              2 |
|  1 | Dog1     | 2018-12-12 |      1 |              1 |
|  2 | Dog2     | 2019-12-12 |      1 |              1 |
|  3 | Dog3     | 2020-12-12 |      1 |              1 |
|  1 | Donkey1  | 2018-12-12 |      5 |              2 |
|  2 | Donkey2  | 2019-12-12 |      5 |              2 |
|  3 | Donkey3  | 2020-12-12 |      5 |              2 |
|  1 | Hamster1 | 2018-12-12 |      3 |              1 |
|  2 | Hamster2 | 2019-12-12 |      3 |              1 |
|  3 | Hamster3 | 2020-12-12 |      3 |              1 |
|  1 | Horse1   | 2018-12-12 |      4 |              2 |
|  2 | Horse2   | 2019-12-12 |      4 |              2 |
|  3 | Horse3   | 2020-12-12 |      4 |              2 |
+----+----------+------------+--------+----------------+


10. Удалив из таблицы верблюдов, т.к. верблюдов решили перевезти в другой
питомник на зимовку. Объединить таблицы лошади, и ослы в одну таблицу.

select idCats as id, Name, Birthday, Action, Animal_species from Cats union select * from Dogs union select * from Donkeys union select * from Hamsters union select * from Horses;
+----+----------+------------+--------+----------------+
| id | Name     | Birthday   | Action | Animal_species |
+----+----------+------------+--------+----------------+
|  1 | Cat1     | 2018-12-12 |      2 |              1 |
|  2 | Cat2     | 2019-12-12 |      2 |              1 |
|  3 | Cat3     | 2020-12-12 |      2 |              1 |
|  1 | Dog1     | 2018-12-12 |      1 |              1 |
|  2 | Dog2     | 2019-12-12 |      1 |              1 |
|  3 | Dog3     | 2020-12-12 |      1 |              1 |
|  1 | Donkey1  | 2018-12-12 |      5 |              2 |
|  2 | Donkey2  | 2019-12-12 |      5 |              2 |
|  3 | Donkey3  | 2020-12-12 |      5 |              2 |
|  1 | Hamster1 | 2018-12-12 |      3 |              1 |
|  2 | Hamster2 | 2019-12-12 |      3 |              1 |
|  3 | Hamster3 | 2020-12-12 |      3 |              1 |
|  1 | Horse1   | 2018-12-12 |      4 |              2 |
|  2 | Horse2   | 2019-12-12 |      4 |              2 |
|  3 | Horse3   | 2020-12-12 |      4 |              2 |
+----+----------+------------+--------+----------------+

select idDonkeys as id, Name, Birthday, Action, Animal_species from Donkeys union select * from Horses;
+----+---------+------------+--------+----------------+
| id | Name    | Birthday   | Action | Animal_species |
+----+---------+------------+--------+----------------+
|  1 | Donkey1 | 2018-12-12 |      5 |              2 |
|  2 | Donkey2 | 2019-12-12 |      5 |              2 |
|  3 | Donkey3 | 2020-12-12 |      5 |              2 |
|  1 | Horse1  | 2018-12-12 |      4 |              2 |
|  2 | Horse2  | 2019-12-12 |      4 |              2 |
|  3 | Horse3  | 2020-12-12 |      4 |              2 |
+----+---------+------------+--------+----------------+

11. Создать новую таблицу “молодые животные” в которую попадут все
животные старше 1 года, но младше 3 лет и в отдельном столбце с точностью
до месяца подсчитать возраст животных в новой таблице.

select idCats as id, Name, Birthday, Action, Animal_species, (TIMESTAMPDIFF(month, Birthday, curdate())) as Age from (select * from Cats union select * from Dogs union select * from Donkeys union select * from Hamsters union select * from Horses) as YoungAnimals where datediff(curdate(), birthday) > 365 and datediff(curdate(), birthday) < 1095;

+----+----------+------------+--------+----------------+------+
| id | Name     | Birthday   | Action | Animal_species | Age  |
+----+----------+------------+--------+----------------+------+
|  3 | Cat3     | 2020-12-12 |      2 |              1 |   26 |
|  3 | Dog3     | 2020-12-12 |      1 |              1 |   26 |
|  3 | Donkey3  | 2020-12-12 |      5 |              2 |   26 |
|  3 | Hamster3 | 2020-12-12 |      3 |              1 |   26 |
|  3 | Horse3   | 2020-12-12 |      4 |              2 |   26 |
+----+----------+------------+--------+----------------+------+


12. Объединить все таблицы в одну, при этом сохраняя поля, указывающие на
прошлую принадлежность к старым таблицам

select * from (select idCats as id, Name, Birthday, Action, Animal_species, 'Cats' as tablename from Cats union all select idDogs, Name, Birthday, Action, Animal_species, 'Dogs' as tablename from Dogs union all select idDonkeys, Name, Birthday, Action, Animal_species, 'Donkeys' as tablename from Donkeys union all select idHamsters, Name, Birthday, Action, Animal_species, 'Hamsters' as tablename from Hamsters union all select idHorses, Name, Birthday, Action, Animal_species, 'Horses' as tablename from Horses) as full;

+----+----------+------------+--------+----------------+-----------+
| id | Name     | Birthday   | Action | Animal_species | tablename |
+----+----------+------------+--------+----------------+-----------+
|  1 | Cat1     | 2018-12-12 |      2 |              1 | Cats      |
|  2 | Cat2     | 2019-12-12 |      2 |              1 | Cats      |
|  3 | Cat3     | 2020-12-12 |      2 |              1 | Cats      |
|  1 | Dog1     | 2018-12-12 |      1 |              1 | Dogs      |
|  2 | Dog2     | 2019-12-12 |      1 |              1 | Dogs      |
|  3 | Dog3     | 2020-12-12 |      1 |              1 | Dogs      |
|  1 | Donkey1  | 2018-12-12 |      5 |              2 | Donkeys   |
|  2 | Donkey2  | 2019-12-12 |      5 |              2 | Donkeys   |
|  3 | Donkey3  | 2020-12-12 |      5 |              2 | Donkeys   |
|  1 | Hamster1 | 2018-12-12 |      3 |              1 | Hamsters  |
|  2 | Hamster2 | 2019-12-12 |      3 |              1 | Hamsters  |
|  3 | Hamster3 | 2020-12-12 |      3 |              1 | Hamsters  |
|  1 | Horse1   | 2018-12-12 |      4 |              2 | Horses    |
|  2 | Horse2   | 2019-12-12 |      4 |              2 | Horses    |
|  3 | Horse3   | 2020-12-12 |      4 |              2 | Horses    |
+----+----------+------------+--------+----------------+-----------+