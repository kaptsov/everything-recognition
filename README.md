## Распознавание предметов при помощи компьютерного зрения

Скрипт реализует распознавание объектов с WEB-камеры компьютера.

Для этого используются XML таблицы, в которых содержатся характерные для объектов контрольные точки, "признаки", записанные во время "обучения с учителем".

Метод обучения называется [Каскады Хаара](https://habr.com/ru/post/208092/).

## Установка

Для работы необходима установленная версия `python3`. Для добавления требуемых зависимостей используйте `pip` (или `pip3` при конфликтах с `python2`) - выполните команду:
```
pip install -r requrements.txt
```

## Использование

Введите в терминале:
```
python run.py
```
Откроется окно программы, в котором вы увидите изображение с подключенной web-камеры. При отсутствии web-камеры скрипт выдаст сообщение в консоль: **"Couldn't find your webcam... Sorry :c"**
В зависимости от настроек конфигурации(которые задаются в файле `config.py`) распознанные объекты будут выделяться прямогугольной рамкой определенного настройками цвета.
Для выхода из программы необходимо нажать клавишу `q` на клавиатуре.

## Конфигурирование

В файле `config.py` задаются объекты для распознавания камерой, выбирается RGB цвет рамки(переменная `color`), и ключом `draw` `True` и `Flase` выбирается видимость рамок.
Так же, в переменную `path` записывают путь к папке с XML таблицей с признаками по Хаару.
С помощью данного скрипта XML таблицы создавать нельзя.

## Описание run.py

**if __name__ == "__main__"**

Основная функция, в которой включается камера, и работает бесконечный цикл распознавания объектов с камеры и рисование рамок по распознанным координатам.
В каждом цикле проверяется нажатие кнопки **q** для выхода из скрипта.

**get_cascades**

Подгружает каскад из XML файла и определяет параметры рамки для рисования.

**draw_sqare**

Рисует в текущем видеокадре рамку по параметрам и координатам.

**show_frame**

Выводит текущий видеокадр с нарисованными рамками на экран.

**is_user_wants_quit**

Проверяет нажата ли кнопка **q** для выхода.