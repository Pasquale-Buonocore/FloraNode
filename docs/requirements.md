# Requisiti del prototipo P0/P1

Stato: proposta derivata dal concept v0.1, da confermare prima dell'implementazione.
Questo documento raccoglie il lavoro corrente; il concept resta un riferimento storico.

## Perimetro proposto

Un vaso, una pompa, sonda capacitiva esterna sostituibile, sensore T/RH e soglia di livello serbatoio. Alimentazione continua USB-C 5 V. Nessun display, batteria o solare nel primo prototipo.

## Comportamenti da verificare

| ID | Requisito | Evidenza attesa |
|---|---|---|
| R01 | Boot, reset e aggiornamento devono portare la pompa a OFF; nessuna ripresa automatica di un ciclo interrotto | T01, T07 |
| R02 | Serbatoio basso o segnale livello mancante inibiscono l'avvio e interrompono un ciclo | T02 |
| R03 | Misura terreno invalida, obsoleta o calibrazione incoerente impediscono l'irrigazione | T03 |
| R04 | Ogni attivazione rispetta durata massima, pausa minima e budget cumulato | T04 |
| R05 | Il comando manuale rispetta gli stessi interblocchi; richieste ripetute non prolungano indefinitamente il ciclo | T04 |
| R06 | Perdita di Wi-Fi o HA non provoca attivazioni né annulla limiti e stato di blocco | T05 |
| R07 | La lettura del terreno è filtrata e viene atteso l'assorbimento dopo ogni impulso d'acqua | T06 |
| R08 | Sono disponibili dati raw, stato calibrazione, causa di blocco e ultima irrigazione | T03, T05 |
| R09 | Un reset non può azzerare il budget e consentire irrigazioni ripetute; dati persistenti assenti/corrotti richiedono una politica conservativa | T07 |

La disconnessione della sonda analogica potrebbe produrre valori plausibili: definire la diagnostica circuitale prima di dichiarare soddisfatto R03. Un contatto livello cablato per segnalare guasto su circuito aperto non rileva necessariamente un cortocircuito.

## Parametri da determinare sul banco

| Parametro | Come determinarlo |
|---|---|
| Pompa e alimentatore | Tensione nominale, corrente di avvio e regime, prevalenza e portata misurate |
| Durata massima per ciclo | Volume massimo accettabile e portata nelle condizioni di montaggio |
| Pausa tra cicli | Ritardo di assorbimento e risposta del sensore |
| Budget cumulato | Limite in secondi di pompa; conversione in ml solo dopo caratterizzazione |
| Finestra del budget | Preferibile finestra mobile; definire funzionamento senza ora di rete e dopo reset |
| Validità del sensore | Range, timeout, diagnostica cavo, calibrazione per substrato |
| Soglie e isteresi | Prove sul vaso/substrato scelto |
| Ingombro e costo obiettivo | Vincoli di montaggio e BOM, prima del PCB |

Una percentuale normalizzata tra due punti di calibrazione non è automaticamente contenuto volumetrico d'acqua. Etichettare la misura di conseguenza.
