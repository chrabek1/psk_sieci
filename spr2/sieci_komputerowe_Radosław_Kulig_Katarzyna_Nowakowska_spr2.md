# Politechnika Świętokrzyska w Kielcach
## Wydział Zarządzania i Modelowania Komputerowego
##### Sieci Komputerowe
##### Laboratorium
#### Badanie modeli TCP/IP i OSI w działaniu.
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

## Wstęp teoretyczny

Podstawą działania współczesnych sieci komputerowych jest poprawna komunikacja pomiędzy urządzeniami, oparta na jasno zdefiniowanych warstwach i protokołach. Każdy element infrastruktury sieciowej – od kabli i kart sieciowych, po przeglądarki internetowe i serwery – pełni określoną funkcję w procesie przesyłania danych. Aby zrozumieć ten proces, konieczne jest poznanie zarówno warstwy fizycznej, jak i zasad funkcjonowania modeli odniesienia OSI oraz TCP/IP, a także narzędzi służących do analizy ruchu sieciowego.

Model OSI (Open Systems Interconnection) opisuje sposób, w jaki dane są przesyłane od jednego urządzenia do drugiego poprzez siedem warstw, z których każda odpowiada za określony etap komunikacji – od fizycznej transmisji sygnału po aplikacje użytkownika końcowego. Model TCP/IP, będący praktycznym uproszczeniem modelu OSI, składa się z czterech warstw i stanowi podstawę funkcjonowania Internetu. Zrozumienie relacji między tymi modelami pozwala lepiej analizować i diagnozować problemy w sieciach komputerowych.

Warstwa fizyczna, będąca najniższą warstwą modelu OSI, odpowiada za fizyczne połączenie urządzeń i przesyłanie sygnałów elektrycznych, optycznych lub radiowych. W ramach tego etapu konfiguracji użytkownik uczy się rozpoznawać porty, moduły i interfejsy różnych urządzeń sieciowych (takich jak routery, przełączniki czy komputery PC) oraz dobierać odpowiednie typy kabli i połączeń. Poprawne wykonanie tych czynności umożliwia prawidłową wymianę danych pomiędzy hostami w sieci.

Kiedy urządzenia są już połączone, istotne staje się zrozumienie, jak dane są przesyłane, enkapsulowane i dekapsulowane podczas komunikacji między klientem a serwerem. W tym celu wykorzystuje się program Cisco Packet Tracer, który pozwala obserwować działanie modeli OSI i TCP/IP w trybie symulacji. Dzięki temu można analizować poszczególne warstwy, jednostki danych protokołów (PDU) oraz proces komunikacji, np. podczas żądania strony WWW z wykorzystaniem protokołu HTTP.

Z kolei narzędzie Wireshark umożliwia praktyczną analizę rzeczywistego ruchu sieciowego. Program przechwytuje i interpretuje pakiety przesyłane w sieci, co pozwala użytkownikowi śledzić adresy IP i MAC, zrozumieć strukturę ramek oraz zależności między poszczególnymi warstwami. Dzięki temu można dokładnie zobaczyć, w jaki sposób protokoły – takie jak ICMP, ARP, DNS czy HTTP – funkcjonują w praktyce.

## PT 3.5.5

### Badanie ruchu internetowego HTTP
W Packet tracerze wchodzimy w tryb symulacji i śledzimy zdarzenia HTTP. Aby mieć co śledzić generujemy ruch HTTP otwierając stronę _www.osi.local_ w przeglądarkę __Web Browser__.   
![1.2c](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.2c.png?raw=true)  
Przechodzimy przez 4 kolejne wydarzenia trybu symulacji, które pojawiąją się na liście zdarzeń.  
![1.2d](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.2d.png?raw=true)  
_Spójrz na stronę przeglądarki internetowej klienta WWW. Czy coś się zmieniło?_  
> Wyświetliła się treść strony  

Badamy zawartość pakietu HTTP, wybieramy pierwsze zdarzenie z listy __Event List__  
![1.3](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.3.png?raw=true)  
W kolumnie __Out Layers__ wybieramy __Layer 7__  
![1.3b](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.3b.png?raw=true)  

