# Сессия 3

* Разработка библиотеки классов 
    * Общие требования
    * Класс аналитики ([реализация](#Разработка-библиотеки-классов-реализация))
    * Разработка модульных тестов
    * Разработка тестовых сценариев

## Разработка библиотеки классов

Инструкция с картинками [ниже](#Разработка-библиотеки-классов-реализация)

### Общие требования

>В связи со стремительным развитием нашей системы было решено вынести некоторый важный функционал за рамки основного проекта и сделать библиотеку классов, которую мы сможем подключать
к любому нашему проекту в случае расширения. Данная библиотека будет подключаться к основному проекту и должна быть представлена в виде `.dll/.jar` файла или папки с файлом `.py`.
>
>Чтобы система правильно интегрировалась вам необходимо обязательно следовать правилам именования библиотек, классов и методов в них. В случае ошибок в рамках именования ваша работа не
может быть проверена и ваш результат не будет зачтен. Классы и методы должны содержать модификатор `public` (если это реализуемо в рамках платформы), чтобы внешние приложения могли
получить к ним доступ.
>
>В качестве названия для библиотеки необходимо использовать: `CompanyCoreLib`. Вам необходимо загрузить исходный код проекта с библиотекой в отдельный репозиторий с названием, совпадающим с
названием приложения.

### Класс аналитики

>Вам необходимо создать класс с названием **Analytics**, который будет позволять проводить аналитику различных процессов в рамках компании.
>
>Реализуйте метод, который принимает в себя список объектов даты и времени по совершенным покупкам/заказам в рамках нашей компании, а возвращает список дат (без времени), отсортированный в порядке уменьшения частоты заказов. Это необходимо, чтобы наша компания могла прогнозировать наиболее высокий спрос на следующий год для обеспечения более качественного оказания услуг.
Возвращаемые данные должны содержать только даты для первого числа каждого месяца и 00:00 минут.
>
>Например, вам поступили следующие данные: `2019-12-12 14:43, 2019-12-01 15:05, 2019-11-04 09:01`, а, значит, самый популярный месяц - декабрь. Вам необходимо вернуть следующие данные: `2019-12-01 00:00, 2019-11-01 00:00`. В случае совпадения характеристик популярности сперва нужно вывести более
ранние месяцы.
>
>Прогноз строится на основе предыдущего года. Так что данные Вам будут выдаваться строго за предыдущий год.
>
>Спецификация метода представлена в отдельном файле в ресурсах.

### Разработка модульных тестов (Unit-tests)

>Для выполнения процедуры тестирования созданного вами метода библиотеки CompanyCoreLib, возвращающего упорядоченный список популярных месяцев, вам необходимо создать отдельный проект
модульных тестов.
>
>В рамках проекта разработайте тесты, максимально полно покрывающие функционал метода. Ничего страшного, если ваш метод работает не совсем идеально и тесты могут быть не пройдены в связи с этим - в данном модуле это не так важно.
>
>Обратите внимание, что имена тестов должны отражать их суть, т.е. вместо `TestMethod1()` тест следует назвать, например, `PopularMonths_NullList()` для тестирования случая передачи пустой коллекции дат.
>
>Необходимо разработать модульные тесты, которые на основании исходных данных можно условно разделить на 2 группы следующим образом: 10 методов низкой сложности и 5 методов высокой
сложности.

### Разработка тестовых сценариев (Test-cases)

>Для выполнения процедуры тестирования удаления товаров Вам нужно описать пять сценариев.
>
>Удаление может быть выполнимо, а может быть отклонено согласно требованиям предметной области.
>
>Необходимо, чтобы варианты тестирования демонстрировали различные исходы работы алгоритма. Для описания тестовых сценариев в ресурсах предоставлен шаблон `testing-template.docx`.

---

## Разработка библиотеки классов (реализация)

Я в ходе предварительной подготовки показывал как делать тесты для проекта, они в принципе одинаковые для любого типа проектов. Но все (и МРМТ тоже) впали в ступор от слов "библиотека классов". Заполним этот пробел.

Библиотека это отдельный проект. Для C# этот проект должен генерировать файл `*.dll`

### Замечания по репозиторию

На демо экзамене ни главный админ, ни я не читали задание (мне вообще нельзя было это делать), поэтому ввели всех в заблуждение, что нужно все пихать в один репозиторий. Но в задании явно сказано "*В качестве названия для библиотеки необходимо использовать: `CompanyCoreLib`. Вам необходимо загрузить исходный код проекта с библиотекой в **отдельный** репозиторий с названием, совпадающим с названием приложения.*" То есть надо было поднять руку и сказать, что Вы, товарищ главный админ не правы. На будущее - пишете какие хотите репозитории в свой аккаунт на локальном ГИТ-е, но имейте в виду, что эксперты не будут разбираться в вашей иерархии, сказано, что репозиторий должен называться `CompanyCoreLib`, значит его и откроют, а искать по другимм репозиториям не будут.

>Однако в "Требованиях и рекомендациях" указано, что каждая сессия должна быть загружена в отдельную **ветку** с названием "Сессия Х"... Но к этому вроде не придирались (посмотрю еще в критериях оценки).

Т.е. у вас в итоге должно получиться 3 репозитория:

* session1 (с диаграммами, не помню чтобы там были требования к названию репозитория, если вдруг увидите, то называйте как положено)
* my_cool_program (пока не смотрел как надо именовать приложение во второй сессии, но скорее всего созвучно названию компании)
* CompanyCoreLib (третья сессия - тут явно указано какое имя должно быть у репозитория)

### Создание проекта

Создаем **новый** проект, установив нужные фильтры (C#, Windows, Библиотека) и выбрав проект для соответствующей платформы. Мы всё делаем для **.NET Framework**.

![создание проекта](../img/demo03.png)

Не забываем указать название проекта. Как вы тут напишете, так dll и будет называться.

![ввод названия](../img/demo04.png)

В итоге студия создаст нам "рыбу" с одним файлом:

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace CompanyCoreLib
{
    public class Class1
    {
    }
}
```

### Создание класса аналитики

Можно, конечно, прямо в этом файле переименовать класс, но это нарушение логической структуры проекта (файл то будет называться по-старому). Поэтому создаем новый класс (1), а рыбу удаляем (2).

1. *Контекстное меню проекта -> Добавить -> Создать элемент*. Далее в списке находим "Класс" и не забываем задать ему название (Analytics в нашем случае). Получится аналогичная "рыба" с нужным названием класса:

    ```cs
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace CompanyCoreLib
    {
        class Analytics
        {
        }
    }
    ```
2. *Контекстное меню Class1 -> Удалить*

### Реализация класса аналитики

В *спецификации метода* (был и такой файл в материалах сессии 3) указано название метода и его параметры, добавляем в наш класс:

```cs
public class Analytics
{
    public List<DateTime> PopularMonths(List<DateTime> dates) {
        return dates;
    }
}
```

**Во-первых**, обращаем внимание на ключевое слово "public" перед названием КЛАССА. Студия его автоматом не пишет, а для экспорта оно нужно. На эти грабли мы уже наступали при тестировании, напоминаю еще раз.

**Во-вторых**, на этом этапе не надо ничего придумывать - и типы данных, и название метода, и даже название параметра метода явно указаны с спецификации.

Собственно уже эта реализация дает почти целый балл в оценке (хотя она ничего и не делает, просто возвращает то что пришло обратно)

Полная реализация
