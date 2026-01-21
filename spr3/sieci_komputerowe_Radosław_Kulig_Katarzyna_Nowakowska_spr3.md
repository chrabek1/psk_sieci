# Politechnika Świętokrzyska w Kielcach
## Wydział Zarządzania i Modelowania Komputerowego
##### Sieci Komputerowe
##### Laboratorium
#### Odczytywanie adresów MAC urządzeń sieciowych 
#### Wykorzystanie programu Wireshark do badania ruchu sieciowego
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
## Lab 7.2.7
## Wstęp teoretyczny
 
Sieci komputerowe umożliwiają wymianę danych pomiędzy urządzeniami poprzez zestaw połączonych ze sobą węzłów komunikacyjnych. Podstawą ich działania jest wielowarstwowy model komunikacji, w którym każda warstwa odpowiada za określone funkcje związane z przesyłaniem informacji. Jedną z kluczowych warstw jest warstwa łącza danych, która odpowiada za komunikację pomiędzy urządzeniami w obrębie tej samej sieci lokalnej.  

W warstwie łącza danych wykorzystywane są adresy MAC (Media Access Control), które jednoznacznie identyfikują interfejsy sieciowe urządzeń. Adresy te są przypisywane sprzętowo i służą do poprawnego dostarczania ramek danych w sieci lokalnej. Znajomość sposobów identyfikowania i odczytywania adresów MAC jest istotna w procesie diagnostyki, konfiguracji oraz zarządzania siecią.  

