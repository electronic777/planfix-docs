Функция переводит дату и время из одного часового пояса в другой. Например, это удобно, если вы получаете дату в формате UTC, а вам необходимо узнать локальное время клиента. 


## Формат


**CONVERTTIMEZONE(** Дата и время; Исходная таймзона; Нужная таймзона**)**


где: 


  * названия таймзон из списка [IANA](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).


## Примеры


CONVERTTIMEZONE("2025-06-13 15:00"; "UTC"; "America/New_York") 


CONVERTTIMEZONE("2025-06-13 15:00"; "America/New_York"; "America/Los_Angeles")
