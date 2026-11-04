# Project Work 2 · La catena di montaggio di un modello

Repository per il lavoro di gruppo del modulo di **Machine Learning**.

## 📌 Obiettivo del Progetto

Un magazzino di ricambi industriali ha 7.771 articoli con storico di uscite mensili da aprile 2025 ad agosto 2026 (17 mesi).
L'obiettivo del gruppo è costruire un sistema end-to-end che:
1. **Preveda** quanti pezzi usciranno il mese prossimo per ogni articolo di una determinata famiglia di prodotti.
2. **Decida** quanta scorta tenere (*scorta di sicurezza*) e quando effettuare l'ordine (*punto di riordino*).
3. **Valuti** le performance sul nuovo mese non visto (settembre 2026) e confronti le decisioni con il sistema aziendale attuale.

## 🧱 Fasi del Lavoro (Catena di Montaggio)

| Blocco | Domanda Guida | Focus |
|---|---|---|
| **1** | Con quali dati lavoro? | Esplorazione e scelta famiglia |
| **2** | Che cosa do in pasto al modello? | Feature engineering |
| **3** | Quando il test è onesto? | Validazione e split corretto |
| **4** | Il modello batte una regola semplice? | Baseline e metriche |
| **5** | Come scelgo il modello? | Confronto modelli e cross-validation |
| **6** | Come scelgo gli iperparametri? | Tuning e sigillo modello |
| **7** | Devo riallenarlo ogni volta? | Strategia di retraining |
| **8** | E poi, che cosa ci faccio? | Decisione operativa di magazzino |

## 👥 Ruoli del Gruppo

- **Tastiera**: Scrive ed esegue il codice.
- **Mappa**: Cerca nella mappa del corso e documentazione (scikit-learn).
- **Diario**: Compila la scheda del gruppo nel notebook.
- **Voce**: Presentazione finale.

## 🚀 Setup e Istruzioni

1. Clona la repository:
   ```bash
   git clone https://github.com/lucasandersoncorreia-dotcom/progetto-machine-learning.git
   ```
2. Installa le dipendenze:
   ```bash
   pip install numpy pandas matplotlib scikit-learn
   ```
3. Inserisci il file dei dati `warehouse_history.csv` nella cartella principale.
4. Apri ed esegui `project_work_2_building_blocks.ipynb`.
