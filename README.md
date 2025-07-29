# adm_training_task7
<h1 align="center">Занятие 7. Работа с загрузчиком</h1>
<h3 class="western"><a name="_heading=h.h6i87lkp3f19"></a> <span style="font-family: Roboto, serif;"><span style="font-size: small;">Описание домашнего задания</span></h3>
<p style="line-height: 100%; margin-bottom: 0cm;"><span style="font-family: Roboto, serif;">1) Включить отображение меню Grub</span></p>
<p style="line-height: 100%; margin-bottom: 0cm;"><span style="font-family: Roboto, serif;">2) Попасть в систему без пароля несколькими способами</span></p>
<p style="line-height: 100%; margin-bottom: 0cm;"><span style="font-family: Roboto, serif;">3) Установить систему с LVM, после чего переименовать VG</span></p>
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<h3 class="western"><a name="_heading=h.df570rpzx1qg"></a><span style="font-family: Roboto, serif;"><span style="font-size: small;">Используемые ОС</span></h3>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Хостовая ОС Ubuntu 24.04 Desktop. Гостевая ОС Ubuntu 24.04 Desktop. VirtualBox версия 7.0.16_Ubuntu r162802</span></p>
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<h3 class="western"><span style="font-family: Roboto, serif;"><span style="font-size: small;">Выполнение</span></span></h3>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">1) Включить отображение меню Grub</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Вначале отключим задержку при загрузке. Открываем конфигурационный файл загрузчика /etc/default/grub:</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">root@training:~# nano /etc/default/grub</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Комментируем строку, скрывающую меню:</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">#GRUB_TIMEOUT_STYLE=hidden</span></p>
  <p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Ставим время отображения меню 10 секунд:</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">GRUB_TIMEOUT=10</span></p>
<img width="817" height="330" alt="image" src="https://github.com/user-attachments/assets/c6ed4178-6a4f-4a73-b900-96cda23395db" />
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Сохраняем, обновляем конфигурацию загрузчика:</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">root@training:~# update-grub</span></p>
<img width="780" height="294" alt="image" src="https://github.com/user-attachments/assets/3ee1e653-cdee-4252-844a-878364a4bddf" />
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
  <p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Перезагружаем ВМ:</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">root@training:~# reboot</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">При запуске видим меню загрузчика:</span></p>
<img width="630" height="451" alt="image" src="https://github.com/user-attachments/assets/893ada08-9e76-43a1-88b5-2ae853b4bc0c" />
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">2) Попасть в систему без пароля несколькими способами</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Способ 1. init=/bin/bash</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">В меню загрузчика нажимаем 'e' (edit)</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Система установлена с использованием LVM (условие задания). В строке параметров загрузки ядра добавляем init=/bin/bash (запуск командной строки). Нажимаем сtrl-x или F10 для загрузки в систему</span></p>
<img width="624" height="451" alt="image" src="https://github.com/user-attachments/assets/97e3c232-132d-4d8c-a804-65f8a5aa17ab" />
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Перемонтируем файловую систему в режим Read-Write:</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">mount -o remount,rw /</span></p>
<img width="723" height="440" alt="image" src="https://github.com/user-attachments/assets/cdb82797-5c9a-46ce-a49c-232c5c55d67a" />
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Видим, что файловая система доступна для записи.</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Способ 2. Recovery mode</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">ТЕКСТ</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">ТЕКСТ</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">ТЕКСТ</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">ТЕКСТ</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">ТЕКСТ</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">ТЕКСТ</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">ТЕКСТ</span></p>
