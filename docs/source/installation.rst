Установка
=========

.. _installation:

XAMPP
------

Кроссплатформенная сборка локального веб-сервера, содержащая:
- Apache;
- MariaDB;
- интерпретатор скриптов PHP

Скачиваем XAMPP for Linux с официального сайта https://www.apachefriends.org/

.. image:: /_static/выбор_xampp.png
   :alt: выбор xampp
   :width: 700

Далее вводим команды в терминале от root (для переключения ввести su). Открываем терминал в папке, куда был скачан файл xampp-linux-x64-8.2.12-0-installer.run. Передаем права для запуска файла и запускаем его

.. code-block:: console

   $ chmod +x xampp-linux-x64-8.2.12-0-installer.run
   $ ./xampp-linux-x64-8.2.12-0-installer.run

.. image:: /_static/установка.png
   :alt: установка
   :width: 700

Выбираем далее и не запускаем xampp

.. image:: /_static/xampp.png
   :alt: xampp
   :width: 700

Переходим в папку, где установлен xampp и запускаем его 

.. code-block:: console

   $ /opt/lampp/lampp start
   $ dnf install libxcrypt-compat
   $ dnf install libnsl
   $ /opt/lampp/lampp start

.. image:: /_static/библиотеки.png
   :alt: библиотеки
   :width: 700
.. image:: /_static/библиотеки_2.png
   :alt: библиотеки
   :width: 700
.. image:: /_static/xampp_запущен.png
   :alt: библиотеки
   :width: 700

WordPress
----------

Для установки необходимо скачать с сайта https://ru.wordpress.org/download/ 

.. image:: /_static/скачать_wordoress.png
   :alt: скачать_wordoress
   :width: 700

Удаляем папку htdocs с ее содержимым и создаем заново 

.. code-block:: console

   $ rm -fr htdocs/
   $ mkdir htdocs/

Необходимо распаковать файл и переместить содержимое папки в /opt/lampp/htdocs/

.. code-block:: console

   $ unzip wordpress-6.5.2-ru_RU.zip
   $ cp -a /home/rexam/Загрузки/wordpress/. /opt/lampp/htdocs/

.. image:: /_static/распаковка.png
   :alt: распаковка
   :width: 700

Вбиваем localhost в браузер и нас встречает окно приветствия

.. image:: /_static/приветствие.png
   :alt: приветствие
   :width: 700

Далее создаем базу данных wp в http://localhost/phpmyadmin/

.. image:: /_static/phpmyadmin.png
   :alt: phpmyadmin
   :width: 700

По умолчанию логин на phpmyadmin root, пароля нет

.. image:: /_static/подключениеБД.png
   :alt: подключениеБД
   :width: 700

И создаем файл с настройками

.. code-block:: console

   $ pluma wp-config.php

.. image:: /_static/файлнастроек.png
   :alt: файлнастроек
   :width: 700

Указываем название сайта и создаем суперадмина 

.. image:: /_static/создание_сайта.png
   :alt: создание_сайта
   :width: 700
.. image:: /_static/поздравляем.png
   :alt: споздравляем
   :width: 700
.. image:: /_static/главное_окно.png
   :alt: главное_окно
   :width: 700

Чтобы был доступ к редактированию файлов на ПК, передаем права на папку daemon

.. code-block:: console

   $ chmod -R 777 htdocs/
   $ chown -R daemon:daemon htdocs/

.. image:: /_static/ftp.png
   :alt: ftp
   :width: 700
