# test
практика

Подготовка
   Для проведения тестов подготовим виртуальную машину VirtualBox на Windows 10 [Version 10.0.19045.4291]
   ![image](https://github.com/user-attachments/assets/32a5fd1d-b769-4284-8b78-272c2e5625e9)
   
   ![image](https://github.com/user-attachments/assets/5096d945-8df8-4b43-8864-996ee3b8e23e)

   

Часть 1. Сканирование виртуальной машины на windows10 без файрвола

1. Сканируем локальную сеть
   ip adress
   ![изображение](https://github.com/user-attachments/assets/b4efcfd6-c678-4af1-aa1b-3e4ee576b78e)

   netdiscover -r 192.168.1.0/24
   ![изображение](https://github.com/user-attachments/assets/2e5e2e9d-d0e8-4e04-8334-2e3382266336)

   nmap -A -sV -oN nmapscan.txt 192.168.1.41
   
   nmap -A -sV -oN nmapscanvulners.txt --script vulners 192.168.1.41
3. 

4. Сканер уязвимостей Сканер-ВС 6
   Сканирование портов
  ![изображение](https://github.com/user-attachments/assets/71c2beb0-9cf2-4431-88f5-f473d209cf0c)

  Сканирование на уязвимости
  ![изображение](https://github.com/user-attachments/assets/5f132123-38f9-40bb-8647-a865bb7fb13c)

  ![изображение](https://github.com/user-attachments/assets/ea2488b0-5d99-4074-ac01-aa29355b1cca)
  ![изображение](https://github.com/user-attachments/assets/385ffec2-aee3-4acd-b3be-cdf80c07835d)

Уязвимость в протоколе HTTP/2
CVE-2023-44487
Уязвимость заключается в обработке мультиплексированных потоков в протоколе HTTP/2. Клиент может многократно запрашивать новый мультиплексный поток и сразу отправлять фрейм RST_STREAM для его отмены. Это создает дополнительные затраты для сервера на установление и закрытие потоков, при этом не достигая лимита сервера по максимальному количеству активных потоков на соединение, что приводит к отказу в обслуживании из-за потребления ресурсов сервера. Атаки могут осуществляться сравнительно небольшими ботнетами, состоящими примерно из 20 000 устройств.

Эксплуатация:
Уязвимость позволяет удаленному злоумышленнику вызвать отказ в обслуживании.

3. Сканер уязвимостей Nessus
![изображение](https://github.com/user-attachments/assets/6c7f28a7-65cc-425a-8c95-f40f39cff102)

![изображение](https://github.com/user-attachments/assets/58e6ae1d-7c76-43cd-af74-389d3fe38cf7)


![изображение](https://github.com/user-attachments/assets/f99e7d8f-e52a-4578-855c-a10ae3737a2a)

Подпись SMB не требуется
Описание
Подписание на удаленном SMB-сервере не требуется. Удаленный злоумышленник, не прошедший проверку подлинности, может использовать это для проведения атак «человек посередине» на SMB-сервер.
Решение
Обеспечьте подписание сообщений в конфигурации хоста. В Windows это можно найти в параметре политики «Сетевой сервер Microsoft: использовать цифровую подпись (всегда)». В Samba этот параметр называется «подпись сервера». Дополнительную информацию см. по ссылкам «см. также».



![изображение](https://github.com/user-attachments/assets/9e5d3d45-e264-4762-9cf8-4827c0ffcc70)

Запрос метки времени ICMP Удаленное раскрытие даты
Описание
Удаленный хост отвечает на запрос метки времени ICMP. Это позволяет злоумышленнику узнать дату, установленную на целевой машине, что может помочь удаленному злоумышленнику, не прошедшему аутентификацию, обойти протоколы аутентификации, основанные на времени.

Временные метки, возвращаемые с компьютеров под управлением Windows Vista/7/2008/2008 R2, намеренно неверны, но обычно они отстают от фактического системного времени в пределах 1000 секунд.
Решение
Отфильтруйте запросы меток времени ICMP (13) и исходящие ответы меток времени ICMP (14).


![изображение](https://github.com/user-attachments/assets/eed43b7a-e564-4680-b687-3eecb8e2a135)

Описание
Этот плагин представляет собой «полуоткрытый» сканер портов SYN. Он должен быть достаточно быстрым даже против цели, защищенной брандмауэром.

Обратите внимание, что сканирование SYN менее интрузивно, чем сканирование TCP (полное подключение) в отношении сломанных служб, но оно может вызвать проблемы для менее надежных межсетевых экранов, а также оставить незакрытые соединения на удаленной цели, если сеть загружена.
Решение
Защитите свою цель с помощью IP-фильтра.

