# FloraNode

Nodo per il monitoraggio di un vaso e l'irrigazione automatica locale, con supervisione Home Assistant.

**Stato:** concept / preparazione del prototipo P0. Non sono ancora presenti firmware eseguibile, schematici o PCB validati.

## Da dove iniziare

1. Leggere il [concept originale v0.1](docs/concept/FloraNode_Concept_Architettura_v0.1.md).
2. Definire i [requisiti del prototipo](docs/requirements.md) e i valori ancora da determinare.
3. Confermare le [decisioni progettuali proposte](docs/decisions/README.md).
4. Scegliere i componenti, completare il pinout e montare il circuito da banco.
5. Implementare e verificare i [collaudi P0/P1](tests/README.md) prima delle prove su pianta.

## Struttura

| Percorso | Contenuto |
|---|---|
| `docs/concept/` | Documento di partenza, conservato come riferimento storico |
| `docs/requirements.md` | Requisiti verificabili e parametri aperti |
| `docs/decisions/` | Scelte, motivazioni, alternative e stato di approvazione |
| `hardware/` | Componenti, pinout, schemi, PCB e BOM |
| `firmware/` | Configurazione e logica locale del nodo |
| `mechanical/` | Custodia, tubazioni e montaggio |
| `tests/` | Procedure di collaudo e risultati sperimentali |

Le sottocartelle per KiCad, ESPHome, CAD ed esportazioni verranno aggiunte insieme ai relativi sorgenti. Gli output di fabbricazione saranno associati alla revisione hardware e a un commit preciso.

## Regole iniziali

- Distinguere sempre proposte, decisioni confermate e risultati misurati.
- Home Assistant supervisiona; il nodo applica limiti e interblocchi anche offline.
- Comandi manuali e automatici attraversano gli stessi controlli di sicurezza.
- Nessuna credenziale Wi-Fi, chiave API o password OTA nel repository.
- Conservare i sorgenti dei progetti; non versionare cache e build intermedie.
- Registrare scheda, firmware, configurazione e condizioni per ogni prova.

La licenza del progetto è ancora da scegliere, distinguendo documentazione, firmware e hardware. La pubblicazione del repository non concede automaticamente una licenza di riuso.
