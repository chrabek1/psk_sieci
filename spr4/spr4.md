# Politechnika Świętokrzyska w Kielcach
## Wydział Zarządzania i Modelowania Komputerowego
##### Sieci Komputerowe
##### Laboratorium
#### Obliczanie podsieci IPv4
#### Praktyka projektowania i wdrażania VLSM
#### Konfiguracja adresacji IPv6
#### Stosowanie komendy ping oraz traceroute do testowania połączeń w sieci
####
![](https://tu.kielce.pl/wp-content/uploads/2018/03/logo_psk.jpg)
Przygotowali: 
 
| Imię i Nazwisko     | Nr albumu| 
| -------------- | ------- |
| Radosław Kulig | 093795 |
| Katarzyna Nowakowska | 096946 |  
 
Kierunek: Inżynieria Danych
 
Studia: stacjonarne
 
Data wykonania ćwiczenia: 27.01.2026
 
*Oświadczam, że:*
 
*Sprawozdanie niniejsze zostało wykonane przeze mnie osobiście. Zamieszczone w sprawozdaniu wyniki badań zostały uzyskane przeze mnie podczas wykonywania zadań laboratoryjnych.*  
*Radosław Kulig*  
*Katarzyna Nowakowska*  
***
## Lab 11.6.6 Obliczanie podsieci IPv4
### Wstęp teoretyczny
Protokół IPv4 (Internet Protocol version 4) stanowi fundament komunikacji w większości współczesnych sieci komputerowych. Jest on odpowiedzialny za adresowanie urządzeń w taki sposób, aby dane mogły bezbłędnie trafić od nadawcy do odbiorcy. Adres IPv4 jest unikalnym identyfikatorem składającym się z 32 bitów. Dla ułatwienia zapisu bity te dzieli się na cztery części, zwane oktetami (po 8 bitów każdy), oddzielone kropkami. Każdy oktet może przyjmować wartość od 0 do 255 w systemie dziesiętnym.
Adresowanie w systemie IPv4 opiera się na strukturze hierarchicznej, co oznacza, że każdy adres składa się z dwóch części:

+ Części sieciowej (prefiks sieciowy): Identyfikuje konkretną sieć lub podsieć.

+ Części hosta: Identyfikuje konkretne urządzenie (interfejs) w tej sieci.

O tym, gdzie kończy się część sieciowa, a zaczyna część hosta, decyduje maska podsieci. Składa się ona z ciągu jedynek (część sieciowa) i zer (część hosta).

<img width="869" height="527" alt="image" src="https://github.com/user-attachments/assets/1f79ce63-40a9-4b36-ae61-e98bc7bee165" />
<img width="870" height="526" alt="image" src="https://github.com/user-attachments/assets/fe384b12-ebd0-458e-96d5-ac1a861d577f" />
<img width="874" height="529" alt="image" src="https://github.com/user-attachments/assets/93a976ae-cc4f-4389-81f9-c50e0cf0dd08" />
<img width="869" height="532" alt="image" src="https://github.com/user-attachments/assets/829eed34-752d-406c-a9dc-489c08e844b3" />
<img width="876" height="527" alt="image" src="https://github.com/user-attachments/assets/5b960874-5d75-4dc6-94d6-b8f6d2729775" />
<img width="860" height="526" alt="image" src="https://github.com/user-attachments/assets/09aa696d-520b-4789-b8a0-c2ed5b44a977" />

-_Dlaczego tak istotne jest analizowanie masek podsieci adresów IPv4?_
> Analizowanie masek podsieci jest kluczowe dla prawidłowego funkcjonowania i projektowania sieci komputerowych, ponieważ to właśnie maska pozwala urządzeniom sieciowym zinterpretować strukturę adresu IP.

### Wnioski
Ćwiczenie potwierdziło, że umiejętność określania adresów hostów oraz sieci na podstawie adresu IP i maski jest kluczem do zrozumienia działania sieci IPv4. Sama znajomość adresu IP bez maski nie pozwala na określenie przynależności urządzenia do konkretnego segmentu sieci.

## PT 11.9.3 Praktyka projektowania i wdrażania VLSM
### Wstęp teoretyczny
VLSM (Variable Length Subnet Mask), czyli maski podsieci o zmiennej długości, to technika pozwalająca na bardziej efektywne zarządzanie przestrzenią adresową. W tradycyjnym podejściu do adresowania sieciowego (tzw. adresowanie klasowe lub stałe podsieci FLSM), każda wydzielona część sieci otrzymuje taką samą liczbę adresów, niezależnie od tego, czy faktycznie ich potrzebuje. W praktyce prowadzi to do sytuacji, w której małe biuro (np. 5 komputerów) i duże piętro (np. 100 komputerów) otrzymują identyczną pulę adresów, co drastycznie marnuje dostępne zasoby.
VLSM to technika, która pozwala "ciąć" sieć na kawałki o różnych rozmiarach. Zamiast jednej sztywnej maski dla całej topologii, stosujemy maski o zmiennej długości, precyzyjnie dopasowane do liczby hostów w danej sieci LAN lub na łączu WAN.

Zapoznajemy się z udostępnioną topologią oraz tabelą adresowania. 

<img width="703" height="411" alt="image" src="https://github.com/user-attachments/assets/4475fe9a-4512-4d40-ab34-f44cb8cead91" />

Dobieramy odpowiednie maski podsieci dla poszczególnych segmentów sieci tak, aby zapewnić wystarczającą liczbę użytecznych adresów IP.

-_Jaka maska podsieci spełni wymagania ilości adresów IP w sieciach oraz ile używalnych adresów zapewnia ta podsieć?_
>ASW-1: maska 255.255.255.224 (/27), 30 użytecznych adresów
>
>ASW-2: maska 255.255.255.224 (/27), 30 użytecznych adresów
>
>ASW-3: maska 255.255.255.240 (/28), 14 użytecznych adresów
>
>ASW-4: maska 255.255.255.240 (/28), 14 użytecznych adresów
>
>Building1–Building2: maska 255.255.255.252 (/30), 2 użyteczne adresy

W następnym kroku wykonujemy podział sieci bazowej 172.31.103.0/24 na mniejsze podsieci. Podział został wykonany techniką VLSM, rozpoczęto go od podsieci o największej liczbie hostów, a kolejne podsieci przydzielano w następnych dostępnych zakresach adresów. 
Następnie uzupełniamy tabelę podsieci.

<img width="803" height="273" alt="image" src="https://github.com/user-attachments/assets/f4544b8d-c9e0-4a5d-8597-8d91c057d950" />


W celu udokumentowanie schematu adresowania przypisuemy adresy IP do urządzeń w każdej podsieci zgodnie z wytycznymi instrukcji.

<img width="800" height="583" alt="image" src="https://github.com/user-attachments/assets/8b199fcd-6083-47e8-8912-d880de2dabc2" />

### Wnioski
Projektowanie sieci z wykorzystaniem techniki VLSM uczy, jak przestać marnować adresy IP poprzez porzucenie sztywnego podziału na równe podsieci na rzecz elastycznego dopasowania maski do faktycznej liczby hostów. Głównym wnioskiem z zadania jest to, że kluczem do sukcesu jest zachowanie hierarchii — planowanie adresacji należy zawsze zaczynać od największych segmentów sieci, stopniowo przechodząc do najmniejszych, w tym dwuadresowych łącz WAN. Poprawnie wykonane ćwiczenie dowodzi, że systematyczne dokumentowanie pierwszych i ostatnich użytecznych adresów w tabeli adresowania jest niezbędne do sprawnego skonfigurowania urządzeń i uzyskania pełnej łączności w całej topologii.

## PT 12.6.6 Konfiguracja adresacji IPv6
### Wstęp teoretyczny
Przejście z protokołu IPv4 na IPv6 to nie tylko zmiana długości adresu, ale przede wszystkim ewolucja sposobu, w jaki urządzenia komunikują się w sieci. Ćwiczenie to skupia się na praktycznym wdrożeniu tej adresacji w topologii typu gwiazda, łączącej sieć lokalną z Internetem (ISP). W protokole IPv6 standardem dla sieci lokalnych (LAN) jest prefiks /64. Oznacza to, że pierwsze 64 bity adresu definiują sieć, a pozostałe 64 bity są zarezerwowane dla identyfikatora interfejsu urządzenia. Urządzenia Cisco domyślnie mają włączony protokół IPv4, ale obsługa IPv6 wymaga ręcznej aktywacji. Kluczowym krokiem jest wydanie komendy ipv6 unicast-routing. Bez niej router zachowuje się jak zwykły komputer – nie będzie przekazywał pakietów między swoimi interfejsami GigabitEthernet i Serial.

Na początku klikamy na R1, a nastepnie zakładkę CLI. Przechodzimy do trybu uprzywilejowanego. Wprowadzamy komende, która musi być skonfigurowana, aby router mógł przesyłać pakiety IPv6.

<img width="314" height="29" alt="image" src="https://github.com/user-attachments/assets/515094ca-2fb2-4410-ae6b-55c86336d0b0" />

Teraz będziemy konfigurować adresacje IPv6 na GigabitEthernet0/0. Wprowadzamy polecenia niezbędne do przejścia do trybu konfiguracji interfejsu dla GigabitEthernet0/0. Konfigurujemy adres IPv6 korzystając z poniższego polecenia: 
R1(config-if)# ipv6 address 2001:db8:1:1::1/64. Następnie konfigurujemy adres lokalnego łącza IPv6 (ang. link-local address) korzystając z polecenia: R1(config-if)# ipv6 address fe80::1 link-local. Na końcu uaktywniamy interfejs.

<img width="624" height="129" alt="image" src="https://github.com/user-attachments/assets/eb262596-e92c-4693-84b8-142e1c45495b" />

Konfigurujemy adresacje IPv6 na GigabitEthernet0/1. Wprowadzamy polecenia niezbędne do przejścia do trybu konfiguracji interfejsu dla GigabitEthernet0/1. Konfigurujemy adres IPv6, adres lokalnego łącza i uaktywniamy interfejs.

<img width="624" height="141" alt="image" src="https://github.com/user-attachments/assets/b89e9814-4bc3-4b20-a9c8-696ff7410833" />


Konfigurujemy adresacje IPv6 na Serial0/0/0. Wprowadzamy polecenia niezbędne do przejścia do trybu konfiguracji interfejsu dla Serial0/0/0. Konfigurujemy adres IPv6, adres lokalnego łącza i uaktywnij interfejs.

<img width="606" height="143" alt="image" src="https://github.com/user-attachments/assets/a0be556a-083d-4f42-a633-ae9e25fbca1e" />

Weryfikujemy adresowanie IPv6 na R1. Wychodzimy z trybu konfiguracji na R1
Musimy zweryfikować adresowanie skonfigurowane. Jeśli jakiekolwiek adresy są niepoprawne, powtarzamy powyższe kroki w razie potrzeby, aby wprowadzić poprawki.
Zapisujemy konfigurację routera w pamięci NVRAM.

<img width="409" height="330" alt="image" src="https://github.com/user-attachments/assets/881e1f5b-7412-487a-a247-47421d42e7e4" />


Teraz skonfigurujemy adresację IPv6 na serwerze Accounting. Klikamy Accounting następnie zakładka Desktop  > IP Configuration. W polu IPv6 Address wprowadzamy adres postaci 2001:DB8:1:1::4 z prefiksem /64. W polu IPv6 Gateway wprowadzamy adres lokalnego łącza postaci, FE80::1.

<img width="669" height="160" alt="image" src="https://github.com/user-attachments/assets/b6951f55-1b38-47c4-b93c-46e8cd24134b" />

Konfigurujemy serwer CAD z adresami, jak to zostało zrobione w poprzednim kroku.

<img width="656" height="159" alt="image" src="https://github.com/user-attachments/assets/1fd96e4c-aa66-4449-a671-af06a1f46557" />

Klikamy komputer Billing, następnie wybieramy zakładkę Desktop a potem IP Configuration. W polu IPv6 Address wprowadzamy adres postaci 2001:DB8:1:1::3 z prefiksem /64. W polu IPv6 Gateway wprowadzamy adres link-local FE80::1.
Powtarzamy poprzednie kroki dla komputera Sales. 

<img width="669" height="165" alt="image" src="https://github.com/user-attachments/assets/4099459c-b20a-41e6-b3c9-1e486a4259ca" />

Klikamy komputer Engineering, następnie wybierz zakładkę Desktop a potem IP Configuration. W polu IPv6 Address wprowadzamy adres postaci 2001:DB8:1:2::3 z prefiksem /64, a polu IPv6 Gateway adres link-local FE80::1. Powtarzamy kroki dla komputera Design.

<img width="677" height="162" alt="image" src="https://github.com/user-attachments/assets/aedcf904-e478-48d9-9bda-f761c0f0a102" />

Klikamy Sales a następnie kliknij zakładkę Desktop . 
Klikamy Web Browser. W polu URL wprowadzamy 2001:DB8:1:1::4 i klikamy przycisk Go. Powinna się pojawić strona WWW serwera Accounting.

<img width="697" height="213" alt="image" src="https://github.com/user-attachments/assets/88fad12c-e3dc-4f5d-88ee-6fe04a87e7b9" />

W polu URL wprowadzamy 2001:DB8:1:2::4 i klikamy przycisk Go. Powinna się pojawić strona WWW serwera CAD.

<img width="683" height="206" alt="image" src="https://github.com/user-attachments/assets/89a28818-5604-4657-8f75-9e91712ebe58" />

Powtarzamy kroki dla pozostałych klientów.

<img width="697" height="205" alt="image" src="https://github.com/user-attachments/assets/7870b0b6-678d-4e86-97f2-83e5b04cdf99" />
<img width="691" height="203" alt="image" src="https://github.com/user-attachments/assets/dc8412cf-2edf-41b3-9ba5-d0b4293a6fd8" />
<img width="687" height="200" alt="image" src="https://github.com/user-attachments/assets/d590349b-8629-4713-ae6c-9521c0d2ee35" />
<img width="696" height="216" alt="image" src="https://github.com/user-attachments/assets/00560273-6d24-4384-8e1e-d1a6426ce22b" />
<img width="699" height="211" alt="image" src="https://github.com/user-attachments/assets/dcec9da6-a332-48ea-82d0-172423946b5b" />
<img width="693" height="206" alt="image" src="https://github.com/user-attachments/assets/dfc6ed3d-1422-455f-a8a5-b741f24175b3" />


Klikamy na dowolnego klienta. Wybieramy zakładkę Desktop > Command Prompt.
Testujemy połączenie z ISP, wpisując komendę:K PC> ping 2001:db8:1:a001::1

<img width="620" height="351" alt="image" src="https://github.com/user-attachments/assets/6eaaf68d-d67c-49f1-9a5f-cea0328cbc18" />
<img width="610" height="343" alt="image" src="https://github.com/user-attachments/assets/512d95ce-d1d1-447c-8c73-3a47878216bd" />
<img width="647" height="366" alt="image" src="https://github.com/user-attachments/assets/bbb2c14e-8a46-41b2-8b68-e9b3b6e55f2c" />
<img width="599" height="332" alt="image" src="https://github.com/user-attachments/assets/19b92225-a423-4fdd-b3dc-e1f9a0fbfea8" />

Powtarzamy komendę ping dla pozostałych klientów by w pełni zweryfikować łączność.

### Wnioski
Ćwiczenie to koncentruje się na praktycznym wdrożeniu protokołu IPv6, co wymaga przede wszystkim aktywacji routingu na routerze poleceniem ipv6 unicast-routing. Konfiguracja opiera się na przypisaniu interfejsom routera R1 oraz urządzeniom końcowym adresów Global Unicast do komunikacji zewnętrznej oraz adresów Link-Local (fe80::1) do komunikacji wewnątrz lokalnych segmentów sieci. Głównym wnioskiem z zadania jest efektywność wykorzystania adresu Link-Local jako bramy domyślnej dla wszystkich hostów, co ujednolica konfigurację w różnych podsieciach. Testy końcowe, obejmujące dostęp do stron WWW serwerów Accounting i CAD oraz komunikację z adresem ISP, potwierdzają, że poprawnie zdefiniowana adresacja i routing umożliwiają pełną łączność w nowym standardzie protokołu IP. Istotnym aspektem technicznym jest również fakt, że w IPv6 błędne adresy nie są automatycznie nadpisywane, co wymusza na administratorze ich ręczne usuwanie w celu uniknięcia konfliktów.

## PT 13.2.7 Stosowanie komendy ping oraz traceroute do testowania połączeń w sieci
### Wstęp teoretyczny
Głównym celem scenariusza jest przywrócenie pełnej łączności w środowiskach IPv4 oraz IPv6 poprzez identyfikację błędów w konfiguracji urządzeń końcowych i pośredniczących. Proces ten rozpoczyna się od zbierania informacji o bieżącym stanie sieci za pomocą narzędzi weryfikacyjnych, takich jak polecenia ipconfig i ipv6config, które pozwalają na odczytanie przypisanych adresów IP, masek podsieci oraz bram domyślnych.
Kluczowym elementem diagnostyki jest wykorzystanie protokołu ICMP poprzez polecenie ping, służące do sprawdzania podstawowej drożności kanału komunikacyjnego między hostami. W przypadku wystąpienia awarii, narzędzie traceroute umożliwia precyzyjne śledzenie trasy pakietu i wskazanie konkretnego urządzenia, na którym następuje przerwanie transmisji. Analiza ta, uzupełniona o wgląd w tablice routingu routerów (polecenie show ip route) oraz status ich interfejsów (polecenie show ip interface brief), pozwala na wykrycie rozbieżności między stanem faktycznym a dokumentacją techniczną zawartą w tabeli adresowania. Ostatecznym etapem jest wdrożenie odpowiednich poprawek konfiguracyjnych i ponowna weryfikacja stabilności połączeń, co gwarantuje poprawność działania całej infrastruktury sieciowej.

<img width="796" height="325" alt="image" src="https://github.com/user-attachments/assets/f98401b8-4d47-47a6-9d3c-9e63900da323" />

Adresy i prefiksy oraz bramy domyślne dla PC1, PC2, PC3 i PC4 w tabeli zostały uzupełnione ręcznie zgodnie z poleceniami.

<img width="754" height="622" alt="image" src="https://github.com/user-attachments/assets/16ac83e7-b137-4596-a09f-e766da57ccb3" />

Klikamy PC1 i otwieramy Command Prompt. WPisujemy polecenie ipconfig /all, aby zebrać informacje IPv4. 

<img width="888" height="363" alt="image" src="https://github.com/user-attachments/assets/7fe88f27-b3ac-4234-a436-77851c58cb41" />

Powtarzamy dla PC3.

<img width="886" height="383" alt="image" src="https://github.com/user-attachments/assets/46b3e60d-2665-429d-a43c-0dcc2eb3aeae" />

Używamy polecenia ping, aby przetestować łączność między PC1 i PC3. Test ping powinien zakończył się niepowodzeniem.

<img width="655" height="233" alt="image" src="https://github.com/user-attachments/assets/a4525431-d760-48b8-8446-60e76fca28aa" />

W celu zlokalizowania problemu, wykonujemy polecenia tracert z jednego komputera na drugi i z powrotem.
PC1 do PC3: 

<img width="623" height="541" alt="image" src="https://github.com/user-attachments/assets/f054f623-4ffa-4c6e-a8ac-f3eafbd59ac5" />

PC3 do PC1: 

<img width="613" height="258" alt="image" src="https://github.com/user-attachments/assets/00c39b00-152b-4dd4-954a-3eb8b4125c01" />

 
W dalszym poszukiwaniu problemu, logujemy się do Routera 1 oraz Routera 2 za pomocą haseł podanych na początku instrukcji. Po zalogowaniu się używamy komend show ip interface brief, aby zobaczyć informacje odnośnie interfejsów oraz show ip route do wyświetlenia sieci podłączonych pod router. 

Router 1:

<img width="898" height="270" alt="image" src="https://github.com/user-attachments/assets/9729af0e-0def-477f-9bc9-abe4e3306f81" />
<img width="881" height="341" alt="image" src="https://github.com/user-attachments/assets/8f64ff6f-8acf-4957-9ec6-720ca02f1c5d" />

Router 2:

<img width="908" height="273" alt="image" src="https://github.com/user-attachments/assets/0234bdcd-88e6-42a9-8fd0-311df60e037a" />
<img width="881" height="380" alt="image" src="https://github.com/user-attachments/assets/79dc27a0-e5d4-4c5f-bc9c-f4b159ffc73a" />

-_(2a)Jaki jest ostatni osiągnięty adres IPv4?_
>10.10.1.97 
-_(2c)Jaki jest ostatni osiągnięty adres IPv4?_
>10.10.1.17
-_(2f)Jaki jest drugi?_
>10.10.1.6
-_(2g)Jakie to pozycje?
>10.10.1.4/30 typu C oraz 10.10.1.6/32 typu L
-_(2h)Jakie to pozycje?
>10.10.1.8/30 typu C oraz 10.10.1.10/32 typu L

Porównujemy odpowiedzi z kroku 2 do danych z dokumentacji, którą mamy dostępną dla tej sieci.
-_Jaki jest błąd?_
>Adres IPv4 dla Routera R2 w interfejsie S0/0/0 jest inny niż w dokumentacji. 
-_Jakie rozwiązanie proponujesz, aby rozwiązać problem?_
>Zmiana adresu.

Teraz wykonujemy nasz plan.

<img width="933" height="464" alt="image" src="https://github.com/user-attachments/assets/4d57b3b9-9baa-4ea7-bb08-eb15347c99db" />

Upewniamy że łączność została przywrócona. Testujemy łączność z PC1 do PC3, a nastepnie z PC3 do PC1.

<img width="642" height="275" alt="image" src="https://github.com/user-attachments/assets/d7f71085-c491-4782-9345-07b2853d294d" />
<img width="624" height="277" alt="image" src="https://github.com/user-attachments/assets/6396fdcf-3168-4587-9aec-592ac8a680cc" />

-_Czy problem został rozwiązany?_
>Problem został rozwiązany, co potwierdzają pingi.

Klikamy PC2 i otwórz Command Prompt, wprowadzamy polecenie ipv6config /all, aby zebrać informacje o IPv6.

<img width="875" height="508" alt="image" src="https://github.com/user-attachments/assets/86454bb4-6968-4d7f-9350-745a0d88845c" />

Powtarzamy na PC4:

<img width="900" height="506" alt="image" src="https://github.com/user-attachments/assets/55ec066d-3be8-4869-8ad1-bc2fe81423f9" />

Testujemy łączność między PC2 i PC4. Ten test ping znowu zakończył się niepowodzeniem.

<img width="652" height="239" alt="image" src="https://github.com/user-attachments/assets/44b24e54-9cc8-40da-b1a6-32fa29e7438e" />

Lokalizujemy źródło problemu. Tak jak w poprzedniej części zadania problem leży w komunikacji pomiędzy tymi dwoma urządzeniami. W celu weryfikacji problemu ponownie używamy polecenia tracert z jednego urządzenia na drugie. 
PC2 do PC4:

<img width="656" height="233" alt="image" src="https://github.com/user-attachments/assets/90f07b6f-6c97-4915-bfa9-122bacc10a55" />

PC4 do PC2: 

<img width="669" height="144" alt="image" src="https://github.com/user-attachments/assets/e12a2ed4-7f11-4c9e-9035-5f1ea5d5f67e" />

W kolejnych próbach rozpoznania problemu, nastąpiło zalogowanie do Routera 3 oraz Routera 1.
Dla routera 1:

<img width="623" height="389" alt="image" src="https://github.com/user-attachments/assets/2ec907ee-daa6-47c2-b972-460426ed53d6" />

Dla router 3:

<img width="633" height="333" alt="image" src="https://github.com/user-attachments/assets/a0095934-a815-488d-96c5-69f84a6fdbbc" />
<img width="903" height="557" alt="image" src="https://github.com/user-attachments/assets/8c2ff432-7834-4035-b54a-7a65e2f259b4" />

-_(2a)Jaki jest ostatni osiągnięty adres IPv6?_
>2001:DB8:1:3::2
-_(2c)Jaki jest ostatni osiągnięty adres IPv6?_
> Nie został osiągnięty żaden adres.
-_Czy jest inaczej?_
> Nie ma żadnego adresu zgodnego z bramą zapisaną we wcześniejszym poleceniu.

Brama domyślna adresu IPv6 na komputerze PC4 nie zgadza się. Propozycją rozwiązania problemu jest jej zmiana tak, aby była zgodna z bramą domyślną Routera R3. 

<img width="945" height="245" alt="image" src="https://github.com/user-attachments/assets/2c70c95a-0a74-457e-9e5b-702dbdc42900" />

Przed rozwiązaniem problemu adres był niezgodny z tym z tabeli adresowania, natomiast oo zmianie pingi się udały. Oznacza to całkowite wyeliminowanie problemu
PC2 do PC4: 

<img width="616" height="275" alt="image" src="https://github.com/user-attachments/assets/29c8452f-c973-45d5-b9e9-8ec0b3d70cda" />

PC4 do PC2: 

<img width="630" height="272" alt="image" src="https://github.com/user-attachments/assets/288d98d7-afd6-460a-b095-c44b6b0c25f2" />

### Wnioski
Na podstawie przeprowadzonych czynności diagnostycznych w ramach instrukcji można stwierdzić, że kluczem do sprawnego funkcjonowania sieci jest ścisła zgodność konfiguracji z dokumentacją techniczną. Ćwiczenie wykazało, że narzędzia takie jak ping i tracert są niezbędne do precyzyjnego lokalizowania punktów awarii. Pozwoliły one ustalić, że w przypadku IPv4 problemem był błędny adres IP na interfejsie szeregowym routera R2 , natomiast w części dotyczącej IPv6 przyczyną braku łączności była nieprawidłowo skonfigurowana brama domyślna na komputerze PC4. Skuteczna naprawa wymagała systematycznej analizy statusu interfejsów oraz tablic routingu, co pozwoliło na wykrycie rozbieżności i wdrożenie poprawek przywracających pełną drożność kanałów komunikacyjnych. Ostateczne testy potwierdziły, że prawidłowe adresowanie, uwzględniające techniki takie jak VLSM oraz właściwe przypisanie bram domyślnych, stanowi fundament stabilnej i wydajnej infrastruktury sieciowej



