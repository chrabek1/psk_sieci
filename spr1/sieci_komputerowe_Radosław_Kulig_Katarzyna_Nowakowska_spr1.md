# Politechnika Świętokrzyska w Kielcach
## Wydział Zarządzania i Modelowania Komputerowego
##### Sieci Komputerowe
##### Laboratorium
#### Podstawowa konfiguracja przełącznika i urządzenia końcowego
![](https://tu.kielce.pl/wp-content/uploads/2018/03/logo_psk.jpg)
Przygotowali: 
| Imię i Nazwisko     | Nr albumu| 
| -------------- | ------- |
| Radosław Kulig | 093795 |
| Katarzyna Nowakowska | 096946 |  
  
Kierunek: Inżynieria Danych

Studia: stacjonarne

Data wykonania ćwiczenia: 22.10.2025

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

Za pomocą kabla konsolowego łączymy komputery ze swoich stanowisk z przełącznikami.  
![kabel konsolowy](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kabel_konsolowy.jpg?raw=true)  
Po nawiązaniu połączenia konsolowego z przełącznikiem, przechodzimy do trybu konfiguracji globalnej i nadajemy przełącznikom odpowiednie nazwy(S3-Katarzyna Nowakowska ; S4-Radosław Kulig) oraz wprowadzamy lokalne hasła (cisco i class)

![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/a%20i%20d.jpg?raw=true)  

Zaby zapobiec niepożądanym zapytaniom DNS wpisujemy komendę `no ip domain lookup`

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
![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/j2.jpg?raw=true)  

## Konfiguracja komputerów PC
Konfigurujemy informacje statycznego adresu IP na komputerach PC zgodnie z tabelą adresowania.
![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/ip.jpg?raw=true)

## Topologia sieci
Gdy mamy skonfigurowane zarówno przełączniki jak i komputery PC odtwarzamy topologię sieci.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr1/topologia.png?raw=true)  
Za pomocą kabli ethernet łączymy ze sobą przełączniki, a następni przełączniki łączymy z odpowiednimi komputerami odwzorowując topologie przedstawioną na schemacie.
![rj45](https://github.com/chrabek1/psk_sieci/blob/main/spr1/rj45.webp?raw=true)

## Pingi
Z komputera PC1 pingujemy S1

![pingS1](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/pingS1.jpeg?raw=true)  
Pierwszy pakiet z reguły jest tracony przy pierwszej próbie pingu.  
Następnie pingujemy S2  
![pingS2](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/pingS2.jpeg?raw=true)  
Ping na PC2  
![pingPC2](https://github.com/chrabek1/psk_sieci/blob/main/spr1/kasia/pingPC2.jpeg?raw=true)  

## Tabela statusów interfejsów
Sprawdzenie statusu interfejsów za pomocą komendy `show ip interface brief` mogliśmy wykonać tylko w momencie konfiguracji przekaźników
,gdy byliśmy podłączeni z nimi kablami konsolowymi(bez odtworzonej topologii sieci), więc włączony status miały jedynie intefejsy `F0/1` i `VLAN 1`  
| Interfejs | S1 Status | S1 Protocol | S2 Status | S1 Protocol | 
| --------- | --------- | ----------- | --------- | ----------- |
| F0/1 | up | up | up | up 
| F0/6 | down | down | down | down |
| F0/18 | down | down | down | down |
| VLAN 1 | up | up | up | up |

Jednak za pomocą narzędzia dedukcji jesteśmy w stanie przewidzieć że z odtworzoną topologią siecii ta tabela powinna prezentować się następująco: 
| Interfejs | S1 Status | S1 Protocol | S2 Status | S1 Protocol | 
| --------- | --------- | ----------- | --------- | ----------- |
| F0/1 | up | up | up | up |
| F0/6 | up | up | down | down |
| F0/18 | down | down | up | up |
| VLAN 1 | up | up | up | up | up |

## Pytanie do przemyślenia  
**Dlaczego niektóre porty FastEthernet na przełącznikach są włączone, a inne wyłączone?**  
Porty FastEthernet na przełącznikach są włączone kiedy są do nich podłączone aktywne urządzenia sieciowe. W naszym ćwiczeniu portami F0/1 są połączone ze sobą przełączniki, portem F0/6 jest podłączony PC1 z S1, a portem F0/18 PC2 z S1. Dlatego te porty są włączone, a wszystkie inne nie.  
  
**Co może uniemożliwić przesłanie żądania ping pomiędzy komputerami?**  
Brak odpowiedzi na ping może być spowodowany m.in. przez:

- błędną konfigurację adresów IP lub masek podsieci na komputerach

- brak konfiguracji interfejsu VLAN 1 na przełączniku lub jego wyłączenie

- niepołączone lub uszkodzone kable sieciowe

- porty przełącznika w stanie „administratively down” (wyłączone poleceniem shutdown)

- błędną konfigurację VLAN (urządzenia w różnych VLAN-ach bez routingu)

- zaporę sieciową (firewall) blokującą odpowiedzi ICMP na komputerze
