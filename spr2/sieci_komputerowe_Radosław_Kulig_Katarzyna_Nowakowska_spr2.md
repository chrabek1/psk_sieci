# Politechnika Świętokrzyska w Kielcach
## Wydział Zarządzania i Modelowania Komputerowego
##### Sieci Komputerowe
##### Laboratorium
#### Badanie modeli TCP/IP i OSI w działaniu.
#### Wykorzystanie programu Wireshark do badania
ruchu sieciowego
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
Badamy zawartość pakietu HTTP, wybieramy pierwsze zdarzenie z listy __Event List__  
![1.3](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.3.png?raw=true)  
W kolumnie __Out Layers__ wybieramy __Layer 7__  
![1.3b](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.3b.png?raw=true)  

- _Jakie informacje wyświetlone są w ponumerowanych krokach bezpośrednio poniżej pól In Layers i Out Layers dla warstwy 7?_  
1.The HTTP client sends a HTTP request to the server.  
- _Jaka jest wartość Dst Port dla Layer 4  w kolumnie Out Layers ?_  
Dst Port:80  
- _Jaka jest wartość Dest. IP dla Layer 3 w kolumnie Out Layers ?_  
192.168.1.254  
- _Jakie informacje są wyświetlane w warstwie 2 w kolumnie Out Layers?_  
Layer 2: Ethernet II Header 0060.47CA. 4DEE >> 0001.96A9.401D

Klikamy na drugą zakładkę __Outbound PDU Details__  
![1.3c](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.3c.png?raw=true)  
- _Jakie są wspólne informacje wymienione w sekcji IP szczegółów PDU (PDU Details) w porównaniu do informacji wymienionych w zakładce OSI Model?  Z którą warstwą jest ona związana?_  
Sa to SRC IP i DST IP związane z warstwą 3.  
- _Jakie są wspólne informacje wymienione w sekcji TCP szczegółów PDU (PDU Details) w porównaniu do informacji wymienionych w zakładce OSI Model? Z którą warstwą jest to związane?_    
Są to Src Post i Dst Port związane z warstwą 4.  
- _Co to jest Host wymienione w sekcji HTTP PDU Datails ? Z jaką warstwą te informacje byłyby powiązane w ramach zakładki OSI Model?_  
Jest to nagłówek HTTP określający nazwę hosta/domenę serwera. Z warstwą 7(aplikacji).  

Klikamy następny kolorowy kwadrat w Kolumnie __type__ na liście zdarzeń  
![1.3e](https://github.com/chrabek1/psk_sieci/blob/main/spr2/3.5.5/1.3e.png?raw=true)  

## Wnioski

W ramach przeprowadzonych ćwiczeń zapoznaliśmy się z podstawowymi zasadami konfiguracji przełączników sieciowych Cisco oraz urządzeń końcowych. Nabyli praktyczne umiejętności w zakresie obsługi interfejsu CLI, konfiguracji adresacji IP, interfejsów VLAN, haseł dostępowych i banerów systemowych.

Przeprowadzone testy łączności (polecenie ping) potwierdziły poprawność konfiguracji oraz prawidłowe działanie połączeń między przełącznikami i komputerami w ramach jednej sieci lokalnej. Ćwiczenie pozwoliło nam również zrozumieć znaczenie stanu portów przełącznika oraz wpływ poprawnej konfiguracji warstwy drugiej modelu OSI na funkcjonowanie sieci.

Podsumowując, laboratorium umożliwiło utrwalenie podstawowych umiejętności administracyjnych niezbędnych do zarządzania infrastrukturą sieciową, a także zrozumienie mechanizmów odpowiedzialnych za przesyłanie danych w sieciach LAN.

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
  
    Tak, pasuje.

- _Czy docelowy adres MAC w Wireshark odpowiada adresowi MAC członka zespołu?_
  
    Tak, odpowiada adresowi fizycznemu członka zespołu.

- _W jaki sposób twój PC uzyskał MAC adres komputera PC, na który wysyłałeś żądania ping?_

    Poprzez protokół ARP (Address Resolution Protocol).
  

### Użycie programu Wireshark do przechwycenia i analizy zdalnych danych ICMP

Ponownie rozpoczynamy przechwytywanie. Gdy wyświetli się okno komunikatu klikamy Continue without saving. Pinguj następujące trzy adresy URL witryn z wiersza polecenia systemu Windows: www.yahoo.com, www.cisco.com, www.google.com.

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
|  www.yahoo.com  | 74.6.143.26 | 00:e0:4c:55:3a:7c |
|  www.cisco.com | 23.198.224.115 | 00:10:db:ff:10:04 |
| www.google.com | 142.20.109.147 | 00:10:db:ff:10:04 |


## Wnioski
W ramach przeprowadzonych ćwiczeń zapoznaliśmy się z podstawowymi zasadami analizy ruchu sieciowego za pomocą analizatora protokołów Wireshark. Nabyliśmy praktyczne umiejętności w zakresie przechwytywania i filtrowania danych sieciowych, a także szczegółowej inspekcji nagłówków pakietów na różnych warstwach modelu TCP/IP.

Przechwycone i przeanalizowane pakiety ICMP(polecenie ping) potwierdziły poprawność działania protokołów warstwy sieciowej. Ćwiczenie pozwoliło nam również zrozumieć i zweryfikować znaczenie procesu enkapsulacji oraz kluczową rolę protokołów pomocniczych, takich jak ARP w dynamicznym rozwiązywaniu adresów MAC w sieci lokalnej oraz DNS w translacji nazw domenowych na adresy IP. Ponadto, zaobserwowaliśmy praktyczną różnicę w adresowaniu warstwy drugiej (MAC) między komunikacją lokalną, a komunikacją zdalną.

Podsumowując, laboratorium umożliwiło utrwalenie teoretycznej wiedzy na temat modelów sieciowych poprzez ich praktyczną weryfikację. Zyskaliśmy głębokie zrozumienie wewnętrznych mechanizmów odpowiedzialnych za transmisję danych w sieciach IP oraz nabyliśmy podstawowe umiejętności niezbędne do diagnozowania i rozwiązywania problemów sieciowych na podstawie analizy rzeczywistego ruchu pakietów.


