# Задание к лекции 2.1 Массивы одномерные
## Задача 3.

### Описание
Напишем программу вывода информации прибытия общественного транспорта (автобусов, троллейбусов и маршрутного такси) на остановку.
Оператор вводит данные о номере маршрута автобуса и времени прибытия. После каждого обновления информации, данные выводятся на экран
в отсортированном виде, начиная от ближайшего времени прибытия к наиболее позднему в следующем формате: `тип транспорта, номер маршрута, время прибытия`.
Для выхода из программы нажать `<enter>`.

### Функционал программы
1. Создание массива времени прибытия общественного транспорта (пользовательский ввод из консоли);
2. Вывод времени прибытия и типа общественного транспорта, номеров маршрутов и времени прибытия в консоль. 

### Пример
```
Введите через пробел тип транспорта, номер маршрута и время прибытия в формате (hh:MM)
автобус М7 7:40 <enter>

Информационное табло:
Тип транспорта Маршрут Время прибытия
автобус        М7      7:40

Введите через пробел тип транспорта, номер маршрута и время прибытия в формате (hh:MM)
троллейбус 8 7:41 <enter>

Информационное табло:
Тип транспорта Маршрут Время прибытия
автобус        М7      7:40
троллейбус     8       7:41

Введите через пробел тип транспорта, номер маршрута и время прибытия в формате (hh:MM)
<enter>
Программа завершена.
```

### Пример реализации
1. Создадим класс для хранения времени прибытия транспорта `class TransportSchedule` с полями
```
- type (можно создать дополнительно enum: bus, trolleybus, shuttle_taxi или тип String)
- route (маршрут типа String)
- time (время прибытия LocalTime)
```
2. Создадим массив для хранения времен прибытия с размером в 10 элементов (максимальное количество строк информационного табло)
и счетчик для итерирования по этому массиву с начальным значением 0
```
TransportSchedule [] schedule = new TransportSchedule[10]; 
int counter = 0;
```
3. Создадим объект `Scanner` и цикл для заполнения массива `schedule`
```
Scanner scanner = new Scanner(System.in);
while (true) {
    System.out.println("Введите через пробел тип транспорта, номер маршрута и время прибытия в формате (hh:MM)");
    System.out.println("end для выхода из программы");
    String type = scanner.next();
    if ("end".equals(type) || counter == 10) {
        System.out.println("Программа завершена.");
        break;
    }
    ...
}
Если type = end выходим из программы, иначе продолжаем ввод значений
``` 
4. Заполняем поля `route` и `time`
```
    String route = scanner.next();
    LocalTime time = LocalTime.parse(scanner.next());
    TransportSchedule transportSchedule = new TransportSchedule(route, time, type);
    schedule[counter] = transportSchedule;
    counter++; //увеличим счетчик для заполения следующей ячейки массива
``` 
5. Вычитаем все значения из объекта scanner, чтоб не оставалось символов переноса каретки
```
    scanner.nextLine(); 
    System.out.println("");
```    
6. Отсортируем массив, используем интервалы так как еще не весь массив заполнен и мы получим NullPointerException.
```
    Arrays.sort(schedule, 0, counter);
```    
7. Выведем заполненные ячейки массива (нарисуем информационное табло)
```
    System.out.println("Тип транспорта --- Маршрут --- Время прибытия");
    for (int i = 0; i < counter; i++) {
        System.out.printf("%14s %11s %18s\n", schedule[i].getType(), schedule[i].getRoute(), schedule[i].getTime());
    }
    System.out.println("");
```
6. Выйдем из цикла и завершим работу программы.
