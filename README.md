# MainsLab
Данные мной были импортированы с помощью мастера импорта и экспорта SQL Server.
В результате, все столбцы получились с типом данных varchar(50).
Столбцы service_amount и service_number я преобразовал в float и сохранил в столбцах service_amount2 и service_number2.

После этого я посмотрел крайние значения по всем столбцам.
Выяснилось, что в нескольких строках значения service_amount2 и service_number2 отсутствовали. Я удалил эти строки.
Кроме того, в одной строке service_amount2 оказался в размере 100 миллиардов, что на 6 порядков превышало следующее по величине значение.
Я взял на себя смелость удалить эту строку тоже. Был один клиент, который родился в 1901 году. Теоретически это возможно и я его оставил.
Меня удивило, что было много строк, где значение service_amount2 и service_number2 было меньше 1. Я не стал их удалять, так как этого не было в задании.
Но самое интересное, что в большом количестве строк (около 1 %) дата рождения была больше даты оказания услуги. То есть человек еще не родился,
но у него уже был страховой полис и ему оказывались услуги. Я попытался прояснить этот вопрос у HR, но не получил конкретных указаний.
Поэтому я оставил эти строки и определил этих клиентов в возрастную группу "0-18".
Названия некоторых лечебных учреждений были записаны кириллицей и неверно отобразились в БД.
Но эти названия не потеряли своей уникальности, а для решения данной задачи этого было достаточно.

Следующим этапом я удалил окончание ".0" у record_id и insured. Можно было обойтись и без этого, но я это сделал.
И подготовку данных я заончил созданием столбцов, которые указывают возраст и возрастную группу пациента на день оказания услуги.

В завершении работы с БД я подготовил 2 запроса. Первый запрос извлекал средний чек по месяцам топ 10 клиник. А второй извлекал таблицу, 
в которой были ответы на остальные вопросы задания.

На первом дашборде в левой части я разместил 2 диаграммы, которые показывали половозрастную структуру застрахованных по каждому году. С помощью среза по месяцам 
можно выбирать период времени и сравнивать эти диаграммы между собой.
В правой части первого дашборда я разместил 2 диаграммы, которые показывают средний чек по месяцам топ 10 клиник по каждому году.

На втором дашборде я разместил 2 диаграммы, которые показывают среднего количества визитов и среднего количества кейсов на застрахованного
по сравнению с аналогичным периодом год назад.
С помощью фильтров можно изучать эти данные в разрезе пола и возрастной группы застрахованных.

Второй способ был сделан с помощью Юпитер Ноутбук. Там все получилось аналогично, кроме того, что у меня не получилось посчитать количесто кейсов.