Celem ćwiczenia laboratoryjnego było zapoznanie się z metodami wyświetlania informacji o interfejsach sieciowych oraz adresach MAC przy użyciu narzędzi systemowych. W trakcie laboratorium przeanalizowano konfigurację kart sieciowych oraz rolę adresów MAC w komunikacji sieciowej.  

 
### Konfigurowanie urządzeń i weryfikacja połączeń. 
Konfigurujemy addres IPv4 dla komputera PC.  
![1.2a](https://github.com/chrabek1/psk_sieci/blob/main/spr3/7.2.7/1.2a.PNG?raw=true)  
W wierszu poleceń na komputerze PC-A wykonujemy ping na adres przełącznika.  
![1.2b](https://github.com/chrabek1/psk_sieci/blob/main/spr3/7.2.7/1.2b.PNG?raw=true)  
_Czy polecenia ping zostały wykonane pomyślnie? Wyjaśnij._   
> Pingi nie doszły do odbiorcy ponieważ przełącznik nie został jeszcze skonfigurowany.  
 
Konfigurujemy przełączniki.  
![1.3](https://github.com/chrabek1/psk_sieci/blob/main/spr3/7.2.7/1.3.PNG?raw=true)  

Sprawdzamy połączenie sieciowe, w tym celu pingujemy przełącznik z PC-A.  
![1.4](https://github.com/chrabek1/psk_sieci/blob/main/spr3/7.2.7/1.4.PNG?raw=true)  
_Czy polecenia ping zostały wykonane pomyślnie? Wyjaśnij._  
> Tak, pingi dotarły do hosta odbiorcy ponieważ skonfigurowaliśmy już przełącznik.  

### Analiza adresu MAC karty sieciowej PC-A.  
Wynik komendy `ipconfig/all`:  
![2.1a](https://github.com/chrabek1/psk_sieci/blob/main/spr3/7.2.7/2.1a.PNG?raw=true)  

_Jaką postać ma identyfikator OUI dla wskazanego adresu MAC karty sieciowej?_  
> Adres MAC karty sieciowej to: `00-E0-4C-55-37-D5`. OUI to pierwsze 3 bajty adresu MAC czyli `00-E0-4C`.

_Jaką postać ma część adresu MAC opisująca numer seryjny urządzenia?_  
>Numer seryjny to ostatnie 3 bajty adresu MAC, czyli `55-37-D5`.  

_Korzystając z powyższego przykładu, odszukaj nazwę producenta, który wyprodukował tą kartę sieciową_
> Producent karty sieciowej to Intel(R).

### Analiza adresu MAC interfejsu S1 F0/6  
W konsoli przełącznika S1 wpisujemy komendę `show interfaces vlan 1`.  
![2.2a](https://github.com/chrabek1/psk_sieci/blob/main/spr3/7.2.7/2.2a.PNG?raw=true)  

_Jaki jest adres MAC dla VLAN 1 na S1?_  
> Adres MAC dla VLAN 1 na S1 to `08:CC:68:34:81:40`.  

_Jaki jest numer seryjny adresu MAC dla VLAN 1?_   
>Numer seryjny to dla VLAN 1 to `34:81:40`.   

_Jaki jest OUI dla VLAN 1?_  
> OUI dla VLAN1 to `08:CC:68`.  

_Na podstawie tego OUI, odpowiedz, jaka jest nazwa producenta?_  
> Ten numer OUI należy do Cisco Systems, Inc.  

_Co oznacza adres bia?_  
> Adres bia to oryginalny adres MAC karty sieciowej nadany przez producenta.  

_Dlaczego w komunikacie wyjściowym polecenia show widzimy 2 razy ten sam adres MAC?  
> Ten sam adres MAC widoczny jest dwukrotnie, ponieważ interfejs VLAN 1 używa swojego fabrycznego adresu BIA jako aktualnego adresu MAC.

Wyświetlamy adres MAC używając polecenia `show arp`.  
![2.2b](https://github.com/chrabek1/psk_sieci/blob/main/spr3/7.2.7/2.2b.PNG?raw=true)  
_Jakie adresy warstwy 2 są wyświetlone na S1?_  
> Wyświetla się tylko adres przełącznika S1 ponieważ topologia jeszcze nie jest odtworzona.

Używamy komendy `show mac address-table` aby przejrzeć adresy MAC na przełączniku.  
![2.3](https://github.com/chrabek1/psk_sieci/blob/main/spr3/7.2.7/2.3.PNG?raw=true)  
_Czy przełącznik wyświetlał adres MAC PC-A? Jeśli odpowiedziałeś "tak" na jakim porcie to było?_  
> Nie wyświetlał się ponieważ podczas konfiguracji nie mieliśmy odtworzonej topologii. Jednak powinien się on wyświetlać na porcie `F0/6`.  

#### Pytania do przemyślenia
_Czy transmisja rozgłoszeniowa może wystąpić na poziomie warstwy 2? Jeśli tak, to jaki byłby adres MAC?_  
> W warstwie drugiej sieci Ethernet możliwe jest wysyłanie ramek do wszystkich urządzeń w danej sieci lokalnej (w obrębie jednego segmentu lub VLAN-u). Adres MAC używany w transmisji rozgłoszeniowej: `FF:FF:FF:FF:FF:FF`. Jest to adres MAC rozgłoszeniowy, który powoduje, że ramka zostaje odebrana przez wszystkie urządzenia w danym segmencie sieci.
 
_Do czego potrzebna jest znajomość adresu MAC urządzenia?_
> Adres MAC służy do jednoznacznej identyfikacji interfejsu sieciowego w sieci lokalnej. Jest on wykorzystywany do poprawnego dostarczania ramek Ethernet pomiędzy urządzeniami w obrębie tej samej sieci.
 
### Wnioski
 
Podczas realizacji ćwiczenia laboratoryjnego zapoznano się z podstawowymi zagadnieniami dotyczącymi warstwy łącza danych oraz rolą adresów MAC w sieciach lokalnych. Wykorzystując narzędzia diagnostyczne, takie jak ipconfig, show interfaces, show arp oraz show mac address-table, możliwe było przeanalizowanie sposobu identyfikacji urządzeń sieciowych oraz powiązania adresów IP z adresami MAC. Przeprowadzone testy łączności wykazały, że poprawna konfiguracja urządzeń jest niezbędna do prawidłowego działania komunikacji sieciowej.  

Ćwiczenie pozwoliło również zrozumieć budowę adresu MAC, w tym znaczenie identyfikatora OUI oraz części unikatowej, a także rolę adresu BIA. Dodatkowo potwierdzono możliwość występowania transmisji rozgłoszeniowej w warstwie drugiej oraz znaczenie adresu MAC rozgłoszeniowego. Zdobyta wiedza stanowi podstawę do dalszej nauki zagadnień związanych z funkcjonowaniem przełączników, diagnostyką sieci oraz analizą ruchu w sieciach komputerowych.  
 
***
## PT 10.3.5
### Wstęp teoretyczny  
Brama domyślna (ang. default gateway) jest elementem konfiguracji sieciowej, który umożliwia urządzeniom końcowym komunikację z hostami znajdującymi się poza ich siecią lokalną. Jest to adres interfejsu routera, do którego wysyłane są pakiety przeznaczone do innych sieci, gdy nie istnieje bardziej szczegółowa trasa w tablicy routingu hosta.  

Poprawna konfiguracja bramy domyślnej ma kluczowe znaczenie dla prawidłowego działania komunikacji między sieciami. Błędny adres bramy lub jego brak skutkuje niemożnością nawiązania połączenia z urządzeniami znajdującymi się poza lokalnym segmentem sieci. Celem ćwiczenia laboratoryjnego jest zdiagnozowanie i usunięcie problemów związanych z konfiguracją bramy domyślnej przy użyciu narzędzi diagnostycznych oraz symulatora Packet Tracer.  

## Rozwiązywanie problemów z bramą domyślną

Wypełniamy tabale adresowania aby móc przeprowadzić testy łączności.

### Tabela adresowania  

| Urządzenie | Interfejs        | Adres IP        | Maska podsieci     | Brama domyślna |
|-----------|------------------|-----------------|--------------------|---------------|
| R1        | G0/0             | 192.168.10.1    | 255.255.255.0      | nd.           |
| R1        | G0/1             | 192.168.11.1    | 255.255.255.0      | nd.           |
| S1        | VLAN 1           | 192.168.10.2    | 255.255.255.0      | 192.168.10.1  |
| S2        | VLAN 1           | 192.168.11.2    | 255.255.255.0      | 192.168.11.1  |
| PC1       | karta sieciowa   | 192.168.10.10   | 255.255.255.0      | 192.168.10.1  |
| PC2       | karta sieciowa   | 192.168.10.11   | 255.255.255.0      | 192.168.10.1  |
| PC3       | karta sieciowa   | 192.168.11.10   | 255.255.255.0      | 192.168.11.1  |
| PC4       | karta sieciowa   | 192.168.11.11   | 255.255.255.0      | 192.168.11.1  |


### Tabela testów połączeń

| Test        | Zakończony pomyślnie? | Problemy            | Rozwiązanie            | Sprawdzony |
|-------------|----------------------|----------------------|------------------------|------------|
| PC1 do PC2  | Nie                  | Adres IP na PC1      | Zmień adres IP PC1     |  Tak       |
| PC1 do S1   | Nie                  | Brama domyślna na S1 |Ustawiamy brame domyślną|   Tak      |
| PC1 do R1   | Tak                  | brak                 |                    |      Tak       |
| PC1 do S2   | Nie                  | VLAN 1                |Ustawiamy poprawny VLAN|   Tak      |
| PC1 do PC3  | Tak                  |                  |                    |   Tak         |
| PC1 do PC4  | Nie                  | Brama domyślna | poprawiamy bramę domyślną | Tak |   

Wykonujemy po koleji testy zgodnie z tabelą.

![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/1.1PingPC1-PC2_niedziala.PNG?raw=true)  
Ping PC1 na PC2 nie działa więc, sprawdzamy poprawność adresów IP na tych komputerach. IP PC1 okazuje się nieprawidłowy więc zmieniamy go na zgodny z tabelą adresacji.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/1.1zmianaIP_PC1.PNG?raw=true)  
Po zmianie adresu IP PC1  udaje się prawidłowo nawiązać łączność z PC2.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/1.1PingPC1-PC2_dziala.PNG?raw=true)  
Ping PC1 na S1 również nie działa więc sprawdzamy konfiguracje S1.
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/S1defaultGateway_brak.PNG?raw=true)
Okazuje się że S1 nie ma ustawionej bramy domyślnej więc ustawiamy ją zgodnie z tabelą adresacji.
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/S1defaultGateway.PNG?raw=true)
Udaje się nawiązać połączenie PC1 do S1
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/PingPC1-S1.PNG?raw=true)
Wykonujemy ping PC1 do R1.
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/1.1PingPC1-R1.PNG?raw=true)  
Okazuje się działać od razu poprawnie.
Wykonujemy ping PC1 do S2. Jako że nie działa sprawdzamy konfiguracje S2 i ustawiamy poprawny adres VLAN 1 zgodnie z tabelą adresacji.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/vlanS2.PNG?raw=true)
Po poprawieniu adresu VLAN 1 na przełączniku S2 udaje nam się nawiązać łączność.
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/PingPC1-S2.PNG?raw=true)
Następnie pingujemy PC3 z PC1.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/PingPC1-PC3_dziala.PNG?raw=true)
Udaje nam się nawiązać łączność.
Następnie pingujemy PC4 z PC1.
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/PingPC1-PC4_niedziala.PNG?raw=true)  
Nie udaje nam się nawiązać połaczenia więc sprawdzamy konfiguracje PC4 i zmieniamy bramę domyślną na poprawną zgodnie z tabelą adresacji.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/1.1zmianaDefaultGatewayPC4.PNG?raw=true)  
Po zmianie bramy domyślnej na PC4 udaje już się pomyślnie nawiązać połączenie.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.3.5/pingPC1-PC4_dziala.PNG?raw=true)
Wyeliminowaliśmy wszystkie problemy i udało nam się poprawnie nawiązać wszelkie łączności.

