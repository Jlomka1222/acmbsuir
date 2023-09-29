# Содержание
1. [Введение](#intro)  
  1.1 [Назначение](#appoi)  
  1.2 [Аналоги](#analogs)
2. [Требования пользователя](#user_requirements)  
   2.1 [Програмные интерфейсы](#program_interfaces)  
   2.2 [Интерфейс пользователя](#user_interface)  
   2.3 [Характеристика пользователей](#user_config)  
   2.4 [Предположения и зависимости](#dependencies)    
4. [Системные требования](#system_requirements)  
  3.1 [Функциональные требования](#functional_requirements)  
  3.2 [Список таблиц](#list_of_tables)  
  3.3 [Нефункциональные требования](#nonfunctional_requirements)  
      3.3.1 [Надежность](#reliability)  
      3.3.2 [Безопасность](#safety)
      3.3.3 [Производительность](#performance)


# 1. Введение

<a name="intro"/>

## 1.1 Назначение

<a name="appoi"/>
В данном документе описано техническое задание поставленное для выполнение проекта "Система регистрации студенов на олимпиаду". Данное приложение является web-приложением, ниже приведены требования пользователя, функциональные и нефункциональные требования к данному приложению. Вся приведенная информация ниже предназначена для упрощения работы команде, реализующей данный проект.
Данный проект предназначается для регистрации команд для участия в олимпиаде BSUIR OPEN. 

## 1.2 Аналоги

<a name="analogs"/>
На просторах интернета можно найти много web-приложений, которые были разработаны для схожих целей: регистрация участников на различные олимпиады по программированию. Но в связи с тем, что каждая олимпиада имеет свои особенности и функции, все web-приложения имеют свой уникальный функционал и каждый проект является авторским решением, удовлетворяющим необходимые в конкретной ситуации требования.

# 2. Требования пользователя 

 <a name="user_requirements"/>

## 2.1 Програмные интерфейсы 

 <a name="program_interfaces"/>

Тестирующая система, разработанная специально под данный проект Иваном Удовиным 

## 2.2 Интерфейс пользователя 

<a name="user_interface"/>

[Главное меню](https://github.com/Jlomka1222/acmbsuir/blob/main/Mocups/MainPage.png)  


[Регистрация пользователя](https://github.com/Jlomka1222/acmbsuir/blob/main/Mocups/SignUp.png)  

[Добавление участника](https://github.com/Jlomka1222/acmbsuir/blob/main/Mocups/AddUserToUser.png)  

[Меню команды](https://github.com/Jlomka1222/acmbsuir/blob/main/Mocups/AddUserToUser-1.png)  

[Расписание](https://github.com/Jlomka1222/acmbsuir/blob/main/Mocups/Schedule.png)  
[Расписание-1](https://github.com/Jlomka1222/acmbsuir/blob/main/Mocups/Schedule-1.png)  
[Расписание-2](https://github.com/Jlomka1222/acmbsuir/blob/main/Mocups/Schedule-2.png)  
[Расписание-3](https://github.com/Jlomka1222/acmbsuir/blob/main/Mocups/Schedule-3.png)  

[Спонсоры](https://github.com/Jlomka1222/acmbsuir/blob/main/Mocups/Sponsor.png)

[Этапы](https://github.com/Jlomka1222/acmbsuir/blob/main/Mocups/Stages.png)


## 2.3 Характеристики пользователя 

<a name="user_config"/>
Пользователями данного приложения будут являтся участники олимпиады, а также их тренера. Участниками являются студенты/школьники, изъявившие желание участвовать в олимпиаде BSUIR OPEN, предположительно, люди участвующие в олимпиадах в IT сфере имеют достойный уровень тезничесской грамотоности и могут польховаться предоставленными им приложениями. 
 
## 2.4 Предположения и зависимости 

 <a name="dependencies"/>
 
1. Пользователь не может получить доступ к Web-приложению если отсутствует подключение к Интернету   
2. Пользователь не может зарегестрировать при отсутствии почты 

# 3. Системные требования  

<a name="system_requirements"/>  

## 3.1 Функциональные требования:    

<a name="functional_requirements"/>  

1. Авторизация пользователей
2. Система ролей
3. Логгирование действий пользователей
4. Управление пользователями
5. Создание олимпиад
6. Регистрация участников на олимпиаду
7. Регистрация команды на олимпиаду
8. Панель администратора

    - Изменение статуса команды
    - Создание аккаунта в тестирующей системе для команды
    - Создание таблиц с информацией для организаторов

        - Учетные записи команд
        - Расположение команд по аудиториям
        - Распределение участников по командам

    - Создание изменение шаблонов писем для рассылки пользователям  

---  
  
## 3.2 Список таблиц:  

<a name="list_of_tables"/>

1. User - пользователь
    - username - varchar(30) NOT NULL, UNIQUE
    - email - varchar(60) NOT NULL, must be valid email, UNIQUE
    - firstname - varchar(50) NOT NULL
    - midname - varchar(50) NOT NULL
    - lastname - varchar(50) NOT NULL
    - education - varchar(200) NOT NULL
    - password - varchar(200) NOT NULL
    - salt - varchar(100) NOT NULL
2. Role - роли пользователей
    - name - varchar(50) NOT NULL, UNIQUE
3. Coach - тренеры 
    - email - varchar(60) NOT NULL, must be valid email, UNIQUE
    - firstname - varchar(50) NOT NULL
    - midname - varchar(50) NOT NULL
    - lastname - varchar(50) NOT NULL
    - tshirt_size - MtO(TShirt size) NOT NULL
    - team - MtM(Team) NOT NULL
4. Participant - участник олимпиады
    - user - OtO(User) NOT NULL
    - firstname - varchar(50) NOT NULL 
    - midname - varchar(50) NOT NULL
    - lastname - varchar(50) NOT NULL
    - email - varchar(60) NOT NULL, must be valid email
    - education - varchar(200) NOT NULL
    - team - MtO(Team)
    - tshirt_size - MtO(TShirt size)
5. Team - команда
    - name - varchar(50) NOT NULL, UNIQUE
    - status - varchar('not done', 'pending', 'approved', 'disqualified') NOT NULL
    - type - MtO(Team type) NOT NULL
    - code - varchar(8) NOT NULL
    - stage - MtO(Olymp stage)
    - tag - varchar(20)
    - olympiad - MtO(Olympiad) NOT NULL
6. Team type - типа команды, может быть школьной или студенческой
    - name - varchar(20) NOT NULL, UNIQUE
7. Olymp stage - стадия олимпиады
    - name - varchar(20) NOT NULL, UNIQUE
    - olympiad - MtO(Olympiad) NOT NULL
    - date - datetime()
8. Email Template - шаблон для писем участникам
    - Olymp Stage - OtO(Olymp Stage) NOT NULL
    - content - text() NOT NULL
9. Olympiad - олимпиада
    - name - varchar(100) NOT NULL, UNIQUE
    - is_opened_registration - boolean default=false
    - type - varchar('ICPC', 'IOI') NOT NULL
10. Logs - журнал действий пользователя
    - user - MtO(User) NOT NULL
    - operation - varchar('create', 'delete', 'update') NOT NULL
    - timestamp - timestamp NOT NULL
    - old - text()
    - new - text()
11. TShirt Size - размеры маек
    - name - varchar(5) NOT NULL, UNIQUE

## 3.3 Нефункциональные требования

<a name="nonfunctional_requirements"/>

### 3.2.1 Надежность  

<a name="reliability"/>  

Сервера находятся в датацентре, обслуживающем некоторые государственные сайты. Благодаря этому они обслуживаются по гостам, а также контролируется безопасность на высшем уровне.

### 3.2.2 Безопасность  

<a name="safety"/>  

Пароли пользователей защищены двойным хешированием. У каждого пользователя есть две соли: собственная и системная, которые хранятся соответственно в базе данных и на сервере. Таким образом, для получения пароля необходимо найти два значения, хранящихся в разных местах, за счет чего и достигается высокий уровень безопасности.

### 3.2.3 Производительность  

<a name="performance"/>  

Так как сайт тестирующей системы помимо задач информирования, частично решает задачи проведения контеста, к нему предъявляются особые требования к производительности, а именно:
- Сайт должен обеспечивать загрузку страниц и выполнение заданий в течение приемлемого времени для участников олимпиады. В среднем, участник олимпиады должен быть в состоянии загрузить страницу задания и начать его выполнение в течение 1 секунды.
- Время выполнения задания: не более 1 минуты
- Время проверки решения: не более 1 минуты

Для оценки этих критериев предпологается к использованию подход "метрик" - условных параметров, по которым можно оценить состояние и загрузку сайта. К важным метрикам, необходимым для аналитики и контроля состояния стоит отнести:
- скорость загрузки страницы
- количество ошибок сайта
- количество ошибок тестирующей системы
- RPS - response per second
- количество зарегистрированных пользователей
- длительность выполнения запросов в базу данных
