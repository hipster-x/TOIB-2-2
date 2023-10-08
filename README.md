# TOIB-2 PR
# Отчет по зданию №2 "Идентификация и аутентификация"
Задача 
1. Создать виртуальную машину на базе ОС Debian 12 https://www.virtualbox.org/wiki/Downloads
https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-12.1.0-amd64-netinst.iso
2. Создать пользователя super-{ФИО}, наделить его привилегиями суперпользователя
3. Зайти под созданным пользователем и создать группу group-{группа}
4. Добавить пользователя super-{ФИО} в группу group-{группа}
5. Продемонстрировать наличие пользователя в группе
6. Создать пользователя user-{ФИО}, добавить его в группу group-{группа}
7. Наделить полномочиями (с использованием механизмов дискреционного управления
доступом chmod) пользователя user-{ФИО} по созданию и удалению файлов в домашнем
каталоге пользователя super-{ФИО}
8. Продемонстрировать работу механизмов разграничения доступа.
# Шаги выполнения 
1 Шаг ![Desktop Screenshot 2023 10 08 - 14 32 11 24](https://github.com/hipster-x/TOIB-2-2/assets/145153023/6f17d372-9587-4157-81ef-ee650684aa8d)

2 Шаг

evdokimov@10:~$ su

Password: 

root@10:/home/evdokimov# sudo useradd super-{EvdokimovAM}

root@10:/home/evdokimov# passwd super-{EvdokimovAM}

New password: 

Retype new password: 

passwd: password updated successfully

root@10:/home/evdokimov# usermod -aG sudo super-{EvdpkimovAM}

bash: usermod: command not found

root@10:/home/evdokimov# sudo usermod -aG sudo super-{EvdokimovAM}

3 Шаг

root@10:/home/evdokimov# sudo groupadd group-{123}

4 Шаг

root@10:/home/evdokimov# usermod -aG group-{123} super-{EvdokimovAM}

5 Шаг

root@10:/home/evdokimov# groups super-{EvdokimovAM}

super-{EvdokimovAM} : super-{EvdokimovAM} sudo group-{123}

6 Шаг

root@10:/home/evdokimov# useradd user-{EvdokimovAM}

root@10:/home/evdokimov# usermod -aG group-{123} user-{EvdokimovAM}

7 Шаг

root@10:/home/evdokimov# chmod 770 /home/super-{EvdokimovAM}

root@10:/home/evdokimov# chown super-{EvdokimovAM}:group-{123} /home/super-{EvdokimovAM}

8 Шаг

root@10:/home/evdokimov# su user-{EvdokimovAM}

touch /home/super-{EvdokimovAM}/test_file.txt

$ rm /home/super-{EvdokimovAM}/test_file.txt

#Bash

![Desktop Screenshot 2023 10 08 - 17 32 05 31](https://github.com/hipster-x/TOIB-2-2/assets/145153023/5b29e76b-ef4b-4f9f-a972-b08a0330c6d8)
