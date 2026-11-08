# Firmware

Stato: nessuna configurazione eseguibile. Proposta: ESPHome con framework ESP-IDF e API nativa Home Assistant.

Definire prima la macchina a stati: disabilitato, attesa misure valide, pronto, irrigazione, assorbimento/pausa, blocco. Un unico percorso autorizza l'attivazione della pompa, sia per richieste manuali sia automatiche. Configurazioni fuori limite devono essere rifiutate.

Prima di implementare:

- Confermare scheda e pinout; non pubblicare YAML con pin ipotetici.
- Specificare spegnimento, cancellazione del ciclo e inibizione durante boot/OTA.
- Definire gestione persistente di budget e pausa: riavviare non deve consentire di aggirare i limiti.
- Definire cosa succede senza ora valida; la sincronizzazione con HA non può essere necessaria per i blocchi.
- Valutare esplicitamente `api.reboot_timeout` e `wifi.reboot_timeout`: ESPHome può riavviare il dispositivo quando manca la connessione. Disabilitare tali riavvii è una possibilità da verificare anche rispetto al recupero della rete, non una soluzione automatica a tutti i guasti.
- Scegliere e fissare la versione ESPHome verificata; includere istruzioni di validazione, compilazione e flash insieme al primo firmware.
- Aggiungere un esempio delle chiavi richieste per `secrets.yaml`, senza credenziali reali.

Riferimenti: [ESP32](https://esphome.io/components/esp32/), [API](https://esphome.io/components/api/), [Wi-Fi](https://esphome.io/components/wifi/).
