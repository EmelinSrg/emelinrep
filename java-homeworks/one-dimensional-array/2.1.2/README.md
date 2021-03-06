# Домашнее задание к занятию 2.1 Массивы одномерные
## Задача 2. Сортировка массива вручную

### Описание
Вы пишете программу анализа цен в интернете. Ваш анализатор получил "сырой" список товаров. Вам необходимо отсортировать этот список в порядке увеличения цен. Массив на вход — массив объектов, типа "Продукт" с полями "Имя, цена, описание". Массив на выход — отсортированный по возрастанию цены массив продуктов. Нужно учесть, что: 
* массив на вход может быть очень большим, а значит, алгоритм ручной сортировки должен быть эффективнее, чем "сортировка пузырьком";
* цены могут совпадать.

### Функционал программы
1. Создание массива и заполнение его продуктами;
2. Сортировка входного массива по возрастанию цены (сортировка на выбор);
2. Вывод отсортированного массива.

### Дополнительная информация 
Изучите  готовые решения от Java. Будет полезно узнать, какой алгоритм сортировки использует Java и почему. Для практики примените Comparator и передайте массив вместе с компаратором методу сортировки (также можно использовать Comparable интерфейс в классе).

Полезные ссылки:
	[Comparator](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html),
	[Arrays.sort](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#sort%28T%5B%5D,%20java.util.Comparator%29),
	[Comparable](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html).

### Пример реализации
1. Создаем объект для продуктов. 
 ```
public class Product {
    public String name;
    public int price;
    public String description;

    public Product(int price, String name, String description) {
       this.name = name;
       this.price = price;
       this.description = description;
    }
 }
 ```
2. Пишем метод сортировки, который при входе получает список продуктов (массив объектов, типа "Продукт").
```
mySort(Product[] products)
```
3. Пишем алгоритм сортировки. Можно выбрать один из известных алгоритмов, например:

``` Merge Sort, Quick Sort ```

... или создать самому.
Просмотрите все возможные алгоритмы сортировки, выберите один из них. 
Напишите метод ```mySort(Product[] products)``` по выбранному алгоритму.
