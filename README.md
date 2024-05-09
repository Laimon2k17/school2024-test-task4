# Тестовое задание для отбора на Летнюю ИТ-школу КРОК по разработке

## Условие задания
Будучи тимлидом команды разработки, вы получили от менеджера проекта задачу повысить скорость разработки. Звучит, как начало плохого анекдота, но, тем не менее, решение вам все же нужно найти. В ходе размышлений и изучений различного внешнего опыта других команд разработки вы решили попробовать инструменты геймификации. То есть применить техники и подходы игрового характера с целью повышения вовлеченности команды в решение задач.

Вами была придумана рейтинговая таблица самых активных контрибьютеров за спринт. Что это значит в теории: по окончании итерации (4 рабочие недели) выгружается список коммитов, сделанных в релизную ветку продукта, и на его основе вычисляются трое самых активных разработчиков, сделавших наибольшее количество коммитов. В зависимости от занятого места, разработчик получает определенное количество внутренней валюты вашей компании, которую он впоследствии может обменять на какие-то товары из внутреннего магазина.

На практике вы видите решение следующим образом: на следующий день после окончания спринта в 00:00 запускается автоматическая процедура, которая забирает файл с данными о коммитах в релизную ветку, сделанных в период спринта, после чего выполняется поиск 3-х самых активных контрибьютеров. Имена найденных разработчиков записываются в файл, который впоследствии отправляется вам на почту.

В рамках практической реализации данной задачи вам необходимо разработать процедуру формирование отчета “Топ-3 контрибьютера”. Данная процедура принимает на вход текстовый файл (commits.txt), содержащий данные о коммитах (построчно). Каждая строка содержит сведения о коммите в релизную ветку в формате: “_<Имя пользователя> <Сокращенный хэш коммита> <Дата и время коммита>_”.
Например: AIvanov 25ec001 2024-04-24T13:56:39.492

К данным предъявляются следующие требования:
- имя пользователя может содержать латинские символы в любом регистре, цифры (но не начинаться с них), а также символ "_";
- сокращенный хэш коммита представляет из себя строку в нижнем регистре, состояющую из 7 символов: букв латинского алфавита, а также цифр;
- дата и время коммита в формате YYYY-MM-ddTHH:mm:ss.

В результате работы процедура формирует новый файл (result.txt), содержащий информацию об именах 3-х самых активных пользователей по одному в каждой строке в порядке убывания места в рейтинге. Пример содержимого файла:
AIvanov
AKalinina
CodeKiller777

Ручной ввод пути к файлу (через консоль, через правку переменной в коде и т.д.) недопустим. Необходимость любых ручных действий с файлами в процессе работы программы будут обнулять решение.

## Автор решения
Ованов Роман Романович
## Описание реализации
В самом начале мы импортируем необходимые модули (os - для проверки существования файла commits.txt, datetime - для работы с датой и временем), а также импортируем класс Counter из модуля collections для подсчета кол-ва элементов.
Далее, объявляем функцию top_contributors с параметром input_file (путь к файлу). Эта функция выполняет необходимые проверки. Сначала идёт проверка на существование файла в дирректории, потом выполняется чтение файла. Потом проходим по каждому элементу в списке данных. В цикле выполняется проверки на формат даты и времени, имени пользователя, хэша, а также общий формат данных в строке.
Затем считается кол-во коммитов для каждого пользователя, а уже потом идёт поиск трёх пользователей с наибольшим кол-о коммитов.
Результаты записываются в файл result.txt
В конце вызывается функция с указание пути к файлу.
## Инструкция по сборке и запуску решения
### Сборка проекта:

1.  **Скачайте исходный код проекта:**
    *   Загрузите архив с исходным кодом с веб-сайта проекта и распакуйте его в удобное место.
2.  **Настройка окружения:**
    *   Убедитесь, что в вашей системе установлен Python3 (если нет, то установите с оффициального сайта `python.org`).
3.  **Подготовка данных:**
    *   Проверьте, что у вас есть необходимые файлы данных, `commits.txt`, с которыми проект будет работать. Если их нет, создайте его.

### Запуск проекта:

1.  **Откройте терминал или командную строку:**
    *   Запустите терминал или командную строку на вашем компьютере.
2.  **Перейдите в директорию проекта:**
    *   Используйте команду `cd <путь_к_директории_проекта>` для перехода в директорию, где находится ваш проект.
3.  **Запуск скрипта:**
    *   Запустите скрипт проекта, который вы хотите выполнить, `python main.py`.
4.  **Проверьте результат:**
    *   После выполнения скрипта проверьте результат его работы. Должен быть создан файл с результатом (result.txt)
