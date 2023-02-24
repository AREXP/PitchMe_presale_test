# Техническое тестовое задание на должность пресейл-инженера

## Описание

### Нужно написать cli-программу, которая отфильтровывает профили, подходящие условию.

Профиль – описание карьерного пути человека.
Он содержит:
* Имя
* Фамилию
* Список скиллов(строки), которыми владеет человек. Как правило это все скиллы из всех мест работы ниже. 
* О себе. Свободный текст, которым человек описывает себя.
* Текущая локация
    * Страна
    * Город
* Опыт, неупорядоченный список состоящий из элементов:
    * Название компании
    * Должность
    * Короткое описание что делал кандидат на этом месте
    * Скиллы, которые он применял на этом месте
    * Дата начала работы в этой компании
    * Дата окончания работы в этой компании. Может быть пустым, это означает, что кандидат сейчас работает на этой должности.
    * Локация
        * Страна
        * Город

Все даты в формате YYYY-MM-DD.
Если человек в работал в одно время в нескольких местах, то считаем это опыт как один. Допустим в 2020 году он работал в двух местах, этот год все рано засчитываем как один год опыта, не два.

В репозитории есть файл, содержащий pydantic-схему профиля, ей необходимо воспользоваться для десериализации.

Список профилей должен быть json-файлом, лежащем в проекте. Для простоты все текстовые значения должны быть на английском языке.

## Задание
Подготовить две функции-проверки:
* Опытный python-разработчик
    * Работал в FAANG на одном из последних двух местах работы
    * Должность на трех последних местах  Backend developer или Software engineer
    * Общий опыт более 8 лет
    * На последнем месте работал с python и c++
    * Живет в Лондоне
* Middle UX-designer
    * На двух(или одном если компания одна) последних местах работал: Product designer или UX-designer или подобное
    * Владеет Figma, Sketch, UX-research, Miro(Любыми двумя)
    * Живет в евросоюзе
    * Опыт на последнем месте работы более двух лет
    * Общий опыт менее пяти лет

Под последними местами выше подразумеваются время. То есть также нужно упорядочит опыт по дате начала работы, в идеале сделать это в pydantic-схеме.

## Интерфейс:
Программа должна запускаться из консоли в виде:

`python <your entry point> --filter <chosen filter> —-input <file_name>`

Где:
* chosen filter параметр, который выбирает одну из проверок
* file_name, файл со списком профилей. Подготовить также и негативные сценарии
Имена параметров могут быть изменены по вашему усмотрению

Вывод:
Для каждого профиля из file_name в консоль печатается статус проверки:
```
$ python3 <args>
John Smith – True
Elon Musk – False, Not enough experience
Steve Jobs – False, Never worked in UK
…
```
Значения:
* True –  проверка пройдена
* False, reason – проверка не пройдена, reason причина(если причин несколько, то достаточно одной). Причины назвать по своему усмотрению.


## Порядок сдачи:
* Форк этого репозитория и пулл реквест по завершении
* Если форк приватный, то пригласить туда arexp19@gmail.com 
* Должны быть приложены примеры запуска, чтобы я мог склонировал репозиторий и запустил проверки.
* Примеры запуска описать в конце этого ридми-файла.
* Должно запуститься на линуксе или маке. Проверить на виндоусе возможности нет.

## Технические ограничения:
* python3.7+
* Только built-in модули, кроме следующего пункта
* pydantic==1.7.3, requirements.txt не обязателен, считаем, что он есть на моем компьютере
