# Projekt: Klasifikacija Brazilskih Novčića

### Teodora Vasić 1039/2023

## Uvod
U ovom projektu razvijena je konvolutivna neuronska mreža za klasifikaciju slika brazilskih novčića. Cilj je bio prepoznavanje različitih vrednosti brazilskih novčića na osnovu slika.

## Skup Podataka
Koristio se skup podataka koji sadrži slike brazilskih novčića različitih vrednosti. Skup podataka je podeljen na trening skup (train set) i testni skup (test set). Svaka slika u imenu sadrzi i vrednost novčića (5, 10, 25, 50, i 100 centavos). Nakon ucitavanja skupa, trening skup je dalje podeljen na trening i validacioni skup.

Skup podataka možete preuzeti sa [Kaggle](https://www.kaggle.com/datasets/volodymyrgavrysh/brazilian-coins-dataset-classification25k-images).

## Priprema Podataka
1. **Ekstrakcija Podataka**: Podaci su ekstraktovani iz `.tar.xz` arhiva koristeći Python biblioteku `tarfile`. Svaka slika je konvertovana u RGB format koristeći biblioteku `PIL`, a oznake su izdvojene iz imena fajlova.
2. **Transformacije**: Slike su transformisane za prilagođavanje ulazu mreže. Transformacije uključuju promenu veličine na 128x128 piksela, konverziju u grayscale (sive tonove), normalizaciju i konverziju u PyTorch tenzore.

## Model
Korišćena je konvolutivna neuronska mreža (CNN) sa sledećom arhitekturom:
- **Konvolutivni slojevi**: Dva konvolutivna sloja sa 32 i 64 filtera.
- **Dropout slojevi**: Za regularizaciju i smanjenje preprilagodjavanja.
- **Povezani slojevi**: Dva potpuno povezana sloja za klasifikaciju.
- **Aktivacija**: ReLU aktivacija između slojeva.
- **Izlazna funkcija**: Log softmax za višeklasnu klasifikaciju.

## Obuka
Model je obučen koristeći `CrossEntropyLoss` kao funkciju gubitka i `Adam` kao optimizator. Proces obuke je trajao 10 epoha. Praćeni su gubici i tačnost tokom obuke kako bi se procenila efikasnost modela.

## Evaluacija
Model je evaluiran na trening i testnim skupovima. Korišćene su metrike kao što su tačnost, preciznost, recall i F1 rezultat. Matrica konfuzije je korišćena za vizualizaciju performansi modela na testnim podacima.

## Vizualizacija
Gubici i tačnost tokom obuke prikazani su pomoću grafika. Konfuziona matrica je korišćena za evaluaciju performansi modela na testnim podacima.

## Zaključak
Razvijena konvolutivna neuronska mreža uspešno prepoznaje različite vrednosti brazilskih novčića na osnovu slika. Model se može dalje poboljšavati dodavanjem složenijih arhitektura, optimizacijom hiperparametara ili primenom na većem skupu podataka.

