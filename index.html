Dziś przedstawię jak w prosty sposób uruchomić Wordpressa w kontenerze Docker. Co nam daje konteneryzacja? Przede wszystkim całkowite wyseparowanie procesów. Inaczej rzecz ujmując - nie musimy zaśmiecać lokalnego komputera silnikiem bazy danych, serwerem HTTP, interpreterem PHP (w dodatku w różnych wersjach), poszczególnymi modułami i komponentami PHP, itd. Czyli możemy stworzyć całe środowisko do web developmentu bez instalowania wszystkich niezbędnych komponentów bezpośrednio w systemie i swobodnie przełączać się między tymi środowiskami.

Stworzymy sobie środowisko, które będzie zawierało serwer HTTP (w tym przypadku chyba Apache), interpreter php w wersji 7, oraz silnik bazy danych MySQL w wersji 5.7. Wszystko to będzie umieszczone i uruchomione wewnątrz kontenera i nic nam nie zaśmieci naszego systemu.

Do tego celu użyjemy Dockera. Samego procesu instalacji Dockera nie będę tutaj opisywał, odsyłam do dokumentacji. W naszym przykładzie użyjemy docker-compose, czyli zainstalujemy wszystkie niezbędne moduły nie z linii poleceń, tylko z wcześniej przygotowanego pliku yml. Plik taki powinien nazywać się docker-compose.yml. Ja zawsze tworzę sobie katalog z projektem (w tym przypadku Wordpress) i wewnątrz tego katalogu umieszczam plik docker-compose.yml. Plik ten zawiera wszystkie niezbędne rzeczy do uruchomienia Wordpressa i wygląda następująco:



```yml
version: '3'
services:
  wordpress:
    depends_on:
    	- db
    image: wordpress:latest
# 	restart: always
	volumes:
 		- ./uploads.ini:/usr/local/etc/php/conf.d/uploads.ini
 		- ./public_html:/var/www/html
	environment:
  		WORDPRESS_DB_HOST: db:3306
  		WORDPRESS_DB_USER: user
  		WORDPRESS_DB_PASSWORD: password
	ports:
  		- 80:80
	networks:
  		- back

  db:
    image: mysql:5.7
# 	restart: always
	volumes:
   		- db_data:/var/lib/mysql
	environment:
  		MYSQL_ROOT_PASSWORD: p4ssw0rd!
  		MYSQL_DATABASE: wordpress
  		MYSQL_USER: user
  		MYSQL_PASSWORD: password
	networks:
  		- back

  phpmyadmin:
	depends_on:
    - db
    image: phpmyadmin/phpmyadmin
#	restart: always
	ports:
  		- 8080:80
	environment:
  		PMA_HOST: db
  		MYSQL_ROOT_PASSWORD: p4ssw0rd!
	networks:
  	- back
networks:
  back:
volumes:
  db_data:
```

Teraz po kolei co tu mamy z tych najważniejszych rzeczy:

- version: '3' - jest to wersja składni Dockera. W zasadzie nas to nie interesuje w tym momencie.

Dalej mamy wymienione usługi, które zostaną zainstalowane, a mamy ich 3:

- wordpress
- db - czyli silnik bazy danych
- phpmyadmin - wiadomo po co

W przypadku usługi Wordpress mamy  następujące parametry:

- depends_on: -db 

  Określa nam zależność pomiędzy usługami. W tym przypadku po uruchomieniu dockera z ustawieniami z naszego pliku usługi zostaną uruchomione w kolejności biorącej pod uwagę zależności. Czyli najpierw uruchomi się silnik bazy danych, a później Wordpress. Gdybyśmy nie dali tej zależności, Wordpress mógłby się nie uruchomić, bo nie zadziała bez bazy danych. W przypadku Worpdressa nie ma jeszcze takiego problemu, ale są inne aplikacje, które po prostu nie wstaną bez działającego silnika bazy danych i wtedy ten parametr jest po prostu konieczny.

- image: worpdress:latest

  Tutaj mamy wskazanie obrazu, który ma się pobrać. W skrócie - żeby uruchomić kontener z działającą aplikacją, należy mieć obraz (można go zbudować samemu, można pobrać z tzw. internetu). Obraz pobiera się tylko raz, chyba, że go usuniemy. Baza obrazów znajduje się tutaj https://hub.docker.com/

