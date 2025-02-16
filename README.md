# IUM_projekt

## Wykonawcy:
Antek Grajek  
Marcin Połosak

## Dane:

W celu poprawnego korzystania z modeli należy w pierwszej kolejności dostarczyć pliki z danymi ,tj. artists.jsonl, sessions.jsonl oraz tracks.jsonl do folderu dane w katalogu projektu.

## Instrukcja uruchomienia mikroserwisu:

W celu aktywacji mikroserwisu należy wykonać następujące kroki:

* Pierwsze uruchomienie:
```
cd microservice
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python3 post_handler.py
```
* Kolejne uruchomienie:
```
cd microservice
source .venv/bin/activate
python3 post_handler.py
```

## Instrukcja obsługi zapytań:

W ramach korzystania z mikroserwisu można skorzystać z następujących funkcjonalności dla przykłądowych danych:

* Predykcja modelem bazowym:
```
curl -X POST -H "Content-Type: application/json"  -d '{"input_data": "2024-01-24"}' --max-time 360 http://localhost:8060/predict/modelA
```


* Predykcja modelem zaawansowanym:
```
curl -X POST -H "Content-Type: application/json"  -d '{"input_data": "2024-01-24"}' --max-time 360 http://localhost:8060/predict/modelB
```

* Testy A/B - rozpoczęcie testów:
```
curl -X POST -H "Content-Type: application/json"  -d '{"input_data": "2024-01-08"}' --max-time 360 http://localhost:8060/ABtest/begin
```
* Testy A/B - dodanie użytkownika - przypis do grupy:
```
curl -X POST -H "Content-Type: application/json"  -d '{"user_id": "134"}' --max-time 360 http://localhost:8060/ABtest/get_playlist
```
* Testy A/B - zakończenie:
```
curl -X POST -H "Content-Type: application/json" --max-time 360 http://localhost:8060/ABtest/finish
```

## Raport z wykonanych testów:

Dodatkowe informacje o wynikach przeprowadzonych testów zapisywane są do pliku experiments.log