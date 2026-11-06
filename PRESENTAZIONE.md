# 🎤 Scaletta Presentazione di Gruppo (5 Minuti)
## Project Work 2: La Catena di Montaggio di un Modello
**Team Luca**: Amanda, Luca, Giuseppe, Matteo  
*Tempo a disposizione: 5 minuti totali (~1 minuto e 15 secondi a testa)*

---

### ⏱️ Cronologia Interventi

```mermaid
gantt
    title Scaletta Speech 5 Minuti
    dateFormat  m:s
    axisFormat %M:%S
    section Amanda
    Dati & Feature Engineering      :a1, 00:00, 01:15
    section Luca
    Pipeline, Split & Baseline      :a2, 01:15, 02:30
    section Giuseppe
    Modelli & Tuning Iperparametri  :a3, 02:30, 03:45
    section Matteo
    Settembre, Scorte & Business    :a4, 03:45, 05:00
```

---

### 1️⃣ Speaker 1: Amanda (~1 min 15 sec)
**Ruolo:** Data Analyst & Feature Engineering  
**Argomenti:** Blocco 1 (Scelta Famiglia & Dati) e Blocco 2 (Feature Engineering)

#### 🗣️ Cosa dire:
> *"Buongiorno a tutti. Nel nostro progetto abbiamo analizzato un magazzino industriale di oltre 7.700 articoli per prevedere la domanda e calcolare i livelli ottimali di scorta.  
> Abbiamo scelto la famiglia **'Tenute e guarnizioni'**, filtrando gli articoli attivi con almeno 12 pezzi venduti nello storico, ottenendo **765 articoli**.  
> Esplorando i dati storici, abbiamo riscontrato tre comportamenti tipici:
> 1. Articoli a **domanda regolare** (prevedibili con facilità);
> 2. Articoli a **ondate** (periodi di calma seguiti da ordini a blocchi);
> 3. Articoli con **un solo picco improvviso** (i più critici per il magazzino).  
> 
> Per aiutare i modelli di machine learning, non ci siamo limitati ai soli lag mensili, ma abbiamo progettato **5 feature specifiche**:
> - `media_6_mesi` per stabilizzare il livello di domanda recente;
> - `std_6_mesi` per catturare l'instabilità delle vendite;
> - `trend_recente` ($lag_1 - lag_2$) per capire la direzione della domanda;
> - `max_6_mesi` per intercettare i picchi;
> - `lead_time_days` come caratteristica logistica del fornitore.  
> Passo ora la parola a Luca per la pipeline e la validazione."*

---

### 2️⃣ Speaker 2: Luca (~1 min 15 sec)
**Ruolo:** Lead Developer & Git Coordinator  
**Argomenti:** Blocco 3 (Split Temporale Onesto) e Blocco 4 (La Baseline)

#### 🗣️ Cosa dire:
> *"Grazie Amanda. Passando all'architettura della catena di montaggio, il primo vincolo fondamentale è stato garantire un **test onesto**.  
> Nelle serie temporali non si può usare uno split casuale: se mescoliamo i mesi, il modello impara dal futuro per predire il passato, ingannandoci. Abbiamo quindi impostato un rigido **split temporale**:
> - **Train:** da aprile 2025 a giugno 2026 (6.885 esempi);
> - **Test:** luglio e agosto 2026 (1.530 esempi);
> - **Futuro reale:** settembre 2026, tenuto completamente nascosto fino alla fine.  
> 
> Prima di toccare qualsiasi algoritmo complesso, abbiamo creato una **Baseline di riferimento**, basata su una regola semplice: la media delle uscite degli ultimi 3 mesi.  
> La Baseline ha ottenuto un **MAE di 6.79 pezzi** sul test.  
> Questa metrica è diventata la nostra 'asticella': qualsiasi modello di Machine Learning che non batta 6.79 pezzi è inutile e costa solo complessità ingiustificata.  
> Ora Giuseppe vi mostrerà come si sono comportati i 4 modelli."*

---

### 3️⃣ Speaker 3: Giuseppe (~1 min 15 sec)
**Ruolo:** Machine Learning Specialist  
**Argomenti:** Blocco 5 (Gara tra Modelli) e Blocco 6 (Tuning & Modello Sigillato)

