# Politechnika Świętokrzyska w Kielcach
## Wydział Zarządzania i Modelowania Komputerowego
##### Sieci Komputerowe
##### Laboratorium
#### Podstawowa konfiguracja przełącznika i urządzenia końcowego
![](https://tu.kielce.pl/wp-content/uploads/2018/03/logo_psk.jpg)
Przygotowali: 
| Imię i Nazwisko     | Nr albumu| 
| -------------- | ------- |
| Radosław Kulig | 09375 |
| Katarzyna Nowakowska | |
|Data wykonania ćwiczenia | 22.10.2025|


Kierunek: Inżynieria Danych

Studia: stacjonarne

*Oświadczam, że:*

*Sprawozdanie niniejsze zostało wykonane przeze mnie osobiście. Zamieszczone w sprawozdaniu wyniki badań zostały uzyskane przeze mnie podczas wykonywania zadań laboratoryjnych.*  
*Radosław Kulig*  
*Katarzyna Nowakowska*  
***

## Wstęp teoretyczny

Przełączniki (ang. switches) stanowią kluczowy element sieci lokalnych (LAN), odpowiadając za przesyłanie ramek danych pomiędzy urządzeniami końcowymi w obrębie jednej sieci. Ich głównym zadaniem jest efektywne kierowanie ruchem w warstwie drugiej modelu OSI, na podstawie adresów MAC. W przeciwieństwie do koncentratorów (hubów), przełączniki analizują tablicę adresów MAC, co pozwala im na przesyłanie ramek tylko do właściwego odbiorcy, minimalizując kolizje i zwiększając przepustowość sieci.

Podstawowa konfiguracja przełącznika obejmuje m.in. nadanie nazwy urządzeniu, ustawienie haseł dostępu, konfigurację interfejsu VLAN 1, przypisanie adresu IP, a także ustawienie banera ostrzegawczego (MOTD). Te czynności są niezbędne, aby zapewnić bezpieczeństwo, ułatwić zarządzanie urządzeniem oraz umożliwić zdalny dostęp administracyjny. Ważnym elementem jest również zapisanie konfiguracji w pamięci NVRAM, aby zachować ustawienia po restarcie urządzenia.

Urządzenia końcowe, takie jak komputery PC, muszą zostać odpowiednio skonfigurowane z adresem IP, maską podsieci i bramą domyślną, aby mogły komunikować się z przełącznikami i innymi hostami w sieci. Poprawność konfiguracji można zweryfikować przy pomocy narzędzia ping, które służy do testowania łączności sieciowej.

W ćwiczeniu tym wykorzystano sprzęt Cisco Catalyst 2960 z systemem operacyjnym Cisco IOS. W ramach laboratorium uczestnik poznaje podstawy pracy w trybie CLI (Command Line Interface) urządzeń Cisco oraz utrwala umiejętność konfiguracji i diagnostyki podstawowych połączeń sieciowych.

## Konfiguracja i weryfikacja podstawowych ustawień przełączników

Po nawiązaniu połączenia konsolowego z przełącznikiem, przechodzimy do trybu konfiguracji globalnej i nadajemy przełącznikom odpowiednie nazwy(S3-Katarzyna Nowakowska ; S4-Radosław Kulig) oraz wprowadzamy lokalne hasła (cisco i class)

![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/a%20i%20d.jpg?raw=true)

Skonfigurowaliśmy i włączyliśmy SVI zgodnie z tabelą adresowania oraz wprowadzamy baner logowania MOTD, aby ostrzec o nieautoryzowanym dostępie 

![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/f.jpeg?raw=true)

Wprowadzoną konfiguracje zostawiamy w pamięci podręcznej przełącznika, nie zapisujemy jej do pamięci NVRAM (zgodnie z poleceniem prowadzącego)

Bieżąca konfiguracja: 

![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/h1.jpg?raw=true)
![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/h2.jpg?raw=true)
![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/h3.jpg?raw=true)

Wersja systemu IOS i inne przedatne informacje i przełączniku: 
![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/i.jpg?raw=true)
![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/i2.jpg?raw=true)

Status podłączonych interfejsów przełącznika:
![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/j.jpg?raw=true)
![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/h2.jpg?raw=true)

## Konfiguracja komputerów PC
Konfigurujemy informacje statycznego adresu IP na komputerach PC zgodnie z tabelą adresowania.
![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/ip.jpg?raw=true)

## Topologia cieci
Gdy mamy skonfigurowane zarówno przełączniki jak i komputery PC odtwarzamy topologię sieci.
