# 🚀 Project Work 2 · Machine Learning
## 📋 Piano di Lavoro Collaborativo & Stato Avanzamento (Team da 5)

Benvenuti nel documento di lavoro e tracciamento del **Project Work 2: La catena di montaggio di un modello**.  
In questo assetto il lavoro è stato distribuito in modo equilibrato e collaborativo tra i **5 componenti del gruppo**: **Lucas Correia (io), Luca Motta, Giuseppe, Matteo Landucci e Amanda**.

Tutti i blocchi operativi (1–8) sono stati **completati con successo**, tutti i test `assert` restituiscono `OK`, la **Scheda del Gruppo** (Cella 42) è integralmente compilata e la relazione finale per il professore è pronta.

---

### 👥 Il Team e la Ripartizione delle Responsabilità

```mermaid
flowchart TD
    subgraph Dati & Modelli ["🔬 Area Data Science & Analisi"]
        A["📊 Amanda<br/><b>Data Analyst & Feature Engineering</b><br/>• Esplorazione dati & famiglia (B1)<br/>• Invenzione 5 feature & trend (B2)<br/>• Analisi scorte di sicurezza (B8)"]
        G["🤖 Giuseppe<br/><b>Machine Learning Specialist</b><br/>• Selezione dei 4 modelli candidati (B5)<br/>• Grid Search con CV a 5 fold (B6)<br/>• Analisi modelli non lineari"]
    end

    subgraph Sviluppo & Ingegneria ["💻 Sviluppo, Pipeline & Git"]
        LC["⌨️ Lucas Correia (io)<br/><b>Lead Developer & Git Coordination</b><br/>• Coordinamento del codice nel notebook<br/>• Esecuzione test assert e controlli<br/>• Gestione e push su GitHub"]
        LM["💻 Luca Motta<br/><b>Data Engineering Specialist</b><br/>• Costruzione matrici X e target y<br/>• Implementazione split temporale (B3)<br/>• Calcolo baseline a 3 mesi (B4)"]
    end

    subgraph Metriche & Diario ["📝 Metriche, Diario & Business"]
        M["📝 Matteo Landucci<br/><b>Diario & Metrics Coordinator</b><br/>• Compilazione Scheda del Gruppo (Cella 42)<br/>• Monitoraggio MAE (B4-B6) e settembre (B7)<br/>• Esperimento di retraining mensile"]
    end

    A <-->|Collaborano su dati & feature| G
    A & G -->|Passano formule & iperparametri| LC & LM
    LC & LM -->|Forniscono metriche & plot| M
    LC & LM & G & M & A --> Rel["🎓 Relazione per il Professore & Presentazione"]
```

---

### 📌 Dettaglio dei Ruoli e delle Mansioni

| Componente | Focus Operativo | Compiti Svolti |
|---|---|---|
| **⌨️ Lucas Correia (io)** | **Lead Developer & Git** | • Coordinamento generale della pipeline nel notebook.<br/>• Scrittura del codice di addestramento, previsione e controlli `assert`.<br/>• Gestione del version control e pubblicazione sul repository GitHub. |
| **💻 Luca Motta** | **Data Engineering** | • **Blocco 3:** Implementazione dello split temporale onesto (nessuna fuga di dati dal futuro).<br/>• **Blocco 4:** Creazione ed esecuzione vettoriale della baseline (media 3 mesi).<br/>• Supporto alla strutturazione dei DataFrame di Scikit-learn. |
| **📊 Amanda** | **Dati, Feature & Magazzino** | • **Blocco 1:** Selezione famiglia *Tenute e guarnizioni* (765 articoli attivi con vendite $\ge 12$). Analisi dei pattern di vendita (regolari, a ondate, picco unico).<br/>• **Blocco 2:** Progettazione delle 5 nuove feature matematiche.<br/>• **Blocco 8:** Analisi di business sulle scorte di sicurezza rispetto al sistema aziendale. |
| **🤖 Giuseppe** | **Algoritmi & Ottimizzazione** | • **Blocco 5:** Configurazione della gara tra 4 modelli (`LinearRegression`, `kNN`, `DecisionTree`, `RandomForest`).<br/>• **Blocco 6:** Tuning con `GridSearchCV` a 5 fold e selezione del modello sigillato (*Random Forest*).<br/>• Analisi del crollo di kNN e stabilità delle foreste casuali. |
| **📝 Matteo Landucci** | **Diario & Metrics Coordinator** | • Compilazione completa della **Scheda del Gruppo** (Cella 42).<br/>• Tracciamento e confronto delle MAE (Baseline: 6.79 vs Random Forest: 6.67 $\rightarrow$ +1.8%).<br/>• **Blocco 7:** Conduzione dell'esperimento di retraining mensile e analisi del mese di settembre (+2.6% vs baseline). |

