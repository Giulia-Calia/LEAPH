# effectors_classifier

## Training/Test Dataset characteristics 
### 01072022_version
Il set di proteine non effettrici e' il risultato del filtraggio per annotazione (tutte le proteine annotate come effettore, o con il nome di un effettore nell'annotazione, sono state rimosse), per lunghezza della sequenza proteica (tenute solo le proteine che hanno lunghezza uguale o comparabile (+- std), a quella degli effettori), per similarita' con le sequenze proteiche degli effettori (utilizzando la formula di correlazione %identita'/lunghezza dell'allineamento descritta in Rost, B. Twilight zone of protein sequence alignments. Protein Eng. 12, 85–94 (1999).

### merging dei set 
Un primo dataset e' stato creato unendo il set di effettori con quello di non effettori, tenendo solo le colonne in comune. Questo e' uno dei casi piu'stringenti perche' abbiamo la classe dei negativi (non effettori) che e' molto simile alla classe positiva (effettori) quindi se raggiungioamo performance del modello buone gia' in questo caso, andando ad introdurre variabilita' successivamente, il modello dovrebbe rimanere consistente con la classificazione. 

### K-fold Cross Validation
Ho utilizzato una 5-fold cross validation fissando il seed per avere sempre la stessa base di partenza. In questo modo ottengo per ogni fold un train e un test set, per ogni fold calcolo il numero ottimale di alberi da avere nella foresta e calcolo l'accuratezza dell'algoritmo quando applicato al caso attuale. Per ogni fold mi salvo l'accuratezza e poi alla fine faccio una media di tutti i fold. Se l'accuratezza e' buona salvo il modello in un file pickle che puo' essere tranquillamente caricato quando si vuole applicare questo esatto modello ai dati reali 