- _Jakie informacje wyświetlone są w ponumerowanych krokach bezpośrednio poniżej pól In Layers i Out  Layers dla warstwy 7?_  
> 1.The HTTP client sends a HTTP request to the server.  
- _Jaka jest wartość Dst Port dla Layer 4  w kolumnie Out Layers ?_  
> Dst Port:80  
- _Jaka jest wartość Dest. IP dla Layer 3 w kolumnie Out Layers ?_  
> 192.168.1.254  
- _Jakie informacje są wyświetlane w warstwie 2 w kolumnie Out Layers?_  
> Layer 2: Ethernet II Header 0060.47CA. 4DEE >> 0001.96A9.401D

Klikamy na drugą zakładkę __Outbound PDU Details__  
![1.3c](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.3c.png?raw=true)  
- _Jakie są wspólne informacje wymienione w sekcji IP szczegółów PDU (PDU Details) w porównaniu do informacji wymienionych w zakładce OSI Model?  Z którą warstwą jest ona związana?_  
> Sa to SRC IP i DST IP związane z warstwą 3.  
- _Jakie są wspólne informacje wymienione w sekcji TCP szczegółów PDU (PDU Details) w porównaniu do informacji wymienionych w zakładce OSI Model? Z którą warstwą jest to związane?_    
> Są to Src Post i Dst Port związane z warstwą 4.  
- _Co to jest Host wymienione w sekcji HTTP PDU Datails ? Z jaką warstwą te informacje byłyby powiązane w ramach zakładki OSI Model?_  
> Jest to nagłówek HTTP określający nazwę hosta/domenę serwera. Z warstwą 7(aplikacji).  

Klikamy następny kolorowy kwadrat w Kolumnie __type__ na liście zdarzeń  
![1.3e](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.3e.png?raw=true)  
_Porównując informacje wyświetlane w kolumnie In Layers z tymi w kolumnie Out Layers, jakie są między nimi główne różnice?_  
> Główną różnicą jest odwrotny kierunek komunikacji.  

Wybieramy zakładkę Inbound and Outbound PDU Details.  

![1.3f](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.3f.png?raw=true)  

Klikamy ostatni kolorowy kwadrat w kolumnie __Info__.  

![1.3g](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.3g.png?raw=true)  

_Ile zakładek zostało wyświetlonych w tym zdarzeniu?_  
> Widoczne są tylko zakładki __OSI Model__ i __Inbound PDU Details__ ,które zawiera dane o pakiecie po wejściu do urządzenia.  

### Wyświetlenie elementów zestawu protokołów TCP/IP  
W sekcji __Event List Filters__ wyświetlamy wszystkie zdarzenia.  

![2.1b](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/2.1b.png?raw=true)  

_Jakie dodatkowe typy zdarzeń są wyświetlane?_
> DNS, ARP i TCP  

Klikamy pierwsze zdarzenie DNS w kolumnie __Type__ i zapoznujemy się z zakładkami OSI Model i PDU Detail  

![2.1c](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/2.1c.png?raw=true)  

Klikamy na __Outbound PDU Details__  

![2.1d](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/2.1d.png?raw=true)  

_Jakie informacje podane są w polu NAME sekcji DNS QUERY?_  
> Jest tam adres strony _www.osi.local_  

Klikamy ostatni kolorowy kwadrat DNS Info na liście zdarzeń.  

![2.1e](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/2.1e.PNG?raw=true)  

_Na którym urządzeniu został przechwycony PDU?_  
> Na naszym symulowanym urządzeniu  

_Jaka jest wartość wyświetlona obok ADDRESS: w sekcji DNS ANSWER zakładki (Inbound PDU Details)?_  
> Jest to adres IP naszego urządzenia: 192.168.1.254  

Znajdujemy pierwsze zdarzenie __HTTP__ na liście i klikamy kolorowe pole kwadratu zdarzenia TCP bezpośrednio po tym zdarzeniu. Zaznaczamy __Layer 4__ w zakładce __OSI Model__.

![2.1f](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/2.1f.PNG?raw=true)  
_Na podstawie numerowanej listy bezpośrednio poniżej obszarów In Layers i Out Layers, jakie informacje wyświetlone są w punkcie 4 i 5?_  
> Potwierdzenie sukcesu nawiązania połączenia  
> 4. The TCP connection is successful.   
> 5. The device sets the connection state to ESTABLISHED.  

Klikamy ostatnie zdarzenie TCP. Zaznaczamy Layer 4 w zakładce OSI Model  

![2.1g](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/2.1g.PNG?raw=true)  