#### 🗣️ Cosa dire:
> *"Grazie Luca. Nel Blocco 5 abbiamo messo a confronto 4 algoritmi con approcci diversi:
> 1. **Linear Regression** (MAE 6.99)
> 2. **Decision Tree** (MAE 7.02)
> 3. **k-Nearest Neighbors ($k=5$)** (MAE 14.62)
> 4. **Random Forest** (MAE 6.67)  
> 
> Il kNN ha fallito nettamente: con soli 5 vicini, basta un articolo simile con un picco anomalo per sballare la previsione.  
> Solo il **Random Forest** è riuscito a battere la baseline al primo colpo.  
> Nel Blocco 6 abbiamo cercato i migliori iperparametri con **GridSearchCV a 5 fold**.  
> Per il Random Forest abbiamo testato diverse profondità e numero di alberi, individuando l'ottimo a **200 alberi con profondità massima 5**.  
> Questo modello ha mostrato grande stabilità: un MAE di **6.38 in cross-validation** e **6.67 sul test**, garantendo un **miglioramento del +1.8%** rispetto alla baseline.  
> A questo punto abbiamo **sigillato** il modello senza più modificarlo, pronti per la prova sul mese non visto. La parola a Matteo."*

---

### 4️⃣ Speaker 4: Matteo (~1 min 15 sec)
**Ruolo:** Diario & Metrics Coordinator  
**Argomenti:** Settembre 2026, Blocco 7 (Retraining), Blocco 8 (Scorte & Conclusioni)

#### 🗣️ Cosa dire:
> *"Grazie Giuseppe. Venerdì abbiamo ricevuto **settembre 2026**: un mese mai visto prima né da noi né dal modello.  
> Settembre si è rivelato un mese molto più difficile a causa del rientro post-ferie, raddoppiando gli errori assoluti per tutti i modelli.  
> Tuttavia, il nostro modello sigillato ha confermato la sua solidità: **MAE 15.96 contro 16.39 della baseline**, migliorando le performance del **+2.6%**!  
> Nel Blocco 7 abbiamo testato se **riaddestrare il modello ogni mese** convenga: la differenza media è minima (-0.063 pezzi). Ad agosto riallenare aiuta leggermente, a settembre peggiora per colpa delle anomalie estive: con solo 3 mesi non conviene complicare la pipeline in produzione.  
> Infine, nel Blocco 8 abbiamo trasformato le previsioni in decisioni aziendali concrete, calcolando la **Scorta di Sicurezza** e il **Punto di Riordino (ROP)** per 640 articoli:
> - Il nostro ROP medio è di **16.3 pezzi**, contro i **30.4 pezzi** del sistema aziendale;
> - Il valore totale della merce a scorta è comparabile (322k€ nostri contro 293k€ dell'azienda).  
> In sintesi: la nostra catena di montaggio predittiva genera raccomandazioni snelle e sensate, riducendo le giacenze inutili senza compromettere il livello di servizio. Grazie a tutti!"*

---

### 💡 Domande Probabili dei Docenti e Come Rispondere

1. **Perché kNN è andato così male rispetto agli altri?**
   - *Risposta:* kNN calcola la distanza nello spazio delle feature; con $k=5$ e articoli con scale di vendita eterogenee o picchi sporadici, un vicino anomalo distorce completamente la previsione. Quando abbiamo alzato $k=15$ in CV l'errore è sceso drasticamente (6.59), confermando che $k=5$ era troppo piccolo.

2. **Perché a settembre la MAE è salita a 15.96 pezzi?**
   - *Risposta:* Settembre è il mese del rientro dalla pausa estiva per le industrie. Le vendite registrano riassortimenti massicci e ordini concentrati che alterano la media storica regolare. Nonostante l'aumento dell'errore assoluto, il nostro modello ha mantenuto il vantaggio relativo rispetto alla baseline (+2.6%).

3. **Perché consigliate di non riaddestrare continuamente ogni mese?**
   - *Risposta:* Il miglioramento marginale (-0.063 pezzi) è trascurabile. Riaddestrare a ogni ciclo espone al rischio di 'overfitting' su mesi anomali (come agosto) e aggiunge complessità operativa e costi di manutenzione software non giustificati.
