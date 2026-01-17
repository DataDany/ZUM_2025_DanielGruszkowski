# **Projekt zaliczeniowy – Zastosowania Uczenia Maszynowego**

## **1. Informacje ogólne**
**Nazwa projektu:**  
Klasyfikacja tematów wiadomości newsowych z wykorzystaniem NLP    

**Autor:**  
Daniel Gruszkowski
s34326

**Kierunek, rok i tryb studiów:**  
*Informatyka, semestr III, Magisterskie internetowe*  

**Data oddania projektu:**  
17.01.2025  

---

URUCHOMIENIE PROJEKTU

Wymagania:
- Python 3.12
- pip

#### *Utworzenie środowiska wirtualnego*

W katalogu głównym projektu wykonaj:
```bash 
python -m venv .venv
```

#### *Aktywacja środowiska*

macOS / Linux:
```bash
source .venv/bin/activate
```

Windows (PowerShell):
```bash
.venv\Scripts\Activate.ps1
```

Po aktywacji w terminalu pojawi się prefiks:
(.venv)

#### *Instalacja zależności*

Zainstaluj wymagane biblioteki:
```bash
pip install -r requirements.txt
```


## **2. Opis projektu**
Celem projektu jest stworzenie systemu klasyfikującego wiadomości newsowe
do odpowiednich kategorii tematycznych na podstawie ich treści.
Projekt obejmuje pełny proces uczenia maszynowego, w tym analizę danych,
preprocessing tekstu, budowę oraz porównanie trzech różnych modeli
klasyfikacyjnych: modelu klasycznego, sieci neuronowej zbudowanej od zera
oraz modelu transformerowego.

---

## **3. Dane**
**Źródło danych:**  
*HuggingFace Datasets*  

**Link do danych:**  
`https://huggingface.co/datasets/sh0416/ag_news `  

**Opis danych:**  
- liczba próbek: 127 600  
- liczba cech / kolumn: 3 (title, description, label)
- format danych: tekstowy (string) 
- rodzaj etykiet / klas:  4 klasy tematyczne  
  - World  
  - Sports  
  - Business  
  - Sci/Tech  
- licencja: MIT License


**Uwaga dotycząca danych:**  
Pełny zbiór danych nie jest przechowywany w repozytorium - dane
pobierane są bezpośrednio z HuggingFace API.

---

## **4. Cel projektu**
Celem projektu jest porównanie skuteczności różnych podejść do klasyfikacji
tekstu:
- klasycznych metod uczenia maszynowego,
- sieci neuronowej,
- nowoczesnego modelu transformerowego.

Projekt ma odpowiedzieć na pytanie, jak wybór reprezentacji tekstu oraz modelu
wpływa na jakość klasyfikacji wiadomości newsowych.

---

## **5. Struktura projektu**
Projekt składa się z czterech głównych etapów, każdy w osobnym notatniku `.ipynb`:

| Etap | Nazwa pliku | Opis |
|------|--------------|------|
| 1 | `1_EDA.ipynb` | Analiza danych, wizualizacje, wnioski |
| 2 | `2_Preprocessing_Features.ipynb` | Czyszczenie danych, preprocessing, inżynieria cech |
| 3 | `3_Models_Training.ipynb` | Trening modeli klasycznego ML, sieci neuronowej i transformera |
| 4 | `4_Evaluation.ipynb` | Ewaluacja, porównanie modeli, wizualizacje wyników |

Dodatkowo:
- `5_Model_Demo.ipynb` – demonstracja działania wytrenowanego modelu
na przykładowych i własnych tekstach.
---

## **6. Modele**
Projekt obejmuje trzy różne podejścia do modelowania danych:

### **6.1 Model klasyczny ML**
- **Algorytm:** Regresja logistyczna  
- **Reprezentacja tekstu:** TF-IDF  
- **Opis:** Klasyczny model oparty o statystyczną reprezentację tekstu.  
- **Wyniki (test):**  
  - Accuracy: 0.915  
  - F1 macro: 0.915  

### **6.2 Sieć neuronowa zbudowana od zera**
- **Architektura:** Embedding -> uśrednianie -> Dense  
- **Liczba warstw:** 3  
- **Funkcje aktywacji:** ReLU  
- **Optymalizator:** Adam  
- **Wyniki (test):**  
  - Accuracy: 0.912
  - F1 macro: 0.912

### **6.3 Model transformerowy (fine-tuning)**
- **Nazwa modelu:** DistilBERT 
- **Biblioteka:** HuggingFace Transformers  
- **Zakres dostosowania:** fine-tuning na zbiorze AG News  
- **Wyniki (test):**  
  - Accuracy: 0.946
  - F1 macro: 0.946   

---

## **7. Ewaluacja**
**Użyte metryki:**  
- Accuracy  
- Precision  
- Recall  
- F1-score

**Porównanie modeli:**

| Model | Accuracy (test) | F1 macro (test) |
|------|-----------------|-----------------|
| LogReg + TF-IDF | 0.915 | 0.915 |
| Simple NN | 0.912 | 0.912 |
| DistilBERT | 0.946 | 0.946 |

**Wizualizacje:**  
- Macierz pomyłek  
- Porównywanie modeli Accuracy, F1 macro

---

## **8. Wnioski i podsumowanie**
Najlepsze wyniki uzyskał model transformerowy DistilBERT, co potwierdza
skuteczność modeli opartych na mechanizmie uwagi w zadaniach NLP.
Klasyczny model TF-IDF + regresja logistyczna okazał się bardzo silnym
punktem odniesienia, osiągając wyniki zbliżone do sieci neuronowej.
Sieć neuronowa zbudowana od zera uzyskała nieco słabsze rezultaty, co
wskazuje na ograniczenia prostych architektur w porównaniu do
pretrenowanych modeli językowych.

W przyszłości projekt można rozszerzyć o:
- większe modele transformerowe,
- analizę błędów klasyfikacji,
- wdrożenie modelu w postaci aplikacji webowej.

---

## **9. Struktura repozytorium**
```
projekt_zum_2025/
│
├── data/
│ └── processed/
├── notebooks/
│ ├── 1_EDA.ipynb
│ ├── 2_Preprocessing_Features.ipynb
│ ├── 3_Models_Training.ipynb
│ └── 4_Evaluation.ipynb
| └── 5_Model_Demo.ipynb
├── models/
├── results/
├── README.md
└── requirements.txt
```
## **10. Technologia i biblioteki**
- Python 3.12 
- NumPy  
- Pandas  
- Matplotlib  
- scikit-learn  
- PyTorch  
- HuggingFace Transformers  
- HuggingFace Datasets  
- HuggingFace Accelerate  
- evaluate  
- joblib  

---

## **11. Licencja projektu**
Projekt udostępniony na licencji:  
*MIT License*  

Źródło danych: zgodnie z licencją wskazaną w sekcji **
[Dane](https://huggingface.co/datasets/sh0416/ag_news)**.

