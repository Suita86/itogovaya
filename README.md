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

9. Заполнить низкоуровневые таблицы именами(животных), командами
которые они выполняют и датами рождения

sql
INSERT INTO Домашние_животные (id, имя, команды, дата_рождения) VALUES (1, 'Собака', 'Сидеть, Лежать', '2018-05-12');
INSERT INTO Домашние_животные (id, имя, команды, дата_рождения) VALUES (2, 'Кошка', 'Мяукать, Прыгать', '2017-10-25');
INSERT INTO Домашние_животные (id, имя, команды, дата_рождения) VALUES (3, 'Хомяк', 'Крутиться в колесе', '2019-02-03');

INSERT INTO Вьючные_животные (id, имя, команды, дата_рождения) VALUES (4, 'Лошадь', 'Тянуть повозку', '2015-07-19');
INSERT INTO Вьючные_животные (id, имя, команды, дата_рождения) VALUES (5, 'Верблюд', 'Переносить груз', '2016-11-30');
INSERT INTO Вьючные_животные (id, имя, команды, дата_рождения) VALUES (6, 'Осел', 'Нести груз', '2017-04-12');

10. Удалив из таблицы верблюдов, т.к. верблюдов решили перевезти в другой
питомник на зимовку. Объединить таблицы лошади, и ослы в одну таблицу.

sql
DELETE FROM Вьючные_животные WHERE имя = 'Верблюд';
CREATE TABLE Лошади_Ослы AS SELECT * FROM Вьючные_животные WHERE имя = 'Лошадь' OR имя = 'Осел';


11.Создать новую таблицу “молодые животные” в которую попадут все
животные старше 1 года, но младше 3 лет и в отдельном столбце с точностью
до месяца подсчитать возраст животных в новой таблице

sql
CREATE TABLE Молодые_животные AS 
SELECT * FROM Родительский 
WHERE возраст > 1 AND возраст < 3;

12. Объединить все таблицы в одну, при этом сохраняя поля, указывающие на
прошлую принадлежность к старым таблицам.

sql
CREATE TABLE Общие_животные AS 
SELECT * FROM Родительский 
UNION ALL 
SELECT * FROM Домашние_животные 
UNION ALL 
SELECT * FROM Вьючные_животные 
UNION ALL 
SELECT * FROM Лошади_Ослы 
UNION ALL 
SELECT * FROM Молодые_животные;

13.Создать класс с Инкапсуляцией методов и наследованием по диаграмме.

java

public class Животное \{
    private String имя;
    private int возраст;

    public Животное\(String имя, int возраст\) \{
        this\.имя \= имя;
        this\.возраст \= возраст;
    \}

    public String получитьИмя\(\) \{
        return имя;
    \}

    public int получитьВозраст\(\) \{
        return возраст;
    \}
\}

public class ДомашниеЖивотные extends Животное \{

    private String\[\] команды;

    public ДомашниеЖивотные\(String имя, int возраст, String\[\] команды\) \{
        super\(имя, возраст\);
        this\.команды \= команды;
    \}

    public void добавитьКоманду\(String новаяКоманда\) \{
        // Логика добавления новой команды для домашнего животного
    \}
\}

public class ВьючныеЖивотные extends Животное \{
    private String\[\] задачи;

    public ВьючныеЖивотные\(String имя, int возраст, String\[\] задачи\) \{
        super\(имя, возраст\);
        this\.задачи \= задачи;
    \}

    public void добавитьЗадачу\(String новаяЗадача\) \{
        // Логика добавления новой задачи для вьючного животного
    \}
\}

14. 14. Написать программу, имитирующую работу реестра домашних животных.
В программе должен быть реализован следующий функционал:
14.1 Завести новое животное
14.2 определять животное в правильный класс
14.3 увидеть список команд, которое выполняет животное
14.4 обучить животное новым командам
14.5 Реализовать навигацию по меню


import java\.util\.Scanner;

public class РеестрЖивотных \{
    public static void main\(String\[\] args\) \{
        Scanner scanner \= new Scanner\(System\.in\);

        System\.out\.println\("Добро пожаловать в реестр домашних животных\!"\);
        System\.out\.println\("Выберите действие:"\);
        System\.out\.println\("1\. Завести новое животное"\);
        System\.out\.println\("2\. Определить животное в правильный класс"\);
        System\.out\.println\("3\. Увидеть список команд, которое выполняет животное"\);
        System\.out\.println\("4\. Обучить животное новым командам"\);

        int выбор \= scanner\.nextInt\(\);
        switch \(выбор\) \{
            case 1:
                // Логика для заведения нового животного
                break;
            case 2:
                // Логика для определения класса животного
                break;
            case 3:
                // Логика для просмотра списка команд животного
                break;
                
            case 4:
                // Логика для обучения животного новым командам
                break;
            default:
                System\.out\.println\("Некорректный выбор\!"\);
        \}
    \}
\}


15.Создайте класс Счетчик, у которого есть метод add(), увеличивающий̆
значение внутренней̆int переменной̆на 1 при нажатие “Завести новое
животное” Сделайте так, чтобы с объектом такого типа можно было работать в
блоке try-with-resources. Нужно бросить исключение, если работа с объектом
типа счетчик была не в ресурсном try и/или ресурс остался открыт. Значение
считать в ресурсе try, если при заведения животного заполнены все поля.

java
public class Счетчик implements AutoCloseable \{
    private int значение \= 0;

    public void add\(\) \{
        значение\+\+;
    \}

    @Override
    public void close\(\) throws Exception \{
        if \(значение \=\= 0\) \{
            throw new Exception\("Ресурс не был использован"\);
        \}
    \}
\}

public class ПримерИспользованияСчетчика \{
    public static void main\(String\[\] args\) \{
        try \(Счетчик счетчик \= new Счетчик\(\)\) \{
            счетчик\.add\(\);
            // Логика работы с объектом счетчика
        \} catch \(Exception e\) \{
            e\.printStackTrace\(\);
        \}
    \}
\}




  
 




 






