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

   