_Jakie jest przeznaczenie tego zdarzenia, w oparciu o informacje zawarte w ostatniej pozycji na liście?_  
>Zamknięcie połączenia.

#### Pytania - wyzwawanie

_Na podstawie informacji, która została sprawdzona podczas przechwytywania w Packet Tracer, jaki numer portu ma, nasłuchujący żądań stron WWW serwer (Web Server)?_  
> Port 80 – jest to standardowy port dla protokołu HTTP.
_Na jakim porcie Web Server nasłuchuje żądania DNS?_
> Port 53 – jest to standardowy port dla protokołu DNS (zarówno UDP, jak i TCP).

### Wnioski

W trakcie ćwiczenia możliwe było szczegółowe prześledzenie sposobu, w jaki dane są przesyłane w sieci zgodnie z modelami TCP/IP oraz OSI. Tryb symulacji w Packet Tracer umożliwił obserwację procesu enkapsulacji oraz dekapsulacji danych na każdym etapie komunikacji pomiędzy klientem a serwerem WWW. Dzięki analizie PDU można było zauważyć, jak kolejne warstwy dodają własne nagłówki zawierające istotne informacje, takie jak adres MAC, adres IP, numery portów czy dane aplikacji.

Ćwiczenie pokazało również, jak w praktyce funkcjonują dodatkowe protokoły zestawu TCP/IP – m.in. DNS, ARP oraz TCP. DNS odpowiada za tłumaczenie nazwy domenowej na adres IP, ARP za uzyskanie adresu MAC dla urządzeń docelowych, a TCP za ustanawianie i utrzymanie niezawodnego połączenia między hostami. Analiza wielu typów zdarzeń pozwoliła lepiej zrozumieć rolę poszczególnych protokołów w komunikacji sieciowej.

Dzięki wizualizacji w Packet Tracer możliwe było zrozumienie kierunku przepływu danych, sposobu reagowania urządzeń na zapytania oraz powiązania elementów modeli TCP/IP i OSI. Ćwiczenie znacząco ułatwia zrozumienie działania stosu protokołów i przygotowuje do dalszej analizy ruchu sieciowego oraz diagnozowania problemów w sieciach komputerowych.

***
## LAB 3.7.10

### Użycie programu Wireshark do przechwycenia i analizy lokalnych danych ICMP
W wierszu poleceń wpisujemy komendę ipconfig /all w celu zobaczenia adresu IP interfejsu komputera, jego opisu oraza adresu fizycznego(MAC).   
![spr2/3.7.10/1.1a.PNG](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/1.1a.PNG)  

Następnie uruchamiamy program Wireshark i klikamy dwukrotnie żądany interfejs w celu rozpoczęcia przechwytywania pakietów. W tym labolatorium interesują nas tylko PDU typu ICMP, dlatego więc w polu Filter wpisujemy icmp i klikamy Enter.  

Przechodzimy ponownie do wiersza poleceń i pingujemy adres IP drugiego członka zespołu.
![https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/1.2c2.PNG](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/1.2c2.PNG)  

Kończymy przechwytywanie klikając na Stop Capture.  

![https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/1.2c.PNG](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/1.2c.PNG)  

Analizujemy dane wygenerowane przez żądania ping. Wireshark wyświetla te dane w trzech sekcjach. Górna sekcja wyświetla listę ramek PDU z podsumowaniem informacji o danym pakiecie IP. Druga sekcja wyświetla informacje na temat ramki PDU oraz dzieli ją na bazie poszczególnych warstw protokołów. Trzecia sekcja wyświetla nieprzetworzone dane(w trybie szesnastkowym oraz dziesiętnym) dla poszczególnej warstwy.  

![https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/1.3a.PNG](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/1.3a.PNG)  


![spr2/3.7.10/1.3b.PNG](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/1.3b.PNG)  

- _Czy źródłowy adres MAC pasuje do interfejsu komputera?_  
  
> Tak, pasuje.  

- _Czy docelowy adres MAC w Wireshark odpowiada adresowi MAC członka zespołu?_  
  
> Tak, odpowiada adresowi fizycznemu członka zespołu.  

- _W jaki sposób twój PC uzyskał MAC adres komputera PC, na który wysyłałeś żądania ping?_  

> Poprzez protokół ARP (Address Resolution Protocol).  
  

### Użycie programu Wireshark do przechwycenia i analizy zdalnych danych ICMP  

