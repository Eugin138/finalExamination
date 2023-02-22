1. Используя команду cat в терминале операционной системы Linux, создать
два файла Домашние животные (заполнив файл собаками, кошками,
хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и
ослы), а затем объединить их. Просмотреть содержимое созданного файла.
Переименовать файл, дав ему новое имя (Друзья человека).

cat > pets.txt

git init

git commit -m "Create pets.txt file"

git remote add origin https://github.com/Eugin138/finalExamination.git

push origin linux1

git checkout -b linux2

cat > pack.txt

git add pets.txt

git commit -m "Create pets.txt file"

git push origin linux2

git pull origin linux1

git checkout -b linux3

cat pets.txt pack.txt > animals.txt

git add animals.txt

git commit -m "Concatinated pack.txt and pets.txt into animals.txt"

git push origin linux3

git pull origin linux1

git cat animals.txt

mv animals.txt mansFriends.txt

git add mansFriends.txt

git commit -m "animals.txt renamed into mansFriends.txt"

git push origin linux3


2. Создать директорию, переместить файл туда

mkdir task3.

mv mansFriends.txt /home/user1/finalExamination/task3/

git commit -m "Create the task3 directory and move mansFriends.txt there"

git push origin linux3

git pull origin linux1

3. Подключить дополнительный репозиторий MySQL. Установить любой пакет
из этого репозитория.

wget https://dev.mysql.com/get/mysql-apt-config_0.8.24-1_all.deb

sudo dpkg -i mysql-apt-config_0.8.24-1_all.deb

sudo apt-get update

sudo apt-get install mysql-server

4. Установить и удалить deb-пакет с помощью dpkg.

apt download cowsay

sudo dpkg -i cowsay_3.03+dfsg2-8_all.deb

sudo apt install -f