## Wnioski

Podczas realizacji ćwiczenia laboratoryjnego udało się skutecznie zdiagnozować oraz usunąć wszystkie problemy związane z błędną konfiguracją adresów IP, bram domyślnych oraz interfejsów VLAN. Kolejne testy łączności pozwoliły na identyfikację przyczyn braku komunikacji pomiędzy urządzeniami oraz potwierdziły poprawność wprowadzanych zmian konfiguracyjnych.

Po wprowadzeniu prawidłowych ustawień zgodnych z tabelą adresowania wszystkie urządzenia sieciowe nawiązały poprawną łączność. Ćwiczenie potwierdziło, że poprawna konfiguracja bramy domyślnej jest kluczowa dla komunikacji między różnymi sieciami oraz stanowi istotny element procesu diagnozowania i rozwiązywania problemów sieciowych.

## Lab 10.4.4

## Wstęp teoretyczny

Sieć komputerowa składa się z urządzeń końcowych oraz urządzeń pośredniczących, takich jak przełączniki i routery, które umożliwiają wymianę danych pomiędzy hostami. Przełączniki działające w warstwie drugiej modelu OSI odpowiadają za komunikację w obrębie jednej sieci lokalnej, natomiast routery, pracujące w warstwie trzeciej, umożliwiają łączenie różnych sieci oraz przesyłanie pakietów pomiędzy nimi.

