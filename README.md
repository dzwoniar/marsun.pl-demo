# Marsun — prototyp strony B2B dla branży OZE

Statyczny prototyp strony prezentującej ofertę dystrybutora sprzętu fotowoltaicznego dla instalatorów. Projekt pokazuje układ landing page: od problemów odbiorcy, przez ofertę i proces współpracy, po FAQ i wezwania do działania.

Repozytorium zawiera warstwę prezentacji. Nie implementuje platformy B2B, zapisów na szkolenia ani obsługi zamówień.

## Co można obejrzeć

- Responsywną stronę z nawigacją do sekcji oferty, procesu, opinii i FAQ.
- Karty produktów i usług, tabelę porównawczą oraz opis rozpoczęcia współpracy.
- Rozwijane odpowiedzi FAQ, sterowane zmianą klasy CSS po kliknięciu.
- Animacje pojawiania się sekcji podczas przewijania, oparte na `IntersectionObserver`.

## Uruchomienie lokalne

Wymagania: współczesna przeglądarka; Python 3 do uruchomienia poniższego serwera plików.

```bash
git clone https://github.com/dzwoniar/marsun.pl-demo.git
cd marsun.pl-demo
python -m http.server 8000 --bind 127.0.0.1
```

Otwórz [http://localhost:8000](http://localhost:8000). Na Windows, jeśli polecenie `python` nie jest dostępne, można użyć `py -m http.server 8000 --bind 127.0.0.1`. Serwer zatrzymuje się przez `Ctrl+C`. Projekt nie wymaga instalacji paczek ani procesu budowania.

## Struktura i architektura

```text
.
├── index.html   # treść, style i skrypt interakcji
└── README.md
```

Cała implementacja znajduje się w [index.html](index.html): HTML opisuje sekcje, osadzony CSS odpowiada za wygląd i punkty przełamania, a końcowy skrypt obsługuje animacje. FAQ wykorzystuje atrybuty `onclick` bez dodatkowej biblioteki. Dane oferty są wpisane bezpośrednio w HTML.

Stos: HTML5, CSS i JavaScript bez frameworka. Zewnętrzną zależnością wizualną jest Google Fonts: DM Sans i Playfair Display. Przy braku połączenia z usługą fontów przeglądarka korzysta z rodzin zastępczych.

## Zakres demonstracji

- Końcowe przyciski zapisu na szkolenie i pobrania PDF prowadzą do `#`; repozytorium nie zawiera dokumentu PDF ani mechanizmu zapisu.
- Opisana w treści weryfikacja firmy przez API GUS nie jest zaimplementowana. Nie ma backendu, bazy danych ani konfiguracji środowiska.
- Opinie, liczby, warunki współpracy i deklaracje handlowe są treścią prototypu; kod nie potwierdza ich aktualności ani realizacji.
- Nie ma skonfigurowanego zestawu testów ani automatycznego wdrożenia. Przed podłączeniem realnej obsługi należy zastąpić odnośniki docelowymi adresami i zweryfikować treści.

## Powiązane warianty

[Wariant v2](https://github.com/dzwoniar/marsun.pl-demo-v2) dodaje interaktywny kalkulator kosztu awarii. Osobny [landing lead magnetu](https://github.com/dzwoniar/marsun.pl-lead) demonstruje formularz pozyskania kontaktu.
