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

Эндпоинты, Параметры URL и Запроса
-----------------------------------

Изменим код 

.. code-block:: Python

 from fastapi import FastAPI
 
 app = FastAPI(
     # зададим название приложения
     title="Trading App"
 )
 
 # словарь пользователей
 fake_users = [
     {"id": 1, "role": "admin", "name": "Bob"},
     {"id": 2, "role": "investor", "name": "John"},
     {"id": 3, "role": "trader", "name": "Matt"},
 ]
 
 # получаем пользователя по его id
 @app.get("/users/{user_id}")
 def get_user(user_id: int):
     return [user for user in fake_users if user.get("id") == user_id]

.. image:: /_static/get_id.png
   :alt: get_id
   :width: 700

Добавим функцию

.. code-block:: Python

 # словарь сделок
 fake_trades = [
     {"id": 1, "user_id": 1, "currency": "BTC", "side": "buy", "price": 123, "amount": 2.12},
     {"id": 2, "user_id": 1, "currency": "BTC", "side": "sell", "price": 125, "amount": 2.12},
 ]
 
 # получаем по одной сделке (лимит), начиная с нулевой (офсет)
 @app.get("/trades")
 def get_trades(limit: int = 1, offset: int = 0):
     return fake_trades[offset:][:limit]

.. image:: /_static/get_trade.png
   :alt: get_trade
   :width: 700

И еще одну

.. code-block:: Python

 # словарт пользователей для редактирования
 fake_users2 = [
     {"id": 1, "role": "admin", "name": "Bob"},
     {"id": 2, "role": "investor", "name": "John"},
     {"id": 3, "role": "trader", "name": "Matt"},
 ]
 
 #  запостим изменение имени у заданного по id пользователя
 @app.post("/users/{user_id}")
 def change_user_name(user_id: int, new_name: str):
     current_user = list(filter(lambda user: user.get("id") == user_id, fake_users2))[0]
     current_user["name"] = new_name
     return {"status": 200, "data": current_user}

.. image:: /_static/post_name.png
   :alt: post_name
   :width: 700

.. autosummary::
   :toctree: generated

   lumache

