# Politechnika Świętokrzyska w Kielcach
## Wydział Zarządzania i Modelowania Komputerowego
##### Sieci Komputerowe
##### Laboratorium
#### Konfigurowanie dostępu do urządzeń sieciowych za pomocą SSH 

####
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
## Lab 16.4.7 Odczytywanie adresów MAC urządzeń sieciowych 
### Wstęp teoretyczny
 
Zdalne zarządzanie urządzeniami sieciowymi jest kluczowym elementem administracji sieci komputerowych. W przeszłości powszechnie stosowany protokół Telnet umożliwiał zdalny dostęp do routerów i przełączników, jednak nie zapewniał on szyfrowania przesyłanych danych, co narażało hasła oraz konfigurację urządzeń na przechwycenie. Rozwiązaniem tego problemu jest protokół Secure Shell (SSH), który umożliwia bezpieczne zestawienie połączenia dzięki szyfrowaniu transmisji oraz mechanizmom uwierzytelniania użytkownika i urządzenia. W ramach ćwiczenia skonfigurowano podstawowe parametry routera i przełącznika Cisco oraz uruchomiono usługę SSH, co pozwoliło na bezpieczny zdalny dostęp do urządzeń sieciowych w lokalnej sieci IP.  

 
### Konfiguracja routera  
Ustalamy hasła, baner i konfigurujemy interface G0/1 routera.  

![1.3](https://github.com/chrabek1/psk_sieci/blob/main/spr5/1.3.PNG?raw=true)  

### Konfiguracja PC-A.  

![1.4](https://github.com/chrabek1/psk_sieci/blob/main/spr5/1.4.PNG?raw=true)  

Sprawdzamy połączenie sieci.  

![1.5](https://github.com/chrabek1/psk_sieci/blob/main/spr5/1.5.PNG?raw=true)   

Ping nie powiódł się ponieważ przełącznik nie jest jeszcze skonfigurowany ani topologia nie jest odwzorowana.  
 
Konfigurujemy dostęp do routera przez SSH.  
Ustalamy nazwę urządzenia, domenę, generujemy klucz szyfrowania oraz nazwę i hasło użytkownika. Włączamy Telnet oraz SSH na liniach wejściowych VTY.  

![2.1-4](https://github.com/chrabek1/psk_sieci/blob/main/spr5/2.1-4.PNG?raw=true)  

Nie jesteśmy jeszcze w stanie ustanowić połączenia SSH do routera ponieważ przechodzi ono przez nieskonfigurowany jeszcze przełącznik.  

### Konfiguracja przełącznika   

Konfigurujemy podstawowe ustawienia przełącznika.  

![3.1](https://github.com/chrabek1/psk_sieci/blob/main/spr5/3.1.PNG?raw=true)  

Konfigurujemy przełącznik dla połączeń poprzez SSH.  

![3.2](https://github.com/chrabek1/psk_sieci/blob/main/spr5/3.2.PNG?raw=true)  

Ustawiamy połączenie SSH do przełącznika.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr5/3.3.PNG?raw=true)  

Udało się ustanowić sesję SSH.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr5/3.3dziala.PNG?raw=true)  

### Uruchamianie SSH z linii poleceń CLI w przełączniku  
Wyświetlamy opcje parametrów polecenia ssh i łączymy się przez SSH z R1.  
Przełączamy się między S1 a R1 bez zamykania sesji SSH za pomocą kombinacji klawiszy _Crtl+Shift+6_.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr5/4cale.PNG?raw=true)  
 
### Wnioski
 
Podczas realizacji ćwiczenia zapoznano się z zasadami bezpiecznego zdalnego zarządzania urządzeniami sieciowymi z wykorzystaniem protokołu SSH. Przeprowadzona konfiguracja routera oraz przełącznika Cisco pozwoliła na zrozumienie znaczenia poprawnych ustawień podstawowych, takich jak adresacja IP, hasła dostępu, banery informacyjne oraz konfiguracja linii VTY. Wykazano, że brak pełnej konfiguracji wszystkich elementów topologii uniemożliwia poprawną komunikację w sieci, co potwierdziły początkowe nieudane próby połączeń. Po prawidłowym skonfigurowaniu przełącznika możliwe było ustanowienie bezpiecznej sesji SSH zarówno z komputera PC, jak i bezpośrednio z poziomu CLI przełącznika. Ćwiczenie potwierdziło przewagę protokołu SSH nad Telnetem w kontekście bezpieczeństwa transmisji oraz podkreśliło jego kluczową rolę w administracji nowoczesnych sieci komputerowych.  