Poprawne zaprojektowanie i konfiguracja sieci wymaga właściwego doboru połączeń fizycznych, adresacji IP oraz konfiguracji interfejsów sieciowych. Celem ćwiczenia laboratoryjnego było zbudowanie sieci opartej na przełącznikach i routerze oraz sprawdzenie poprawności jej działania poprzez weryfikację łączności pomiędzy poszczególnymi urządzeniami.

### Konfiguracja urządzeń
Konfigurujemy Adresy IPv4 i IPv6, maski podsieci i bramy domyślne na PC-A i PC-B.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.4.4/2.1a.PNG?raw=true)    
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.4.4/2.1a_ipv6.PNG?raw=true)  
Pingujemy PC-B z PC-A.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.4.4/2.1c.PNG?raw=true)  
_Dlaczego ping sie nie powiódł?_  
>Ten ping nie miał prawa zadziałać, ponieważ nie skonfigurowaliśmy jeszcze routera ani switcha.

Następnie konfigurujemy router.
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.4.4/2.1a-i.PNG?raw=true)  
Konfigurujemy i uaktywniamy oba interfejsy na routerze.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.4.4/2.2j_s1.PNG?raw=true)  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.4.4_nie%20dziala/2.2jpc-b.PNG?raw=true)  
Ustawiamy zegar na routerze.
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.4.4/2.2n.PNG?raw=true)  
Wykonujemy ping z PC-A na PC-B.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr3/10.4.4/2.1c.PNG?raw=true)
_Czy polecenia ping zostały wykonane pomyślnie? Wyjaśnij_
> Nie ponieważ nie skonfigurowaliśmy jeszcze przełącznika
