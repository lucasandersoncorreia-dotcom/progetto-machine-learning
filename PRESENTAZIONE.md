# 🎤 Scaletta Presentazione di Gruppo (5 Minuti)
## Project Work 2: La Catena di Montaggio di un Modello
**Team Lucas**: Lucas Correia (io), Luca Motta, Giuseppe, Matteo Landucci, Amanda  
*Tempo a disposizione: 5 minuti totali (1 minuto esatto a testa per 5 persone)*

---

### ⏱️ Cronologia Interventi (1 minuto a testa)

```mermaid
gantt
    title Scaletta Speech 5 Minuti (5 Componenti)
    dateFormat  m:s
    axisFormat %M:%S
    section Amanda
    Dati & Feature Engineering      :a1, 00:00, 01:00
    section Luca Motta
    Pipeline, Split & Baseline      :a2, 01:00, 02:00
    section Lucas Correia
    Architettura & Gara Modelli     :a3, 02:00, 03:00
    section Giuseppe
    Tuning 5-Fold CV & Sigillo      :a4, 03:00, 04:00
    section Matteo Landucci
    Settembre, Retraining & Scorte  :a5, 04:00, 05:00
```

---

### 1️⃣ Speaker 1: Amanda (00:00 – 01:00)
**Ruolo:** Data Analyst & Feature Engineering  
**Argomenti:** Blocco 1 (Scelta Famiglia & Dati) e Blocco 2 (Feature Engineering)

#### 🗣️ Cosa dire:
> *"Buongiorno a tutti. Nel nostro progetto abbiamo analizzato un magazzino industriale di oltre 7.700 articoli per prevederne la domanda e calcolare i corretti livelli di scorta.  
> Abbiamo isolato la famiglia **'Tenute e guarnizioni'**, filtrando gli articoli attivi con almeno 12 pezzi venduti nello storico, ottenendo **765 articoli**.  
> Nei dati emergono tre comportamenti distinti:
> 1. Articoli a **domanda regolare**;
> 2. Articoli a **ondate** (periodi di silenzio seguiti da ordini massicci);
> 3. Articoli con **un solo picco improvviso**, i più critici e imprevedibili.  
> 
> Per addestrare i modelli abbiamo rispettato la **Regola Aurea** (nessun dato dal futuro) e introdotto **5 feature quantitative**: la media a 6 mesi, la deviazione standard per quantificare l'instabilità, il trend recente come derivata prima, il picco massimo semestrale e il lead time del fornitore.  
> Passo la parola a Luca Motta per la pipeline e la baseline."*

---

### 2️⃣ Speaker 2: Luca Motta (01:00 – 02:00)
**Ruolo:** Data Engineering & Pipeline Specialist  
**Argomenti:** Blocco 3 (Split Temporale Onesto) e Blocco 4 (La Baseline da Battere)

#### 🗣️ Cosa dire:
> *"Grazie Amanda. Per garantire un **test onesto**, abbiamo bandito lo split casuale: mescolando le date, il modello imparerebbe dal futuro per indovinare il passato.  
> Abbiamo impostato un rigido **split temporale**:
> - **Train:** da aprile 2025 a giugno 2026 (6.885 esempi);
> - **Test:** luglio e agosto 2026 (1.530 esempi);
> - **Settembre 2026:** tenuto completamente sigillato.  
> 
> Prima di usare algoritmi complessi, abbiamo definito la **Baseline**: una media mobile semplice degli ultimi 3 mesi.  
> Sul test la baseline ottiene una **MAE di 6.79 pezzi**. Questo valore è la nostra soglia minima: qualsiasi modello che non batta 6.79 pezzi è inutile e non deve entrare in produzione.  
> La parola a Lucas per la gara tra i modelli."*

---

### 3️⃣ Speaker 3: Lucas Correia (02:00 – 03:00)
**Ruolo:** Lead Developer & Git Coordinator  
**Argomenti:** Blocco 5 (Gara tra i 4 Modelli Candidati)

