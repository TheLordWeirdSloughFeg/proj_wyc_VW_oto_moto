# Wycena samochodów marki Volkswagen w oparciu o dane z OtoMoto

# Wstęp
Firma Autox zleciła mi zaprojektowanie aplikacji do wyceny samochodów marki Volkswagen, która pomoże osobom chcącym szybko sprzedać samochód tej marki. Aby użytkownicy dobrze estymowali ceny, aplikacja musi być interaktywna, gdyż poszczególne szczegóły techniczne takie jak: rok produkcji, przebieg itp. mają wpływ na cenę pojazdu.

# Wyniki
## Zbiór danych
Dane dotyczące samochodów zostały pobrane ze strony [OtoMoto](https://www.otomoto.pl/).</br>
Wszystkie oferty z 500 stron portalu zostało pobranych do tabelki danych wykorzystując Selenium Server.

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/selenium.JPG" />
</p>
Z linków generowanych w pętli od strony 1 do 500 pobrałem wartość oraz nazwę parametru z każdej oferty.<br/>

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/wektorlinkow.JPG" />
</p>
Następnie poszczególne parametry złączyłem w kolumny i zapisałem jako ramkę danych. W przypadku braku danego parametru  NA.

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/df.JPG" />
</p>

Ilość wszystkich ofert pobranych ze strony [OtoMoto](https://www.otomoto.pl/) to:

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/ilosc_ofert.JPG" />
</p>

Ze zbioru danych wybrałem następujące kolumny:

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/kolumny.JPG" />
</p>
Następnie wybrałem jedynie samochody marki Volkswagen:

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/VW.JPG" />
</p>
Zbiór wstępny wyglądał następująco:

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/df_1.JPG" />
</p>
W kolejnym kroku podzieliłem zbiory na testowy i treningowy.

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/podzial_zbiorow.JPG" />
</p>
Wczytałem kolejno pakiety potrzebne do uczenia maszynowego.

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/biblioteki.JPG" />
</p>



Przykładowy trening lasu losowego:

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/trening_rf.JPG" />
</p>


## Ocena modelu
Oceniam model lasu losowego stosując moduł Caret.

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/ocena.JPG" />
</p>
Jak widać model jest świetnie dopasowany. Precyzja, F1 oraz recall wynoszą prawie 1.

# Budowanie aplikacji w Shiny
Posiadając już zoptymalizowany i działający model przystępuję do budowy aplikacji stosując moduł Shiny. Najpierw buduję aplikację korzystając z funkcji shinyServer. Dodaję również wytrenowany model lasu losowego.

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/interfejs_c.JPG" />
</p>
Po wytrenowaniu modelu aplikacja ma wyświetlać wynik.

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/interfejs_d.JPG" />
</p>
## Interfejs
Po skonstruowaniu aplikacji projektuję interfejs użytkownika. Do łatwego użytkowania dodaję suwaki dla parametrów rok, pojemność silnika, przebieg, moc silnika, oraz model pojazdu do wyceny. W zakładkach dodaję tabelkę danych do łatwiejszego wglądu. Na samym końcu dodaję przycisk do predykcji wyceny modelu.

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/interfejs.JPG" />
</p>
Uruchamiam aplikację, a następnie dla sprawdzam wycenę Volkswagena Passata z 2010 roku, o przebiegu 49000 km, pojemności silnika 2200 cm<sup>3</sup> i mocy silnika 200 KM.<br/>
Aplikacja po uruchomieniu wygląda następująco:

<p align="center">
  <img src="https://github.com/TheLordWeirdSloughFeg/proj_wyc_VW_oto_moto/blob/main/obrazki/wycena_passata.JPG" />
</p>
Oszacowana cena to ok. 47.522 zł.

# Wnioski
Aplikacja jest stabilna i wizualnie prosta. Zastosowany w niej model uczenia maszynowego (las losowy) sprawdza się w wycenie samochodów marki Volkswagen. Następnym krokiem może być jej zastosowanie np. jako aplikacja do urządzeń mobilnych, pomagająca użytkownikom w wystawianiu ogłoszeń portalu firmy Autox.
