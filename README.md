# Лабораторна робота №3. Дослідження засобів мережного рівня моделі OSI. Статичне та динамічне налаштування ІР адресації

## Тестове оточення

| Параметр | Значення |
|---|---|
| ОС | Ubuntu 24.04 LTS, дві віртуальні машини VirtualBox 7.2 |
| server | enp0s8: статична IP 10.0.0.1/8, ISC DHCP Server 4.4.3-P1; enp0s3: NAT |
| client | enp0s3: динамічна IP 10.0.0.10/8 (DHCP), MAC 08:00:27:2d:4d:bf |
| Мережа | VirtualBox Internal Network `intnet`, 10.0.0.0/8, пул 10.0.0.10–10.0.0.20 |
| Інструменти | Wireshark 4.6.9, dhclient, dhcpd -t, ping, traceroute, ip route |

## Defect reports

| ID | Опис | Серйозність | Статус | Файл захоплення |
|---|---|---|---|---|
| DR-01 | `subnet 10.0.0.0 netmask 0.0.0.255`: сервер не запускається (bad subnet number/mask combination) | Critical | Verified | `defect1_bad_netmask.pcapng` |
| DR-02 | `option subnet-mask 255.255.255.248`: клієнт отримує /29 і втрачає зв'язок зі шлюзом | Major | Verified | `defect2_wrong_mask_option.pcapng` |

## Файли

- `ЛР3_Павлюк_ІА-32.docx` / `.pdf`: звіт (теорія, хід роботи зі знімками екрана, defect reports, висновки)
- `dhcpd.conf.good`: робоча конфігурація DHCP-сервера
- `dhcp_dora.pcapng`: обмін DHCPDISCOVER → OFFER → REQUEST → ACK і DHCPRELEASE (фільтр Wireshark: `dhcp`)