#### 🗣️ Cosa dire:
> *"Grazie Luca. Nel Blocco 5 abbiamo orchestrato la gara tra 4 modelli eterogenei addestrati sugli stessi dati e valutati sulla MAE del test:
> 1. **Regressione Lineare:** MAE 6.99 (non batte la baseline);
> 2. **Decision Tree:** MAE 7.02 (soffre di alta varianza);
> 3. **k-Nearest Neighbors (k=5):** crolla con un errore disastroso di **14.62 pezzi**;
> 4. **Random Forest:** vince la gara con **MAE 6.67 pezzi**, l'unico a battere la baseline.  
> 
> Il fallimento di kNN è stato didatticamente illuminante: calcolando distanze geometriche su scale non normalizzate con soli 5 vicini, gli articoli intermittenti con ordini a picco hanno distorto completamente le stime.  
> Random Forest ha invece trionfato grazie all'ensemble bagging, che riduce la varianza e gestisce nativamente outlier e non linearità.  
> Ora Giuseppe vi spiegherà come abbiamo ottimizzato e sigillato il modello."*

---

### 4️⃣ Speaker 4: Giuseppe (03:00 – 04:00)
**Ruolo:** Machine Learning Specialist  
**Argomenti:** Blocco 6 (Tuning con Cross-Validation & Modello Sigillato)

#### 🗣️ Cosa dire:
> *"Grazie Lucas. Nel Blocco 6 abbiamo cercato i migliori iperparametri con **GridSearchCV a 5 parti**.  
> Per Random Forest abbiamo esplorato numero di stimatori e profondità degli alberi, individuando l'ottimo a **200 alberi con profondità massima 5**.  
> Il modello ha dimostrato un'eccezionale coerenza:
> - **MAE in Cross-Validation:** 6.38 pezzi;
> - **MAE sul Test Set:** 6.67 pezzi;
> - Uno scarto di soli 0.29 pezzi, prova inconfutabile di assenza di overfitting.  
> 
> A questo punto abbiamo **sigillato** il nostro Random Forest: registrava un miglioramento ufficiale del **+1.8%** rispetto alla baseline.  
> Come accade in azienda, una volta sigillato il modello non si tocca più: va in produzione e si attende il mese successivo.  
> La parola a Matteo per i risultati di settembre e le scorte."*

---

### 5️⃣ Speaker 5: Matteo Landucci (04:00 – 05:00)
**Ruolo:** Diario, Metriche & Retraining Coordinator  
**Argomenti:** Settembre 2026, Blocco 7 (Retraining), Blocco 8 (Scorte Aziendali & Conclusioni)

#### 🗣️ Cosa dire:
> *"Grazie Giuseppe. Venerdì abbiamo ricevuto **settembre 2026**, un mese reale mai visto.  
> Con la riapertura autunnale delle fabbriche, gli ordini concentrati hanno fatto raddoppiare l'errore per tutti i modelli, ma il nostro Random Forest ha tenuto ed esteso il vantaggio: **MAE 15.96 contro 16.39 della baseline (+2.6%)**!  
> Nel Blocco 7 abbiamo testato se **riaddestrare il modello ogni mese** convenga: il delta medio è di appena **-0.063 pezzi**. Con soli 3 mesi non ha senso complicare la pipeline; raccomandiamo un retraining semestrale.  
> Infine, nel Blocco 8 abbiamo calcolato la Scorta di Sicurezza e il Punto di Riordino (ROP) per 640 articoli:
> - Il nostro ROP medio è di **16.3 pezzi**, contro i **30.4 del sistema aziendale**;
> - A livello economico, per gli articoli di **classe A** preferiamo abbondare per scongiurare rotture di stock, mentre per la **classe C** riduciamo le giacenze per liberare liquidità.  
> La nostra catena di montaggio predittiva produce decisioni snelle, stabili e misurabili. Grazie a tutti!"*

---

### 💡 Domande Probabili del Docente e Risposte Pronte

1. **Perché kNN è andato così male rispetto agli altri?**
   - *Risposta:* kNN usa la distanza euclidea nello spazio delle feature non standardizzate. Con $k=5$ e articoli con ordini intermittenti, pochi vicini ad alto volume falsano completamente la previsione di un articolo a basso consumo. Aumentando $k=15$ in CV l'errore è sceso a 6.59.

2. **Perché a settembre la MAE è salita a circa 16 pezzi?**
   - *Risposta:* Settembre segna la ripresa industriale post-ferie con ordini cumulativi e riassortimenti importanti. L'errore assoluto scala con i volumi, ma in termini relativi il modello ha aumentato il proprio vantaggio rispetto alla baseline, passando da +1.8% a +2.6%.

3. **Perché sconsigliate il retraining mensile continuo?**
   - *Risposta:* Lo scarto medio è di soli -0.063 pezzi. Riaddestrare ogni mese espone al rischio di incorporare mesi anomali (come agosto) che peggiorano le previsioni successive, aumentando i costi di manutenzione senza benefici concreti.
