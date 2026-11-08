# Piano di collaudo P0/P1

Stato: procedure proposte, **nessuna prova eseguita**.

Per ogni risultato registrare data, operatore, scheda/revisione, commit e versione firmware, configurazione, alimentatore, pompa, substrato e strumenti. Conservare dati raw e foto utili insieme al rapporto della prova.

| Test | Procedura | Criterio di esito |
|---|---|---|
| T01 | Osservare il comando e la pompa durante alimentazione, reset e brownout | Nessuna attivazione involontaria; OFF dopo reset |
| T02 | Simulare serbatoio basso e cavo livello scollegato prima e durante un ciclo | Avvio inibito o arresto entro il tempo massimo di risposta da specificare |
| T03 | Provare sonda scollegata, misura fuori range/obsoleta e calibrazione invalida | Blocco; diagnostica coerente. Documentare guasti non distinguibili da una lettura valida |
| T04 | Richiedere cicli manuali/automatici, anche ripetuti, oltre i limiti | Durata massima, pausa e budget rispettati senza aggiramenti |
| T05 | Spegnere HA e poi togliere il Wi-Fi oltre i timeout configurati | Logica locale operativa; nessuna perdita dei limiti; riconnessione verificata |
| T06 | Confrontare letture raw con pompa spenta/accesa e dopo irrigazione | Misurare disturbi e ritardo di assorbimento; fissare limiti accettabili prima di dichiarare il superamento |
| T07 | Riavviare durante ciclo/pausa e ripetere dopo aver esaurito il budget; provare dati persistenti assenti | Pompa OFF, nessuna ripresa del ciclo, nessun budget ripristinato in modo permissivo |
| T08 | Misurare volume erogato e verificare flusso a pompa spenta a diverse quote | Caratterizzazione portata e assenza di flusso incontrollato nel montaggio scelto |

T01-T04 e T07 sono prerequisiti per le prove automatiche con acqua; iniziare verificando il comando con carico simulato. La validazione su pianta richiede inoltre T05, T06, T08 e una prova prolungata con durata e criteri definiti.
