1. Используя команду cat в терминале операционной системы Linux, создать
два файла Домашние животные (заполнив файл собаками, кошками,
хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и
ослы), а затем объединить их. Просмотреть содержимое созданного файла.
Переименовать файл, дав ему новое имя (Друзья человека).

suita@suita-VirtualBox:~$ cat > "Домашние животные" 
Собаки
Кошки
Хомяки

cat > "Вьючные животные" 
Лошади
Верблюды
Ослы

suita@suita-VirtualBox:~$ cat "Домашние животные" "Вьючные животные" > "Друзья человека"
suita@suita-VirtualBox:~$ cat "Друзья человека"
Собаки
Кошки
Хомяки
Лошади
Верблюды
Ослы
suita@suita-VirtualBox:~$ mv "Друзья человека" "Любимцы"

2. Создать директорию, переместить файл туда.

suita@suita-VirtualBox:~$ mkdir животные
suita@suita-VirtualBox:~$ mv Друзья_человека животные/

3. Подключить дополнительный репозиторий MySQL. Установить любой пакет
из этого репозитория

suita@suita-VirtualBox:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5072E1F5
sudo add-apt-repository 'deb http://repo.mysql.com/apt/debian/ buster mysql-8.0'
suita@suita-VirtualBox:~$ sudo apt update
suita@suita-VirtualBox:~$ sudo apt install mysql-server

4. Установить и удалить deb-пакет с помощью dpkg.

suita@suita-VirtualBox:~$ sudo dpkg -i"C:\Users\saida\Downloads\vivaldi-stable_5.5.2805.48-1_amd64.deb" 
suita@suita-VirtualBox:~$ sudo dpkg -r vivaldi-stable_3.8.2259.42-1_amd64.deb

5. Выложить историю команд в терминале ubuntu

405  bash
406  cat > "Домашние животные"
  407  cat > "Домашние животные" << EOF
Собаки
Кошки
Хомяки
  408  cat > "Вьючные животные" << EOF
Лошади
Верблюды
Ослы
  409  cat "Домашние животные" "Вьючные животные" > "Друзья человека"
  410  cat "Друзья человека"
  411  mv "Друзья человека" "Любимцы"
  412  mkdir Животные
  413  mv "Любимцы" Животные/
  414  sudo mkdir Животные
  415  ls
  416  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5072E1F5
  417  sudo add-apt-repository 'deb http://repo.mysql.com/apt/debian/ buster mysql-8.0'
  418  sudo apt update
  419  sudo apt install mysql-server
  420  sudo dpkg -i package_name.deb
  421  sudo dpkg -r package_name
  422  sudo dpkg -P package_name
  423  sudo dpkg -r mysql-server-8.0
  424  history
  425  history > command_history.txt
  426  CREATE DATABASE Друзья_человека;
  427  sudo dpkg -i путь_к_файлу.deb  # Установка пакета
  428  suita@suita-VirtualBox:~$ sudo dpkg -i .deb  # Установка пакета
  429  dpkg -s firefox.
  430  apt search gimp
  431  sudo apt install gimp
  432  cd ~/Загрузки/
  433  sudo dpkg -i vivaldi-stable_3.8.2259.42-1_amd64.deb
  434  apt download vivaldi
  435  apt download vivaldi.deb
  436  sudo dpkg -i"C:\Users\saida\Downloads\vivaldi-stable_5.5.2805.48-1_amd64.deb" .deb  # Установка пакета
  437  sudo dpkg -r "C:\Users\saida\Downloads\vivaldi-stable_5.5.2805.48-1_amd64.deb"    # Удаление пакета
  438  sudo dpkg -i "C:\Users\saida\Downloads\vivaldi-stable_5.5.2805.48-1_amd64.deb"
  439  cd ~/Загрузки/
  440  sudo dpkg -i vivaldi-stable_3.8.2259.42-1_amd64.deb
  441  mkdir животные
  442  mv Друзья_человека животные/
  443  sudo dpkg -r mysql-server-8.0
  444  sudo dpkg -i mysql-server-8.0
  445  history


7. В подключенном MySQL репозитории создать базу данных “Друзья
человека”
sql
CREATE DATABASE Друзья человека;
USE Друзья человека;

8. Создать таблицы с иерархией из диаграммы в БД

sql
CREATE TABLE Родительский (
    id INT PRIMARY KEY,
    имя VARCHAR(50),
    возраст INT,
    тип VARCHAR(50)
);

CREATE TABLE Домашние_животные (
    id INT PRIMARY KEY,
    имя VARCHAR(50),
    команды VARCHAR(100),
    дата_рождения DATE,
    FOREIGN KEY (id) REFERENCES Родительский(id)
);

CREATE TABLE Вьючные_животные (
    id INT PRIMARY KEY,
    имя VARCHAR(50),
    команды VARCHAR(100),
    дата_рождения DATE,
    FOREIGN KEY (id) REFERENCES Родительский(id)
);


  
 




 






