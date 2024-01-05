# Port-Przekierowany
## Wstęp
Niniejsza instrukcja opisuje sposób połączenia się ze sterownikiem poprzez port przekierowany. W pierwszym rozdziale podana jest przykładowa topologia sieci służącej do połączenia ze sterownikiem, dalej opisane są porty, które należy przekierować w celu uzyskania konkretnych funkcjonalności sterownika, a następnie opisany jest sposób przykładowej konfiguracji routera i połączenia się ze sterownikiem z Windows CE.

## Przykłądowa topologia

![image](https://github.com/BA-PL/Port-Przekierowany/assets/155453679/d73265a0-68a7-408e-af19-4a956aa9e806)

## Porty wykorzystywane w Beckhoff 

[Infosys](https://infosys.beckhoff.com/english.php?content=../content/1033/ipc_security_wince/11019143435.html)

## Przykładowe ustawienie routera

![image](https://github.com/BA-PL/Port-Przekierowany/assets/155453679/eb52c3fd-5f3a-4d87-8503-546b8c07dd49)

## Nawiązywanie połączenia z urządzeniem wyposażonym w system operacyjny Windows CE

Aby nawiązać połączenie musimy dodać wpis o połączeniu w rejestrze systemu Windows. Do tego celu wykorzystujemy  program  TwinCAT  System  Manager.  Wybieramy  w  nim  opcję  Choose  Target System\Search(Ethernet) i uzupełniamy odpowiednie pola w oknie Add Route Dialog – opis poniżej. Wpisów musimy dokonać ręcznie, nie zadziała w tym przypadku komenda Broadcast Search.

![image](https://github.com/BA-PL/Port-Przekierowany/assets/155453679/17391b10-9dfd-4f68-8ce7-0b4a72903022)

Kolejne kroki: 
1.   Wpisujemy adres zewnętrznego IP urzadzenia 
2.   Wciskamy przycisk Enter Host Name/IP 
3.   Wyświetli się nam nazwa sieciowa urządzenia, z którym chcemy się połączyć 
4.   Wybieramy dodawanie po IP Address 
5.   Wciskamy przycisk Add Router 
6.   W polu Connected może nie pojawić się znak „X” oznaczający nawiązanie połączenie.

Połączenie nie jest jeszcze aktywne, co pokazuje pasek stanu w oknie głównym:
![image](https://github.com/BA-PL/Port-Przekierowany/assets/155453679/2e163325-1318-49fc-a079-97b697aa9383)
Spowodowane jest to tym, że w rejestrach urządzenia wpisany jest wewnętrzny adres IP naszego komputera, a powinien być wpisany zewnętrzny adres IP routera do którego komputer jest podłączony. Zmian dokonujemy w następnym kroku.

## Modyfikacja wpisu w rejestrze Windows CE

Uwaga!! 
Obrazy Windows CE od wersji TwinCAT 2.11. 2243 lub TwinCAT 3.1 Build 4016.6 mają fabrycznie zablokowany dostęp  zdalny  za  pomocą  programu  CERHOST.  Dalsze  czynności  nie  będą  możliwe.
Instrukcja odblokowania: [Infosys](https://infosys.beckhoff.com/english.php?content=../content/1033/cx51x0_hw/6436348939.html) 
Odnajdujemy wpis w rejestrze dotyczący połączenia z naszym komputerem (w tym przypadku jest to folder DELL) 
Zmieniamy wpis dotyczący adresu IP - powinien zawierać zewnętrzny adres IP routera za którym znajduje się komputer, z którego programujemy sterownik. Adres ten można sprawdzić np. na stronie www.mojeip.cz.
![image](https://github.com/BA-PL/Port-Przekierowany/assets/155453679/44fb3961-5f56-4e0a-8ff8-c21ab5276e02)
Resetujemy system:
![image](https://github.com/BA-PL/Port-Przekierowany/assets/155453679/812e24f2-18db-4022-b3c7-f98d6b9e9602)
W   programie   TwinCAT   System   Manager   widzimy,   że   nawiązane   jest   połączenie   z   urządzeniem:
![image](https://github.com/BA-PL/Port-Przekierowany/assets/155453679/3cc8170a-fd1b-4e3c-86cb-30cf728a1888)







