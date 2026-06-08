# 🍔 Interaktywna Mapa Fast Foodów w Warszawie

Projekt przedstawia interaktywną mapę lokalizacji najpopularniejszych sieci fast food (McDonald's, KFC, Burger King, Kebab King, Pizza Hut) na terenie Warszawy. Aplikacja bazuje na bibliotece **Leaflet** i integruje państwowe dane przestrzenne (WMS).

## 🚀 Główne Funkcje

*   **Dwie warstwy podkładowe (Base Layers):**
    *   Standardowa mapa drogowa **OpenStreetMap**.
    *   Wysokorozdzielcza **Ortofotomapa** pobierana bezpośrednio z rządowego serwisu **Geoportal (WMS)**.
*   **Interaktywne markery:** Punkty gastronomiczne wyświetlane jako spersonalizowane czerwone okręgi (`L.circleMarker`) z dynamicznymi etykietami (tooltips) po najechaniu myszką, prezentującymi nazwę, ulicę, numer oraz miasto.
*   **Wyszukiwarka z autouzupełnianiem (Autocomplete):**
    *   Dynamiczny panel wyszukiwania w prawym górnym rogu.
    *   Podpowiadanie pasujących lokali w czasie rzeczywistym.
    *   Po kliknięciu w podpowiedź mapa automatycznie centruje się na wybranym punkcie, przybliża widok (`zoom: 15`) i otwiera okienko popup z informacjami o lokalu.
*   **Narzędzia nawigacyjne:** Przełącznik warstw, podgląd skali mapy oraz zoptymalizowane napisy w stopce (attribution).

---

## 🛠️ Użyte Technologie

*   **HTML5** & **CSS3** (podstawowy layout, stylizacja autouzupełniania wyszukiwarki)
*   **JavaScript (ES6)** (logika filtrowania danych, zdarzenia DOM, wyszukiwarka)
*   **Leaflet.js** (biblioteka do obsługi map interaktywnych)
*   **WMS (Web Map Service)** (serwis geoportal.gov.pl dostarczający zdjęcia satelitarne)
*   **GeoJSON** (format zapisu punktów geograficznych)

---

## 📂 Struktura Projektu

```text
projekt_mapa_fast_food/
├── images/                       # Folder na ewentualne zasoby graficzne
├── index.html                    # Główny plik aplikacji (zawiera strukturę, style oraz kod JS z bazą GeoJSON)
├── leaflet.css / leaflet.js      # Lokalne pliki biblioteki Leaflet (wsparcie działania offline)
├── zdjecie.ico                   # Ikona strony (favicon)
└── README.md                     # Dokumentacja projektu (ten plik)
```

---

## ⚙️ Jak uruchomić?

Projekt jest w pełni statyczny i nie wymaga serwera aplikacyjnego ani bazy danych. Aby go uruchomić:
1. Pobierz lub sklonuj to repozytorium.
2. Otwórz plik `index.html` bezpośrednio w dowolnej przeglądarce internetowej (Chrome, Firefox, Edge, Safari).

---

## 🧐 Ocena Projektu — Czy to "git" projekt?

**Tak, to bardzo fajny (git) projekt!** Oto dlaczego:

### ✅ Zalety projektu:
1.  **Dobre wykorzystanie Leaflet.js:** Prawidłowo zaimplementowana mapa, warstwy, przełącznik warstw, kontrolka skali oraz markery.
2.  **Integracja z WMS Geoportalu:** Wykorzystanie `L.tileLayer.wms` do zaciągania Ortofotomapy z zewnętrznego, państwowego serwisu to duży plus. Pokazuje to umiejętność pracy z zewnętrznymi usługami GIS.
3.  **Własna wyszukiwarka autocomplete:** Zamiast gotowej wtyczki, wyszukiwarka została napisana samodzielnie za pomocą czystego JavaScriptu (filtrowanie tablicy obiektów GeoJSON na zdarzenie `input` i dynamiczne renderowanie listy `<ul>`). To świetne ćwiczenie z obsługi manipulacji drzewem DOM.
4.  **Lokalne zależności:** Pliki `leaflet.js` i `leaflet.css` znajdują się w katalogu projektu, co zapewnia stabilność działania aplikacji niezależnie od sieci CDN.

### 💡 Sugestie ulepszeń (co można poprawić w przyszłości):
1.  **Wydzielenie bazy danych GeoJSON:** Aktualnie cała baza punktów (ponad 1000 linii kodu) znajduje się bezpośrednio wewnątrz tagu `<script>` w `index.html`. Warto przenieść zmienną `geojson_points` do osobnego pliku (np. `points.json` lub `points.js`) i wczytywać ją dynamicznie (np. za pomocą `fetch()`). Ułatwi to edycję bazy punktów i poprawi czytelność kodu.
2.  **Responsywność na urządzeniach mobilnych:** Okienko autouzupełniania wyszukiwarki ma stałą szerokość `200px`. Można dostosować style CSS, aby panel wyszukiwania lepiej dopasowywał się do ekranów smartfonów.
3.  **Grupowanie punktów (Marker Clustering):** Przy bardzo dużej liczbie fast foodów na małym obszarze markery zaczną na siebie nachodzić. Dodanie wtyczki `Leaflet.markercluster` pogrupowałoby bliskie punkty w estetyczne klastry.