Ponownie rozpoczynamy przechwytywanie. Gdy wyświetli się okno komunikatu klikamy Continue without saving. Pinguj następujące trzy adresy URL witryn z wiersza polecenia systemu Windows:  www.yahoo.com, www.cisco.com, www.google.com.

![](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/2.1c_yahoo.PNG)  

![](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/2.1c_cisco.PNG)  

![](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/2.1c_google.PNG)  

Zatrzymujemy proces przechwytywania danych klikając ikonę Stop Capture.  


Przeglądamy przechwycone dane w programie Wireshark.  
![](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/2.2yahoo.PNG)  


![](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/2.2cisco.PNG)  


![](https://github.com/chrabek1/psk_sieci/blob/c129221cc9a12a53fb11a2030def6c8315692feb/spr2/3.7.10/2.2google.PNG)  


Adresy IP i MAC trzech stron internetowych dla których wykonaliśmy pingowanie:
| Strona | Adres IP | Adres MAC |
| ------------- |:-------------:|:-------------:|
|  www.yahoo.com  | 74.6.143.26 | 00:10:db:ff:10:04 |
|  www.cisco.com | 23.198.224.115 | 00:10:db:ff:10:04 |
| www.google.com | 142.20.109.147 | 00:10:db:ff:10:04 |  

_Co jest istotne w tej informacji?_
>
_Czym różni się ta informacja od informacji uzyskanej w części 1, dotyczącej używania polecenia ping w
sieci lokalnej?_
>


## Wnioski
W ramach przeprowadzonych ćwiczeń zapoznaliśmy się z podstawowymi zasadami analizy ruchu sieciowego za pomocą analizatora protokołów Wireshark. Nabyliśmy praktyczne umiejętności w zakresie przechwytywania i filtrowania danych sieciowych, a także szczegółowej inspekcji nagłówków pakietów na różnych warstwach modelu TCP/IP.  

Przechwycone i przeanalizowane pakiety ICMP(polecenie ping) potwierdziły poprawność działania protokołów warstwy sieciowej. Ćwiczenie pozwoliło nam również zrozumieć i zweryfikować znaczenie procesu enkapsulacji oraz kluczową rolę protokołów pomocniczych, takich jak ARP w dynamicznym rozwiązywaniu adresów MAC w sieci lokalnej oraz DNS w translacji nazw domenowych na adresy IP. Ponadto, zaobserwowaliśmy praktyczną różnicę w adresowaniu warstwy drugiej (MAC) między komunikacją lokalną, a komunikacją zdalną.  

Podsumowując, laboratorium umożliwiło utrwalenie teoretycznej wiedzy na temat modelów sieciowych poprzez ich praktyczną weryfikację. Zyskaliśmy głębokie zrozumienie wewnętrznych mechanizmów odpowiedzialnych za transmisję danych w sieciach IP oraz nabyliśmy podstawowe umiejętności niezbędne do diagnozowania i rozwiązywania problemów sieciowych na podstawie analizy rzeczywistego ruchu pakietów.  

***

## PT 4.7.2  

### Określenie właściwości fizycznych urządzeń pracujących w intersieci  

W celu indentyfikacji portów zarządzania routera klikamy na niego (East) i przechodziny do zakładki Physical, która powinna być aktywna. Możemy powiększyć i rozszerzyć okno, aby zobaczyć cały router.  

- _Które porty zarządzania są dostępne?_  
>Router domyślnie ma dwa porty Gigabit Ethernet plus porty Console/Auxiliary. Dodatkowo, ma sloty na rozszerzenia, dzięki którym można dodać np. porty szeregowe WAN lub dodatkowe porty LAN/przełączające.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/1.1.PNG?raw=true)  


Identyfikujemy interfejsy LAN I WAN w tym celu klikamy kartę **CLI**, a następnie Enter.  

- _Które interfejsy LAN i WAN są dostępne w routerze East i ile ich jest?_  
	>LAN (GigabitEthernet): Dwa interfejsy: GigabitEthernet0/0 i GigabitEthernet0/1.  
	>WAN (Serial): Dwa interfejsy: Serial0/0/0 i Serial0/0/1.  

Jeżeli chcemy uzyskać dostęp do trybu użytkownika musimy wporawdzić polecenie show ip interface brief.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/1.2b.PNG?raw=true)   