---

## 📊 Stato Avanzamento: Cosa Abbiamo Fatto (Blocchi 1 – 8)

Tutti i blocchi sono stati completati con successo e convalidati:

| Blocco | Obiettivo & Attività | Esito & Metriche Chiave | Stato |
|:---:|:---|:---|:---:|
| **1** | **Con quali dati lavoro?** Caricamento dataset, selezione della famiglia *Tenute e guarnizioni*, filtro articoli attivi ($\ge 12$ pezzi). | **765 articoli attivi** selezionati su 7.771 totali. | ✅ **OK** |
| **2** | **Cosa do in pasto al modello?** Creazione di 5 feature: `media_6_mesi`, `std_6_mesi`, `trend_recente` ($lag_1 - lag_2$), `max_6_mesi`, `lead_time_days`. | **8.415 esempi** generati con 8 feature complessive in $X$. | ✅ **OK** |
| **3** | **Quando il test è onesto?** Split temporale rigoroso: Train (aprile 2025 – giugno 2026), Test (luglio – agosto 2026). Nessuna contaminazione temporale. | **6.885 train**, **1.530 test**. | ✅ **OK** |
| **4** | **Battere la baseline?** Calcolo della baseline predittiva semplice (media uscite degli ultimi 3 mesi). | **MAE Baseline = 6.79 pezzi** (soglia minima da battere). | ✅ **OK** |
| **5** | **Gara tra modelli:** Addestramento e test di Linear Regression, kNN ($k=5$), Decision Tree e Random Forest. | **Vince Random Forest** con **MAE = 6.67** (kNN crolla a 14.62). | ✅ **OK** |
| **6** | **Tuning iperparametri:** Ottimizzazione con 5-fold CV. Sigillo del modello definitivo. | Modello sigillato: **Random Forest** (200 alberi, depth 5). **MAE 6.67 (+1.8% vs baseline)**. | ✅ **OK** |
| **7** | **Riallenare ogni mese?** Test su settembre 2026 con modello fisso vs modello riallenato mensilmente. | Settembre difficile (post-ferie): **MAE 15.96 vs baseline 16.39 (+2.6%)**. Riallenare varia per mese (diff media -0.063 pezzi). | ✅ **OK** |
| **8** | **Decisione operativa di magazzino:** Calcolo scorta di sicurezza ($SS$) e punto di riordino ($ROP$) per ottobre 2026 e confronto con il sistema reale. | Nostro $ROP$ medio: 16.3 pezzi vs 30.4 del sistema. Valore merce: 322k€ vs 293k€. | ✅ **OK** |

---

## 📄 File di Documentazione e Consegna per il Professore

- **Relazione Ufficiale:** [`RELAZIONE_FINALE_PROFESSORE.md`](RELAZIONE_FINALE_PROFESSORE.md) e la versione stampabile [`RELAZIONE_FINALE_PROFESSORE.html`](RELAZIONE_FINALE_PROFESSORE.html).
- **Notebook Verificato:** [`project_work_2_building_blocks.ipynb`](project_work_2_building_blocks.ipynb) con codice e scheda del gruppo (Cella 42).
- **Presentazione del Team:** [`PRESENTAZIONE.md`](PRESENTAZIONE.md) e slide interattive in [`presentazione.html`](presentazione.html).
