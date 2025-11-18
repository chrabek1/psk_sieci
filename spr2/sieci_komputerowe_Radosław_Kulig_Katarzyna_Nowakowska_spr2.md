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
Wprowadź swoją odpowiedź tutaj.
- _Jakie są wspólne informacje wymienione w sekcji TCP szczegółów PDU (PDU Details) w porównaniu do informacji wymienionych w zakładce OSI Model? Z którą warstwą jest to związane?_    
Wprowadź swoją odpowiedź tutaj.
- _Co to jest Host wymienione w sekcji HTTP PDU Datails ? Z jaką warstwą te informacje byłyby powiązane w ramach zakładki OSI Model?_  
## Wnioski

W ramach przeprowadzonych ćwiczeń zapoznaliśmy się z podstawowymi zasadami konfiguracji przełączników sieciowych Cisco oraz urządzeń końcowych. Nabyli praktyczne umiejętności w zakresie obsługi interfejsu CLI, konfiguracji adresacji IP, interfejsów VLAN, haseł dostępowych i banerów systemowych.

Przeprowadzone testy łączności (polecenie ping) potwierdziły poprawność konfiguracji oraz prawidłowe działanie połączeń między przełącznikami i komputerami w ramach jednej sieci lokalnej. Ćwiczenie pozwoliło nam również zrozumieć znaczenie stanu portów przełącznika oraz wpływ poprawnej konfiguracji warstwy drugiej modelu OSI na funkcjonowanie sieci.

Podsumowując, laboratorium umożliwiło utrwalenie podstawowych umiejętności administracyjnych niezbędnych do zarządzania infrastrukturą sieciową, a także zrozumienie mechanizmów odpowiedzialnych za przesyłanie danych w sieciach LAN.
