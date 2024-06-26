# Тема 4. Функции и стандартные модули/библиотеки
Отчет по Теме #4 выполнил:
- Ильдейкин Антон Александрович
- ИНО ЗБ ПОАС-22-2

| Задание | Лаб_раб(10) | Сам_раб(5) |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |
| Задание 6 | + |  |
| Задание 7 | + |  |
| Задание 8 | + |  |
| Задание 9 | + |  |
| Задание 10 | + |  |


Работу проверили:
- к.э.н., доцент Панов М.А.
## Самостоятельная работа №1
### Дайте подробный коментарий для кода. Коментарий нужен для каждой строчки кода, что она делает.

```python
from datetime import datetime #импорт модуля для работы с временем
from math import sqrt         #функция sqrt нужнo для вычисления квадратного корня


def main(**kwargs):             #опеределяем фунцию main
    for key in kwargs.items():  #перебираем ключи в словаре kwargs
        result = sqrt(key[1][0] ** 2 + key[1][1] ** 2) #вычисляем квадратный корень из координат
        print(result)           #выводим результат


if __name__=='__main__': # модуль импортируется в другой скрипт и присваивает имя main
    start_time = datetime.now() #записываем текущее время в переменную
    main(                #вызов функции с заданными аргументами
        one=[10, 3],
        two=[5, 4],
        three=[15, 13],   # координаты - 1,2,3,4,5 
        four=[93, 53],
        five=[133, 15],
    )
    time_costs = datetime.now() - start_time #вычисление времени программы
    print(f"Время выполнения программы - {time_costs}") #вывод в консоль времени выполнения программы
```
### Результат:
![Меню](https://github.com/Dirtzzz/Tema_4/blob/main/4.1.png)

## Самостоятельная работа №2
### Напишите программу, которая будет заменять игральную кость с 6 гранями. Если значение равно 5 или 6, то в консоль выводится «Вы победили», если значения 3 или 4, то вы рекурсивно должны вызвать эту же функцию, если значение 1 или 2, то в консоль выводится «Вы проиграли». При этом каждый вызов функции необходимо выводить в консоль значение "кубика". Для выполнения задания необходимо использовать стандартную библиотеку random. Программу нужно написать, используя одну функцию и "точку входа"

```python
import random

def roll_dice(side):
    print(f"Выпало значение: {side}")
    if side == 5 or side == 6:
        print("Вы победили")
    elif side == 3 or side == 4:
        roll_dice(random.randint(1, 6))
    else:
        print("Вы проиграли")

if __name__ == "__main__":
    roll_dice(random.randint(1, 6))
```

### Результат:
![Меню](https://github.com/Dirtzzz/Tema_4/blob/main/4.2.png)

## Самостоятельная работа 3
### Напишите программу, которая будет выводить текущее время, с точностью до секунд на протяжении 5 секунд. Программу нужно написать с использованием цикла. Подсказка: необходимо использовать модуль datetime и time, а также вам необходимо как-то "усыплять" программу на 1 секунду.

```python
import datetime
import time

def print_current_time():
    now = datetime.datetime.now()
    current_time = now.strftime("%H:%M:%S")
    print(current_time)

for i in range(5):
    print_current_time()
    time.sleep(1)         # "Усыпляем" программу на 1 секунду
```

### Результат:
![Меню](https://github.com/Dirtzzz/Tema_4/blob/main/4.3.png)

## Самостоятельная работа 4
### Напишите программу, которая считает среднее арифметическое от аргументов вызываемое функции, с условием того, что изначальное количество этих аргументов неизвестно. Программу необходимо реализовать используя одну функцию и "точку входа".

```python
def calculate_average(*args):

    total = sum(args) 
    count = len(args)
    return total / count

if __name__ == "__main__":
    args = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    average = calculate_average(*args)
    print(f"Среднее арифметическое: {average}")
```

### Результат:
![Меню](https://github.com/Dirtzzz/Tema_4/blob/main/4.4.png)

## Самостоятельная работа 5
### Создайте два Python файла, в одном будет выполняться вычисление площади треугольника при помощи формулы Герона (необходимо реализовать через функцию), а во втором будет происходить взаимодействие с пользователем (получение всей необходимой информации и вывод результатов). Напишите эту программу и выведите в консоль полученную площадь.
1 файл ploshadi.py
```python
import math
def heron_ploshadi(a, b, c):
    s = (a + b + c) / 2
    area = math.sqrt(s * (s - a) * (s - b) * (s - c))
    return area
if __name__ == "__main__":
    pass
```
2 файл user.py
```python
import ploshadi
def get_user_input():

    a = float(input("Введите длину стороны a: "))
    b = float(input("Введите длину стороны b: "))
    c = float(input("Введите длину стороны c: "))
    return a, b, c

def print_results(area):
    print(f"Площадь треугольника: {area}")
if __name__ == "__main__":
    a, b, c = get_user_input()
    area = ploshadi.heron_ploshadi(a, b, c)
    print_results(area)
```
### Результат:
![Меню](https://github.com/Dirtzzz/Tema_4/blob/main/4.5%20ploshadi.png)
![Меню](https://github.com/Dirtzzz/Tema_4/blob/main/4.5%20user.png)

