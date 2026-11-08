# Hardware

Stato: nessuno schema o PCB implementato.

Prima del cablaggio P0 raccogliere:

- Codice esatto della dev board e link a schema e pinout.
- Modello pompa, tensione, corrente di spunto/regime, portata e prevalenza.
- Modello della sonda, alimentazione, range di uscita e compatibilità ADC a 3,3 V.
- Sensore I2C, interfaccia livello e connettori.
- Schema di alimentazione, driver, protezioni e stato elettrico del comando durante reset.
- Tabella GPIO, inclusi USB, pin di boot e margine per diagnostica.

Budget preliminare delle funzioni: un ingresso terreno, due linee I2C, un ingresso livello, un'uscita pompa; aggiungere eventuali LED/pulsante e diagnostica. Il pinout definitivo dipende dal modulo scelto.

Per Rev.A aggiungere progetto KiCad, librerie necessarie, BOM con codici produttore, test point e procedura di primo avvio. Gerber ed esportazioni destinati alla fabbricazione devono indicare revisione e commit di origine.
