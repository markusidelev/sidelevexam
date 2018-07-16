# Задание

### Вводная
Вы получаете заготовку готового клиент-серверного приложения, требующего доработки согласно описанного ТЗ. 
Макет доступен по [ссылке](https://drive.google.com/open?id=1D0BRnNpj8GXESagePPYVknEx5J9jwAqU),
предоставляется [дамп БД](http://bit.ly/blog-db). При выполнении задания вам потребуется 
использовать полученные знания по HTML/CSS, JavaScript, PHP, MySQL. Для конфигурационных данных необходимо использовать
файл `config.php` в корне проекта. Для вывода статей на страницу требуются данные: изображение статьи (если оно доступно),
заголовок статьи, имя автора, дата публикации (формат даты показан на макете), краткое описание статьи (поле `annotation`
таблицы `articles`). 

## Техническое задание
Требуется сверстать данную страничку согласно предлагаемого макета. Написать js-код, выполняющий требуемый функционал. Написать php-код для полноценной работы страницы. Необходимо в связке  php+js **обязательно реализовать функционирование указанных компонентов страницы согласно макету**:

+ **Выпадающий список фильтрации статей по имени автора**

+ **Фильтр по годам публикаций**

+ **Фильтр по месяцам публикаций**

+ **Блок пагинации статей**

Контент, выводимый на странице - статьи - необходимо формировать динамически, т.е. с использованием возможностей JS. 
Вообще, любой код, который предлагается вам в данной заготовке, допускается изменять любым удобным вам 
образом. Обязательно лишь выполнение поставленных задач указанными способами(при наличии описания). 
Пагинация должна работать следующим образом: кнопки с двойной стрелкой переносят на первую/последнюю из доступных страниц,
кнопки с одинарной стрелкой переносят на предыдущую/следующую страницу, кнопки с цифрами переносят на соответствующую страницу.
Какие кнопки должны отображаться показано на макете.

**Взаимодействие с сервером должно осуществляться без перезагрузки страницы, т.е. с помощью ajax. Для уточнения запросов
требуется передавать серверу POST-параметры. Сервер должен отдавать данные в формате json (MIME application/json).**
На странице должно выводиться фиксированное кол-во статей(указывается в `config.php`). Порядок общения следующий:
1. При загрузке страницы вы должны отправлять ajax-запрос на корневой адрес сайта с параметром `init=1`. В ответе  
сервера должны быть указаны: кол-во доступных статей, кол-во страниц пагинации, список авторов статей с их `id`, 
данные для вывода статей на текущую страницу, года для формирования фильтра. На основании полученных данных на клиентской 
стороне формируется контент и выводится в браузере.
2. При выборе автора из выпадающего списка на сервер должен уходить параметр `author=25`, где значением параметра является
`id` автора из соответствующий записи в БД (таблица `authors`). В ответе сервера должны быть года статей данного автора, 
кол-во статей автора, данные о статьях для вывода на текущую страницу.
3. При выборе фильтра по году - клик по конкретному году - на сервер должен уходить параметр `year=2010` с указанием выбранного
года. В ответе от сервера должны быть месяцы, в которые в выбранном году были статьи; данные для вывода статей на текущую страницу;
кол-во статей. Если при этом выбран автор, то нужно предоставить статьи, написанные выбранным автором в указанный год. 
Соответственно и данные о месяцах должны быть корректными.
4. При выборе месяца на сервер должен уходит параметр `month=0` с указанием номера выбранного месяца. В ответе от сервера
должны содержаться данные о кол-ве статей, написанных в выбранный месяц. При наличии параметров выбора автора и/или года
должны быть предоставлены данные о статьях, соответсвующих всем предоставленным параметрам. Если не указан автор, то предоставляются
статьи, созданные в указанный месяц указанного года и их кол-во. 
5. Для построения и использования пагинации необходимо передавать на сервер параметр `page=1` с номером страницы, на 
которую производится переход. При наличии каких-либо параметров фильтрации они также должны быть переданы на сервер. 
В ответе сервера должны содержаться данные статей, которые должны быть выведены на указанную страницу.

## Дополнительные задания
Для получения бонусных баллов необходимо реализовать в приведенном коде-заготовке механизм автозагрузки классов по psr-4.
Также желательна возможность при наличии установленных параметров-фильтров при перезагрузке страницы, чтобы они не сбрасывались
и данные выводились соответствующие существующим фильтрам(Например, если у меня выводится страница №2 со статьями Иванова И.Н.,
опубликованными в марте 2007 года, то при перезагрузке страницы я должен увидеть ту же самую подборку статей). 


Если в процессе выполнения задания вы почуствуете жгучее желание изменить уже существующий код - не стесняйтесь, оценка 
снижена не будет. При необходимости описания каких-либо вспомогательных функций, вы можете разместить их в `core/helpers.php`.
Если вы считаете, что в каком-то классе не хватает каких-то методов или существующие можно переработать - разрешается 
вносить изменения в любой существующий код. Решение должно быть предоставлено в виде ссылки на репозиторий с инструкцией
по развертке проекта, если она требуется. Для того, чтобы развернуть данную заготовку, необходимо загрузить корневую папку
сайта в папку вашего веб-сервера, в случае OpenServer это domains/localhost и получить доступ к сайту по адресу `http://localhost`.
Дамп базы данных следует импортировать в свою базу, после чего прописать необходимые конфигурационные данные для доступа к БД
в файле `config.php` в корне проекта. 
