FastAPI
=========

Для работы с документами нам нужен python, рассмотрим один из фреймворков: FastAPI. Работать будем в Visual Studio Code с расширением Python. 

Установка и запуск
-------------------

Создаем папку в домашнем каталоге с названием проекта.

 .. note::
   Название и расположение можно выбирать свои, однако внимательно переименовывайте дальше по инструкции проекты

Создана папка /home/rexam/trading_app и открыта в Visual Studio Code. Подключено виртульное окружение venv для установки библиотек


.. image:: /_static/vs01api.png
   :alt: vs01api
   :width: 700

Внизу справа нажав на номер верии мы можем выбирать окружение и через кнопку запуска увидим в терминале, что папка появилась

.. image:: /_static/venv.png
   :alt: venv
   :width: 700

Для установки всех библиотек пропишем команду:

.. code-block:: console

pip install fastapi[all]

Далее создадим файл main.py и в него вставим код ниже 

.. code-block:: Python

# подключаем фреймворк FastAPI
from fastapi import FastAPI

# создаем наше приложение. Слово app можно заменить налюбое другое
app = FastAPI()

# прописываем метод get: при загрузке сайта на главной странице / пользователь получит
@app.get("/")
# эту функцию, которая просто выводит текст
def get_check_work():
    return "Фреймворк FastAPI успешно установлен!"
 
Для запуск в терминале напишем

.. code-block:: console

uvicorn main:app --reload

.. image:: /_static/hello.png
   :alt: hello
   :width: 700

.. autosummary::
   :toctree: generated

   lumache

