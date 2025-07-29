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
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">В меню загрузчика на первом уровне выберем второй пункт (Advanced options…), далее загрузим пункт меню с указанием recovery mode в названии:</span></p>
<img width="620" height="221" alt="image" src="https://github.com/user-attachments/assets/c6a8b7db-1c1c-4323-a477-4f70b9fe3956" />
<img width="620" height="221" alt="image" src="https://github.com/user-attachments/assets/6008475c-fc33-4d0c-8761-a68eeb465928" />
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">включаем поддержку сети (network):</span></p>
<img width="657" height="290" alt="image" src="https://github.com/user-attachments/assets/2a2dcba4-5edd-4cc5-b43d-a1afee4a95a3" />
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Далее выбираем пункт root, вводим пароль и попадаем в консоль:</span></p>
<img width="694" height="403" alt="image" src="https://github.com/user-attachments/assets/79ef56af-215d-41fa-8272-2e52184fb7c2" />
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">3) Установить систему с LVM, после чего переименовать VG</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">У нас установлена система с использованием LVM. </span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Посмотрим текущее состояние системы:</span></p>
<p>root@training:~# vgs<br /> VG #PV #LV #SN Attr VSize VFree<br /> ubuntu-vg 1 1 0 wz--n- &lt;23,00g 0 <br />root@training:~# </p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">VG называется ubuntu-vg. Переименуем ее:</span></p>
<p>root@training:~# vgrename ubuntu-vg ubuntu-training<br /> Volume group "ubuntu-vg" successfully renamed to "ubuntu-training"<br />root@training:~#</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Далее в /boot/grub/grub.cfg меняем старое название VG на новое:</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">root@training:~# nano /boot/grub/grub.cfg</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Нажимаем Ctrl+\ (замена) и меняем ubuntu--vg на ubuntu--training</span></p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Произведено 3 замены:</span></p>
<img width="807" height="184" alt="image" src="https://github.com/user-attachments/assets/de013450-8103-42ab-b597-0b40e162de41" />
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Перезагружаем систему и проверяем:</span></p>
<p>root@training:~# vgs<br /> VG #PV #LV #SN Attr VSize VFree<br /> ubuntu-training 1 1 0 wz--n- &lt;23,00g 0 <br />root@training:~#</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">VG успешно переименована.</span></p>
<p style="line-height: 100%; margin-bottom: 0cm;">&nbsp;</p>
<p style="line-height: 108%; margin-bottom: 0.28cm;" align="justify"><span style="font-family: Roboto, serif;">Задание завершено.</span></p>
