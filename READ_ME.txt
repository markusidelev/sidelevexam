Экзамен 
Сиделев Данил

//////////
Внимание!
В зависимости от компьютера (сервера) скорость обновления контента на странице может падать. Если начать активно нажимать на кнопки выбора фильтров - страницы обновятся столько же раз. Обычно, на выполнение любого запроса тратится несколько милисекунд. Если после нажатия ничего не происходит - подождите секунд 10, в зависимости от железа. 
//////////


Постараюсь описать здесь, что работает:

    /////////
    Реализованно:
        Первичная загрузка данных при открытии страницы.
            (Загрузка статей при включении происходит в своем изначальном случайном порядке, как в базе. Я бы выставил в порядке новизны статей (эта строчка в запросе закоментированна), но это сильно уменьшает скорость всех загрузок и такого требования нет в задании. Оставляю случайность базы на совести её создателя =) )

        Загрузка всех имен авторов и генерация select при открытии страницы 

        Генерация блоков статей с картинками, авторами, датой и текстом (аннотацией)
            Реализованно с помощью template и underscore.js
            Количество выводимых статей на одну страницу меняется в файле config

        Генерация блока пагинации (первая страница, последняя, следущая, предыдущая)
            Блок пагинации обновляется при каждом переключении страницы или фильтров
            Реализованно с помощью template и underscore.js
            Делал похожей на оригинал, но позволил себе вольности в стилях и количестве кнопок
            Пред-предпоследняя кнопка - номер последней страницы, так захотел

        Загрузка данных при выбранном фильтре и генерация блоков. (год, месяц, автор)
            Количество статей при выбранном фильтре влияет на пагинацию
            Адекватно реагирует на малое количество данных, меньше одной страницы (кажется)

        При нажатии на уже активный фильтр (год или/и месяц) отключает его. 
            Селектор авторов работает так же (при нажатии на -выберите автора-)

        
        Стили элементов страницы сделаны в близком соответсвии с оригиналом, но я позволил себе вольности.
            
        Сделана адаптация к экранам предоставленного размера (меньше 768px)
            Разве что не сделана мобильная адаптация блока пагинации

        Все параметры в запросах и ответах реализованы как в задании (кажется)


    //////////
    Не реализовано: 
       Дополнительным заданием с подгрузкой классов не занимался

        Не успел реализовать дополнительное задание - сохранение фильтров и состояния страницы при перезагрузке, но знаю, как это делать. Реализовывал подобное в домашнем задании с крестиками-ноликами, приложу ссылку. Знаю, что к оценке это ничего не добавит, это для совести.         
            https://markusidelev.github.io/porftolio/crossandtoes/  

        Хотел реализовать вывод даты в том же формате, как и на макете (например "7 февраля 2017"), но не успел. Я реализовал это в своем первом варианте вывода статей (оставил в content.php) и реализовал это с помощью js отдельно, но никак не успел подружить это с template и underscore.js.

        Возможно, ещё что-то упустил или забыл реализовать.

    /////////
    Известные баги:
        В body выводится респонс (как я понял) прямо на страницу. Не вылечил, спрятал под незакрытым комментарием в index.view.php 