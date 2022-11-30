* un linguaggio regolare è un linguaggio definibile tramite una espressione regolare
* Sono molto limitati, essendo troppo semplici. Non possono essere usati per creare un linguaggio di programmazione, ma possono aiutare a definire la sintassi di un lessema
* Esistono linguaggi non regolari, che non possono essere rappresentati da espressioni regolari
* Per analizzare linguaggi simili, avremo bisogno di un analizzatore sintattico, composto da un tokenizer ed un parser
* Il primo trasforma i caratteri in token, lessemi, ed il parser analizza il significato e la correttezza
* L'output sarà un AST (Abstract Syntax Tree), una rappresentazione astratta di un programma 

* Useremo una grammatica CF (Context Free), molto più espressiva di una regolare, per definire le cose che ci mancano
* Essi possiedono un insieme di simboli terminali, pratici, e l'insieme di simboli non terminali, non pratici, e le produzioni, insiemi di coppie
* Linguaggi possono derivare dalle grammatiche, per ogni simbolo non terminale

* Una grammatica è una tripla, insieme di simboli terminali, non terminali e l'insieme di produzioni (coppie di non terminali e definizioni)
* Per capire se una stringa appartiene ad una grammatica si usa la derivazione, riscrivendo ogni non terminale con le sue definizioni
* La derivazione può essere a un passaggio o multipli