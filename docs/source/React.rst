React
======

.. note::
  Node.js — это серверная платформа, поддерживающая выполнение JavaScript-кода, возможности которой пригодятся нам для React-разработки.

Если эта платформа ещё у вас не установлена — сейчас самое время это исправить.

.. code-block:: console
  
  dnf install npm -y

Если предлагает установить другую версию, не забываем очистить кеш и ключ --force Пример

.. code-block:: console
  
  npm cache clear --force
  npm install -g npm@10.8.2 --force
  npm install -g npx --force

Для создания основы React-приложения, будем использовать пакет create-react-app от Facebook. Благодаря create-react-app программист получает в своё распоряжение множество нужных инструментов, что избавляет его от необходимости самостоятельно их подбирать.
Для того чтобы установить create-react-app, воспользуйтесь такой командой:

.. code-block:: console
  
  npx create-react-app my_app

На этом предварительная подготовка закончена. Для запуска приложения выполните следующие команды:

.. code-block:: console  
  
  cd react-intro
  npm start

Тут мы переходим в папку проекта и запускаем сервер разработки, который позволяет открыть новое React-приложение, перейдя в браузере по адресу http://localhost:3000/.

.. image:: /_static/react.png
   :alt: react
   :width: 700

.. autosummary::
   :toctree: generated

   lumache
