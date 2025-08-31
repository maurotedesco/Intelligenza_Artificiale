# Glossario di Intelligenza Artificiale

Questo glossario fornisce definizioni concise dei termini fondamentali che incontrerai durante il corso di Intelligenza Artificiale.

-   **Intelligenza Artificiale (AI):** Simulazione dell'intelligenza umana nelle macchine, che permette loro di percepire, ragionare, apprendere e agire.
-   **Machine Learning (ML):** Sottocampo dell'AI che permette ai sistemi di imparare dai dati senza essere programmati esplicitamente.
-   **Deep Learning (DL):** Sottocampo del ML basato su reti neurali artificiali con molti strati (profonde), capaci di apprendere rappresentazioni complesse dei dati.
-   **Rete Neurale Artificiale (RNA):** Modello computazionale ispirato al cervello, composto da nodi (neuroni) interconnessi organizzati in strati.
-   **Neurone (o Nodo):** Unità di elaborazione fondamentale in una rete neurale che riceve input, li elabora e produce un output.
-   **Addestramento (Training):** Processo in cui un modello ML impara dai dati per migliorare le sue prestazioni e generalizzare.
-   **Dataset:** Raccolta strutturata di dati usata per addestrare, validare e testare un modello ML.
-   **Feature (Caratteristica):** Variabile di input usata da un modello per fare previsioni o identificare pattern.
-   **Label (Etichetta):** Variabile di output o valore target che un modello ML cerca di prevedere (nel caso dell'apprendimento supervisionato).
-   **Apprendimento Supervisionato:** Tipo di ML dove il modello impara da dati etichettati (input-output noti).
-   **Apprendimento Non Supervisionato:** Tipo di ML dove il modello trova pattern e strutture in dati non etichettati.
-   **Apprendimento per Rinforzo:** Tipo di ML dove un agente impara a prendere decisioni interagendo con un ambiente per massimizzare una ricompensa.
-   **Overfitting:** Quando un modello impara troppo bene i dati di addestramento, perdendo la capacità di generalizzare su nuovi dati.
-   **Underfitting:** Quando un modello è troppo semplice e non riesce a catturare i pattern fondamentali nei dati di addestramento.
-   **Algoritmo:** Insieme di istruzioni ben definite per risolvere un problema o eseguire un compito.
-   **Modello:** La rappresentazione matematica o computazionale appresa dai dati durante l'addestramento, usata per fare previsioni.
-   **Funzione di Attivazione:** Funzione che determina l'output di un neurone in una rete neurale, introducendo non linearità.
-   **Backpropagation:** Algoritmo per addestrare reti neurali, che propaga l'errore all'indietro per aggiornare i pesi del modello.
-   **Gradient Descent:** Algoritmo di ottimizzazione usato per minimizzare la funzione di costo di un modello, muovendosi nella direzione del gradiente negativo.
-   **Funzione di Costo (o Loss Function):** Misura l'errore tra le previsioni del modello e i valori reali, guidando l'ottimizzazione.
-   **Iperparametri:** Parametri che non vengono appresi dal modello ma sono impostati prima dell'addestramento (es. learning rate, numero di strati).
-   **Natural Language Processing (NLP):** Sottocampo dell'AI che si occupa dell'interazione tra computer e linguaggio umano.
-   **Computer Vision:** Sottocampo dell'AI che permette ai computer di "vedere" e interpretare immagini e video.
-   **Bias (Pregiudizio):** Errore sistematico in un modello o nei dati che porta a risultati ingiusti o distorti, spesso a causa di dati di addestramento non rappresentativi.
-   **Accuratezza (Accuracy):** Percentuale di previsioni corrette su tutte le previsioni fatte da un modello.

**Glossario: Agenti AI**

*   **Agente AI:** Entità che percepisce l'ambiente e agisce su di esso.
*   **Ambiente:** Il contesto in cui l'agente opera e interagisce.
*   **Percezione (Percept):** L'input che l'agente riceve dall'ambiente in un dato istante.
*   **Azione:** L'output che l'agente esegue sull'ambiente.
*   **Funzione Agente:** La mappatura concettuale da sequenze di percezioni ad azioni.
*   **Programma Agente:** L'implementazione concreta della funzione agente.
*   **Razionalità:** La capacità dell'agente di agire in modo da massimizzare la sua misura di performance, date le sue percezioni e conoscenze.
*   **Autonomia:** La capacità dell'agente di apprendere e adattarsi, senza dipendere interamente dalla conoscenza pre-programmata.
*   **Agente Riflesso Semplice:** Agisce basandosi solo sulla percezione corrente.
*   **Agente Riflesso basato su Modello:** Mantiene uno stato interno (modello) dell'ambiente per decidere le azioni.
*   **Agente basato su Obiettivi:** Agisce per raggiungere stati futuri desiderati (obiettivi).
*   **Agente basato su Utilità:** Agisce per massimizzare una funzione di utilità che quantifica la desiderabilità degli stati.
*   **Agente di Apprendimento:** Migliora le sue prestazioni nel tempo attraverso l'esperienza.

---

**Glossario: RAG (Retrieval-Augmented Generation)**

*   **RAG (Retrieval-Augmented Generation):** Tecnica che potenzia i Large Language Models (LLM) recuperando informazioni rilevanti da una base di conoscenza esterna prima di generare una risposta.
*   **Recupero (Retrieval):** La fase in cui il sistema cerca e seleziona documenti o frammenti di testo pertinenti da una base di conoscenza esterna, basandosi sulla query dell'utente.
*   **Generazione (Generation):** La fase in cui l'LLM utilizza la query originale e le informazioni recuperate per formulare una risposta coerente e informata.
*   **Base di Conoscenza Esterna:** Un archivio di dati (es. documenti, database, articoli) da cui il sistema RAG recupera le informazioni.
*   **Embedding (Vettorizzazione):** La rappresentazione numerica di testo (o altri dati) in uno spazio vettoriale, utilizzata per confrontare la somiglianza semantica tra query e documenti.
*   **Allucinazione (Hallucination):** La tendenza di un LLM a generare informazioni false o fuorvianti, presentandole come fatti. RAG mira a ridurle.