- _Ile jest wyświetlonych interfejsów fizycznych?_  
>Wyświetlone są 4 interfejsy fizyczne (GigabitEthernet0/0, GigabitEthernet0/1, Serial0/0/0, Serial0/0/1).  


Wprowadzamy polecenie **show interface gigabitethernet 0/0**.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/1.2c.PNG?raw=true)  

- _Jaka jest domyślna szerokość pasma tego interfejsu?_  
>Domyślna szerokość pasma tego interfejsu wynosi: 1 000 000 Kbit/s (1 Gbps).  



Wprowadzamy polecenie **show interface serial 0/0/0**.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/1.2c2.PNG?raw=true)  
- _Jaka jest domyślna szerokość pasma tego interfejsu?_   
>Domyślna szerokość pasma tego interfejsu (oznaczona jako BW) wynosi: 1544 Kbit/s (1.544 Mbps).  


Indentyfikujemy złącza modułów rozszerzeń.  

- _Ile złączy rozszerzeń jest dostępnych dla dodatkowych modułów na routerze East?_  
>Dwa złącza rozszerzeń.  

Następnie klikamy na **Switch2**.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/1.3.PNG?raw=true)  

- _Ile złączy rozszerzeń jest dostępne?_  
>Dostępnych jest 6 złączy rozszerzeń.  


### Wybieranie odpowiednich modułów dla połączeń

Klikamy na East, a następnie kliknij zakładkę **Physical**. Po lewej stronie, pod etykietą Modules, można zobaczyć dostępne opcje rozszerzające możliwości routera. 

![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/2.1a.PNG?raw=true)
<img width="611" height="517" alt="image" src="https://github.com/user-attachments/assets/289a4359-6456-468e-a4e6-0958bd502238" />  
<img width="659" height="541" alt="image" src="https://github.com/user-attachments/assets/8f3c445f-21db-4ece-9626-5e148937d48a" />  
<img width="646" height="521" alt="image" src="https://github.com/user-attachments/assets/175010cf-78ab-4bbf-bfd0-1f9d4577b44c" />  
<img width="684" height="557" alt="image" src="https://github.com/user-attachments/assets/e5caa183-af61-4015-8d38-95c362392ca1" />  
<img width="698" height="575" alt="image" src="https://github.com/user-attachments/assets/b928530b-7206-41d5-b2cd-0e20edcff217" />  
<img width="661" height="536" alt="image" src="https://github.com/user-attachments/assets/f6d34d4d-80d9-4eb0-869f-aa9e48d79812" />  


- _Musisz podłączyć komputery PC1,2 i 3 do routera East, ale nie masz wystarczających środków do zakupu nowego przełącznika. Który moduł można wykorzystać do podłączenia trzech komputerów do routera East?_  
>Należy wykorzystać moduł HWIC-4ESW. Ten moduł jest kartą rozszerzeń z czterema portami przełączającymi, co pozwala na bezpośrednie podłączenie wielu urządzeń końcowych (hostów) do routera, efektywnie zastępując oddzielny przełącznik dla małej grupy urządzeń.
utaj.  
- _Ile hostów można połączyć z routerem za pomocą tego modułu?_  
>Moduł HWIC-4ESW posiada cztery porty przełączające.  

Klikamy **Switch2**.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/2.1b.PNG?raw=true)  

- _Który moduł możesz włożyć, aby zapewnić Gigabitowe połączenie optyczne do przełącznika Switch3?_  
>PT-SWITCH-NM-1FGE  

Klikamy ponownie East. Musimy spróbować włożyć odpowiedni moduł z kroku 1a.   
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/2.2a.PNG?raw=true)  

Zostanie wyświetlony komunikat Cannot add a module when the power is on. Urządzenie musi zostać wyłączone przed dodaniem lub usunięciem modułów, a więc klikamy przycisk zasilania i wyłączamy East. Musimy teraz włożyć odpowiedni moduł z kroku 1a. Po zakończeniu klikamy przycisk zasilania i włączamy East.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/2.2b.PNG?raw=true)  

Korzystając z tej samej procedury wkładamy moduł zidentyfikowany w kroku 1b do pustego gniazda najdalej po prawej stronie Switch2. Następnie używamy polecenia show ip interface brief na Switch2.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/2.2c.PNG?raw=true)  

- _W którym złączu moduł został umieszczony?_  
>GigabitEthernet5/1.  

