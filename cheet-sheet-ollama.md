# Ollama Cheat Sheet per Principianti e Uso Comune

Questo cheat sheet riassume i comandi Ollama essenziali e fornisce esempi pratici per iniziare a utilizzare modelli linguistici localmente.

## Comandi Fondamentali

* **Avviare Ollama Server (in background):**
    ```bash
    ollama serve
    ```
    *(Solitamente si avvia automaticamente all'installazione o al primo utilizzo di un comando)*

* **Eseguire un Modello:**
    ```bash
    ollama run <nome_modello>
    ```
    * **Esempio:** Eseguire il modello Llama 2
        ```bash
        ollama run llama2
        ```
    * Ollama scaricherà il modello se non è presente localmente e avvierà una sessione interattiva.

* **Elencare i Modelli Scaricati:**
    ```bash
    ollama list
    ```
    * Mostra la lista dei modelli disponibili localmente, la loro dimensione e data di creazione.

* **Scaricare un Modello Specifico (senza eseguirlo subito):**
    ```bash
    ollama pull <nome_modello>
    ```
    * **Esempio:** Scaricare il modello `mistral`
        ```bash
        ollama pull mistral
        ```

* **Rimuovere un Modello:**
    ```bash
    ollama rm <nome_modello>
    ```
    * **Esempio:** Rimuovere il modello `llama2`
        ```bash
        ollama rm llama2
        ```

* **Mostrare Informazioni su un Modello:**
    ```bash
    ollama show <nome_modello>
    ```
    * Visualizza dettagli sul modello, come i layer, la licenza e il prompt di sistema predefinito.

* **Creare un Modello Personalizzato da un `Modelfile`:**
    ```bash
    ollama create <nome_modello_personalizzato> -f <path_to_Modelfile>
    ```
    * **Esempio:** Creare un modello chiamato `codice-specializzato` usando il file `Modelfile.codice`
        ```bash
        ollama create codice-specializzato -f Modelfile.codice
        ```

* **Copiare un Modello Esistente e Modificarlo:**
    ```bash
    ollama cp <nome_modello_esistente> <nuovo_nome_modello>
    ```
    * **Esempio:** Copiare `llama2` in `llama2-italiano`
        ```bash
        ollama cp llama2 llama2-italiano
        ```
    * Dopo la copia, puoi usare `ollama show llama2-italiano` per vedere il `Modelfile` generato e modificarlo con `ollama create` usando un file.

## Casi d'Uso Comuni ed Esempi

**1. Conversazione Generale:**

```bash
ollama run llama2 
```

**2. Rispondere a Domande:**
ollama run mistral
>>> Qual è la capitale dell'Italia?
La capitale dell'Italia è Roma.

**3. Generazione di Testo Creativo:**

Bash

ollama run llama2
>>> Scrivi una breve storia su un gatto che esplora una vecchia libreria.
Tra scaffali polverosi e l'odore di carta antica, un gatto soriano di nome Ombra si avventurò. I suoi occhi ambrati brillavano nella penombra, catturando i titoli dorati sui dorsi dei libri...

**4. Generazione di Codice (a seconda del modello):**

Bash

ollama run codellama
>>> Scrivi una semplice funzione in Python che saluta un nome dato come input.
def saluta(nome):
  return f"Ciao, {nome}!"

print(saluta("Alice"))


**5. Analisi di Testo Semplice (a seconda del modello):**

Bash

ollama run llama2
>>> Qual è il sentimento in questa frase: "Sono molto felice di usare Ollama!"
Il sentimento in questa frase è positivo.


**6. Utilizzo di un Modello Specifico per un Task (es. traduzione):**

Potrebbe non esserci un modello "traduttore" puro in Ollama, ma si possono usare modelli generalisti con prompt specifici:

Bash

ollama run llama2
>>> Traduci "Ciao, come stai?" in inglese.
Hello, how are you?


**7. Creazione di un Modello Personalizzato (tramite Modelfile - Esempio):**

Crea un file chiamato Modelfile.italiano con il seguente contenuto:

Dockerfile

FROM llama2

SYSTEM """
Sei un assistente utile che risponde sempre in italiano.
"""
Poi esegui:

Bash

ollama create mio-llama-italiano -f Modelfile.italiano
Ora puoi usare il tuo modello personalizzato:

Bash

ollama run mio-llama-italiano
>>> Parlami del tempo oggi.
Oggi, le previsioni del tempo indicano...


**8. Utilizzo di Variabili d'Ambiente (Esempio per proxy):**

Se la tua rete aziendale richiede un proxy:

Bash

export HTTP_PROXY="http://tuo_proxy:porta"
export HTTPS_PROXY="http://tuo_proxy:porta"
ollama pull mistral


** Suggerimenti e Note**
I nomi dei modelli sono case-sensitive.
La prima volta che esegui un modello, Ollama lo scaricherà, il che potrebbe richiedere del tempo a seconda della dimensione del modello e della tua connessione internet.
Puoi interrompere una sessione interattiva con un modello premendo Ctrl + D o digitando /bye.
Esplora la documentazione ufficiale di Ollama per funzionalità più avanzate e opzioni di configurazione.
La disponibilità e le capacità dei modelli variano. Sperimenta con diversi modelli per trovare quello più adatto alle tue esigenze.
Questo cheat sheet dovrebbe fornire un solido punto di partenza per utilizzare Ollama nella tua azienda.
Ricorda di consultare la documentazione ufficiale per informazioni più dettagliate e funzionalità avanzate.
