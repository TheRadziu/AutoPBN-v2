# **AutoPBN v2**
**Rewritten code, comes with ARM and x64 builds!**
![AutoPBN v2 preview](http://i.imgur.com/O43x1qz.png)
#### Current Versions:
Client/Loader - **1.06**  
Main Code - **2.00**

### 1. What is AutoPBN?
It's linux application that will control and watch over PokeBotNinja, making botting times more human-like.  
Thanks to that you can leave bots running on your favorite VPS or even raspberry pi, without necessity to check on it every few hours if there was an error/crash or not, and without fear of permban. 

### 2. Functions and features:
* AutoStop PBN after random period of time (customizable in config file, function can be disabled for risky infinite botting),
* AutoStart PBN after random period of time (customizable in config file),
* AutoRestart PBN in case of: failed login, api/hash error (customizable in config file) or in case of disconnect or crash,
* Full MultiAccount support, run as many different accounts with different settings on one PBN as you like!
* If AutoPBN was run with -config parameter, it will try to load settings from AutoPBN_jsonname.config [example: AutoPBN_MyOtherPogoAccount.config for MyOtherPogoAccount.json] if this file exists, otherwise it will load AutoPBN.config instead, 
* From v2 onwards, your AutoPBN will be always up to date, without need to look for or download new files! 
* Full logs available in AUTOPBN_LoadedJsonFilename.LOG files,
* json file verification (it will tell you if there is something crucial missing in loaded file like hash or password) [can be skipped with -skip parameter],
* Automatically adjust loaded json to fit AutoPBN requirements (enable AutoLogin and AutoStart and disable in-built autokill function),
* additional paremeters support (listed somewhere below),

### 3. Requirements: 
* Linux OS (tested on Ubuntu 16.04 and Raspbian Jessie) on x64 or ARM device,
* Pokebot.ninja (for multiAcc support use AT LEAST v96) with at least Gold benefits, 
* Already fully configured .json file (json configuration through AutoPBN will be added much later),

### 4. Installation and how to use it:
1. Download AutoPBN for ARM or x64 from [GitHub here](https://github.com/TheRadziu/AutoPBN-v2/releases/latest)
2. Extract its files to PokeBotNinja folder
3. Edit *AutoPBN.config* file (for linux: nano/vim | for windows: Notepad++ recommended) and set values as you like:
* **CHECK_VERIFY** - For purchased donate level (reminder: at least gold) or Multipatch leave it YES, for patched/modified PokeBotNinja set it NO,
* **AUTO_ENABLED** - YES - Enables AutoStop function | NO - Disables AutoStop function, PBN will run forever unless you press CTRL+C combo in AutoPBN window (note: with AutoStop disabled AutoPBN will still restart watch over PBN process (restart if crashed/dc/login error/hash or api error etc)
* **MIN_AUTOKILL** - Min time of Autostop function [default: 120](2 hours)
* **MAX_AUTOKILL** - Max time of Autostop function [default: 240](4 hours)
* **MIN_AUTOSTART** - Min time of Autostart function [default: 180](3 hours)
* **MAX_AUTOSTART** - max time of Autostart function [default: 300](5 hours)
* **TIMEOUT_LOGIN** - Set after how many seconds AutoPBN will check if login was successful [default: 60]
* **TIMEOUT_RETRIES** - Set how many times AutoPBN will try to reconnect in case of failed login before quitting. [default: 5]
4. *(optional if you already have fully configured PokeBotNinja)*  Run *./startbot.sh* to run PokeBotNinja normally and configure your json file (**important: tick remember password box**). Log in to your PTC/google account, save your settings and quit PBN.
5. Everything is now ready! From now on you can run PBN through AutoPBN via *./AutoPBN* and close it with CTRL + C combo.
6. *(optional)* In case of "Permission denied" error after issuing *./AutoPBN* command use *sudo chmod +x AutoPBN*

### 5. Startup parameters:
Example: *./AutoPBN -help*  
* config - loads specified .json file [example: *-config MyOtherPogoAccount.json*], can be used with *-skip* parameter,   
* help - displays list of currently available startup parameters with their brief description,  
* about - displays developer info and current AutoPBN main code version,  
* skip - skips .json verification [**for permanent skip of verification set CHECK_VERIFY as NO in your .config file!**]  
* api - Displays API information and link to the site where you can obtain your own api hash  
* ping - Pong!  
* pong - Ping?  

### 6. Changelog
[to be translated into english soon, for now enjoy it in beatiful Polish language :F]
```
02.04.17 - v2.00
-Przepisana wiekszość kodu, teraz AutoPBN korzysta z binarek a nie plików bash.
-Dodana funkcja autoaktualizacji głownego kodu.
-Dodane pełne wsparcie MultiAcc, teraz AutoPBN może być uzyte z jakimkolwiek plikiem konfiguracyjnym PokeBotNinja (wiecej informacji w punkcie 5)
-Poprawiłem wartosci typu YES/NO. Teraz mozna tez uzywać małych liter (yes/no).
-Dodano sprawdzanie wartosci liczbowych w plikach .config
-Poprawiłem kilka poprzednich check'ów - teraz informuje co jest nie tak.
29.03.17 - v1.22
-Dodana nowa opcja w pliku konfiguracyjnym "AUTO_ENABLED" - więcej informacji w punkcie 4 tego tematu.
-Skrypt wspiera teraz osobne pliki konfiguracyjne dla kazdego konta (w formie AutoPBN_nazwajson.config np. AutoPBN_MojePierwszeKonto.config (opcjonalnie, w razie braku pliku uzywany jest AutoPBN.config). Ta funkcja stanie sie funkcjonalna w momencie wprowadzenia pełnego supportu MultiAcc.
-W razie braku pliku konfiguracjnego AutoPBN.config, bot sam go utworzy z domyślnymi ustawieniami.
-Poprawki kodu, głupie błędy logiczne. 
28.03.17 - v1.21 hotfix
-Poprawiłem brzydką literówkę w jednej funkcji + kilka innych usprawnień kodu.
28.03.17 - v1.21
-Dodałem trochę wsparcia dla kilku klientów PokeBotNinja uruchomionych w tym samym momencie - teraz AutoPBN uzywa osobnych .pid dla kazdego uruchomionego bota. 
-Pliki z logami posiadają teraz w nazwie nazwę pliku json na którym jest uruchomiony bot (przygotowania dla pełnego supportu MultiACC)
-!!plik konfiguracyjny jest teraz osobnym plikiem AutoPBN.config!!
-Skrypt teraz wyswietla dokładnie o której godzinie bot będzie zatrzymany lub uruchomiony.
-Pliki tymczasowe AutoPBN nie będą juz zawalać folderu z botem :) (wyrzuciłem je do pełnoprawnego folderu tymczasowego /tmp/)​
-Bot sprawdza czy został uruchomiony w terminalu i jeśli nie to odmówi uruchomienia. (to jest fix dla problemu z brakiem kontroli nad skryptem i botem)
05.03.17 - v1.20
-Dodałem wsparcie dla wersji cracked. Wymaga zmiany wartosci CHECK_VERIFY.
-Nowy parametr startowy 'api' - wyswietla informacje i link do aktualnego api (./AutoPBN.sh -api)
05.03.17 - v1.19
-Skrypt teraz wyswietla swoją nazwę, wersję i aktualny status w tytule okna. 
-Czas do AutoStartu lub AutoStop'u jest teraz wyświetlany w godzinach w formie hh mm (np. 3h33m)
-Dodałem wsparcie dla parametrów startowych (np. './AutoPBN.sh -skip' by pominąć weryfikację konfiguracji PokeBotNinja. Wszystkie dostępne parametry znajdziecie w punkcie 5 tego tematu.
-Skrypt daje sobie już radę z bezposrednim uruchamianiem (dwuklik -> 'run in terminal')
-W przypadku niepomyślnej weryfikacji pliku konfiguracyjnego PokeBotNinja, błedy są od teraz logowane do AUTOPBN.LOG
05.03.17 - v1.18
-Dodałem weryfikację konfiguracji PokeBotNinja, dzięki czemu będzie mniej postów typu "EJ ZIOMEK NIE DZIAŁA MI DLACZEGO EYYYYYY". Nową fukcją jest również automatyczne włączenie autologinu i/lub autostartu bota(w razie kiedy są wyłączone) który jest wymagany do poprawnego działania skryptu. A na koniec dodałem nowe zmienne(TIMEOUT_RETRIES) i poprawiłem stare (TIMEOUT_LOGIN) - po więcej informacji odsyłam do punktu 4 tego postu.
04.03.17 - v1.17 hotfix1
-Poprawiłem trochę literówek, i błąd który czasami powodował że bot uruchamiał się dwukrotnie.
04.03.17 - v1.17
-Skrypt teraz daje sobie radę z błędami logowania (bład hash/API lub nieudane logowanie), Poprawki logów (AUTOPBN.LOG)
04.03.17 - v1.14
-Pierwsze publiczne wydanie
```

### 7. Todo list:
- [ ] Add RAM limit for single PokeBotNinja instance (customizable via config file)
- [ ] Add json configuration via AutoPBN, so running PokeBotNinja at least once will no longer be required. 