### Łączenie urządzeń  

Używamy poniższej tabeli, aby prawidłowo połączyć wszystkie urządzenia. Wybieramy odpowiedni rodzaj kabla, następnie klikamy na pierwsze urządzenie i wybieramy określony interfejs. Klikamy na drugie urządzenie i wybierz określony interfejs. Jeżeli prawidłowo połączyliśmy dwa urządzenia, zobaczysz że wynik się zwiększył.  
<img width="886" height="571" alt="image" src="https://github.com/user-attachments/assets/b4ea0490-0038-4971-a638-6dce50187651" />  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/3.PNG?raw=true)  

### Sprawdzanie połączeń
Sprawdzamy status interfejsu na East. Klikamy zakładkę CLI i wprowadzamy komendę show ip interface brief.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/4.1a.PNG?raw=true)  

Klikamy **Laptop** i wybieramy kartę Config . Wybieramy interfejs **Wireless0** i zaznaczamy pole wyboru On.   
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/4.2a.PNG?raw=true)  

Klikamy kartę Desktop na Laptop, a następnie ikonę Web Browser , aby uruchomić przeglądarkę internetową. Wpisujemy  www.cisco.pka w polu URL i kliknij Go.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/4.2b.PNG?raw=true)  


Klikamy **TabletPC** i wybierz kartę Config i  interfejs **Wireless0**. Zaznaczamy pole wyboru On.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/4.2c.PNG?raw=true)  

Powtarzamy kroki opisane w kroku 2b w instrukcji, aby zweryfikować wyświetlanie strony.  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/4.2d.PNG?raw=true)  

Teraz zmieniamy metodę dostępu tabletu. Klikamy **TabletPC** i wybierz kartę Config oraz interfejs **Wireless0** . Odznaczamy pole On. Powinno być teraz puste, a połączenie bezprzewodowe utracone.  
Następnie klikamy interfejs 3G/4G Cell1. Zaznaczamy pole wyboru On, w ciągu kilku sekund powinno pojawić się połączenie komórkowe.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/4.3b.PNG?raw=true)  

Powtarzamy proces weryfikacji dostępu do Internetu.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/4.3c.PNG?raw=true)  


Teraz sprawdzamy łączność z innymi komputerami, ponieważ wszystkie komputery powinny mieć łączność ze stroną internetową i ze sobą nawzajem.  

![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/4.4pc2.PNG?raw=true)  
![](https://github.com/chrabek1/psk_sieci/blob/main/spr2/4.7.2/4.4pingPC7-PC2.PNG?raw=true)  

## Wnioski
W ramach przeprowadzonych ćwiczeń zapoznaliśmy się z podstawowymi zasadami projektowania i implementacji warstwy fizycznej w intersieci symulowanej w programie Cisco Packet Tracer. Nabywaliśmy praktyczne umiejętności w zakresie identyfikacji , rozszerzania oraz prawidłowego okablowania urządzeń sieciowych.

Zidentyfikowaliśmy dostępne porty zarządzania i interfejsy LAN/WAN routera East , a następnie, kierując się koniecznością podłączenia dodatkowych hostów PC1, PC2 i PC3 bez nabywania nowego przełącznika, wybraliśmy i zainstalowaliśmy moduł przełączający HWIC-4ESW. Proces ten wymagał uprzedniego wyłączenia zasilania routera, co jest kluczową procedurą w pracy z modułami nierozszerzalnymi w trybie hot-swap. Analogicznie postąpiliśmy z przełącznikiem Switch2, instalując moduł optyczny PT-SWITCH-NM-1FGE w celu zapewnienia gigabitowego połączenia ze Switch3.

Kolejnym etapem było prawidłowe okablowanie całej topologii. Po nawiązaniu wszystkich połączeń, status interfejsów został zweryfikowany za pomocą poleceń CLI (np. show ip interface brief), a testy łączności (dostęp do strony internetowej i pingi między hostami) potwierdziły pełną funkcjonalność sieci.

Podsumowując, laboratorium umożliwiło nam utrwalenie kluczowych umiejętności w zakresie fizycznej administracji sieciowej, w tym rozszerzania urządzeń, prawidłowego doboru okablowania oraz podstawowej diagnostyki, co jest fundamentalne dla zapewnienia niezawodności i skalowalności infrastruktury sieciowej.














