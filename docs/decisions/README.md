# Decisioni progettuali

Aggiornato: 8 novembre 2026. Tutte le scelte sotto sono **proposte**, non decisioni confermate dall'utente.

Quando una scelta viene confermata, registrarla in un file `NNNN-titolo.md` con stato, contesto, alternative, motivazione, conseguenze e criterio di riesame. Non serve creare un documento separato per ogni dettaglio di cablaggio.

| Tema | Proposta | Motivazione / cosa può cambiarla |
|---|---|---|
| Architettura | Un nodo per vaso, controllo locale | Coerente con il concept; rivedere se si passa a un serbatoio con più zone |
| MCU | ESP32-C3 su dev board per P0, poi modulo radio | Carico modesto; confermare GPIO, memoria e comportamento offline sul prototipo |
| Firmware | ESPHome, framework ESP-IDF, API nativa HA | Riduce il lavoro d'integrazione; ESP-IDF dedicato se la logica o la verifica diventano troppo complesse |
| Alimentazione | USB-C 5 V continua | Evita di introdurre subito ricarica e gestione energetica; pompa compatibile da scegliere |
| Terreno | Sonda capacitiva esterna sostituibile per P0 | Permette di confrontare sensori e posizioni senza rifare il PCB del controller |
| T/RH | Sensore digitale I2C | Modello e collocazione da scegliere, evitando calore del regolatore e condensa |
| Livello | Contatto con cablaggio che inibisce la pompa se aperto | Validare polarità, debounce e guasti rilevabili |
| Attuazione | Driver dimensionato sulla pompa reale, stato OFF imposto anche elettricamente | La sola inizializzazione firmware non copre tutto il tempo di boot/reset |
| Sicurezza aggiuntiva | Valutare un limite hardware indipendente di durata | Necessario decidere il comportamento richiesto in caso di blocco MCU; il secondo core non è un controllore indipendente |
| Licenze | Da decidere prima di distribuire sorgenti riutilizzabili | Distinguere codice, hardware e documentazione; verificare ogni materiale riusato |

## ESP32-C3 oppure ESP32-S3

| Caratteristica del chip | C3 | S3 |
|---|---|---|
| CPU | RISC-V, 1 core, fino a 160 MHz | Xtensa LX7, 2 core, fino a 240 MHz |
| SRAM interna | 400 KB | 512 KB |
| Wi-Fi / Bluetooth | Wi-Fi 2,4 GHz + BLE | Wi-Fi 2,4 GHz + BLE |
| Espansione | Verificare GPIO del modulo e della dev board | Più GPIO a livello chip, supporto PSRAM e periferiche per applicazioni più complesse |
| Impiego proposto | Nodo per singolo vaso senza interfaccia grafica | Display evoluto, molti I/O, elaborazione o buffer più grandi |

Il numero di GPIO del chip non corrisponde ai pin liberamente utilizzabili sulla scheda: flash, USB, strapping e periferiche della dev board possono impegnarli. Compilare una tabella pin prima di acquistare o disegnare il PCB.

Per il perimetro attuale il C3 è la proposta preferita. Non occorre dedicare un core ai sensori e uno al Wi-Fi. Un S3 già disponibile può essere usato per il banco senza vincolare la scelta del modulo finale. Il dual-core non offre ridondanza indipendente e non garantisce un ADC più accurato. Consumi e costo vanno confrontati sulle schede e sui moduli concreti, non soltanto sul nome del chip.

## Fonti tecniche

Consultate l'8 novembre 2026:

- [Datasheet ESP32-C3](https://documentation.espressif.com/esp32-c3_datasheet_en.html)
- [Datasheet ESP32-S3](https://documentation.espressif.com/esp32_s3_datasheet_en.pdf)
- [Piattaforma ESP32 in ESPHome](https://esphome.io/components/esp32/)
- [API ESPHome](https://esphome.io/components/api/)
- [Wi-Fi ESPHome](https://esphome.io/components/wifi/)