- #restart: always

  Oznacza, że kontener powinien się automatycznie uruchamiać po starcie systemu. W moim pliku jest to zakomentowane, ponieważ nie chcę, aby to startowało automatycznie. Nie pracuję aż tak dużo lokalnie na Wordpressie, żeby mi się to wszystko uruchamiało. Natomiast na biurowej maszynie, gdzie głównie pracuję na Wordpressie mam tę linię odkomentowaną. Czyli Worpdress uruchamia się automatycznie po starcie systemu.

- volumes: ...

  Tutaj mamy wskazanie woluminów, jak to się ładnie po polsku nazywa. Są to zasoby dyskowe znajdujące się na zewnątrz kontenera (przed dwukropkiem) oraz znajdujące się wewnątrz kontenera (po dwukropku). Czyli w naszym przypadku mamy plik uploads.ini (będzie za chwilę po co on jest) zmapowany do /usr/local/etc/php/conf.d/uploads.ini. Mówimy dockerowi mniej więcej tak: "Weź ten plik uploads.ini i udawaj, że to jest plik uploads.ini znajdujący się w systemie operacyjnym w katalogu /usr/local/etc/conf.d". Dodam, że kropka i ukośnik znajdujący się przed plikiem oznacza, że ten plik znajduje się w tym samym katalogu co nasz plik docker-compose.yml. Można też tutaj podać bezwzględną ścieżkę.

  W kolejnej linii mamy katalog public_html, który ma zawierać tę samą zawartość, co katalog /var/www/html/. To po to, aby mieć dostęp do plików Wordpressa. Czy to jest konieczne? W sumie raczej nie, ale poprzez bezpośredni dostęp do plików, można coś szybciej zrobić.

- environment

  Tutaj wskazujemy parametry bazy danych czyli nazwę bazy i użytkownika, a także hosta i port. Naszym hostem bazy danych jest usługa db, a portem 3306. Po co to jest? Możemy np. mieć serwer bazodanowy gdzieś w sieci dostępny pod konkretnym adresem. Nie musimy korzystać wtedy z Dockera, możemy uruchomić jako kontener Wordpressa, a baza może być na innym komputerze. Może też być tak, że stworzymy całkiem osobny kontener z silnikiem bazy danych, wtedy wskażemy tutaj adres IP oraz port. W zasadzie tak się powinno robić, czyli stawiać osobne kontenery dla każdej usługi, żeby nie położyć całego systemu jedną awarią. Ale to zależy od wielu czynników i planowaniem topologii sieci oraz projektowaniem usług sieciowych w tym wpisie nie będę się zajmował...

- ports

  W tej linii przekierowujemy porty. Docker uruchomi kontener z serwerem HTTP na naszej lokalnej maszynie i teraz musimy się jakoś do niego dostać. W tym przypadku po prostu mówimy dockerowi, że odwołanie do naszego hosta na porcie 80, zostanie przekierowane do serwera Apache również na port 80. Gdybyśmy mieli więcej projektów lub port 80 byłby zajęty przez inną usługę, możemy tę linię zapisać  np.: - 8080:80. Czyli wtedy odwołam się na maszynie lokalnej do portu 8080, i zostanę przekierowany na port 80 do serwera Apache wewnątrz kontenera.



Dalej mamy kolejne usługi z analogicznymi parametrami. Z uwag dodam tylko, że w przypadku usługi db pojawia się w sekcji environment parametr MYSQL_ROOT_PASSWORD: p4ssw0rd! czyli hasło roota bazy danych oraz pozostałe dane bazy danych (nazwa, użytkownik i hasło). W usłudze phpmyadmin przekierowujemy port 8080 na 80  i podajemy hosta oraz hasło roota.

Teraz pozostaje tylko stworzyć katalog testowy (np. Wordpress) wrzucić do niego dwa pliki:

docker-compose.yml

uploads.ini

Plik uploads.ini zwiększa nam limity na upload. Domyślne parametry nie pozwalają uploadować dużych plików, a po podmianie pliku uploads.ini możemy wrzucać do Wordpressa duże zdjęcia oraz inne pliki wtyczek lub motywów. Zawartość upoads.ini wygląda następująco:

```php
file_uploads = On
upload_max_filesize = 256M
post_max_size = 256M
memory_limit = 256M
max_execution_time = 600
```

