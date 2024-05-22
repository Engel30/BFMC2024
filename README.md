Codice di controllo per il basso livello ai fini della _Bosch Future for Mobility Challenge 2024_.

I seguenti codici sono stati utilizzati per pilotare una macchina con motore elettrico brushless, permettendo di:
- Controllo del motore mediante utilizzo di un PI
- Controllo di un servo motore per lo sterzo
- Acquisizione di dati da un sensore IMU
- Comunicazione seriale con una raspberry

### Scopo dei diversi codici
- **BFMC2024**: controllo del motore brushless
- **BFMC2024_BRUSHED**: stesso codice del precedente, ma il motore brushless è sostituito con un motore a spazzole
- **Lanekeeping v1**: versione di partenza del codice, con motore a spazzole

### Schema di connessione elettrico
Di seguito sono riportate le connessioni tra la scheda STM32F401RE e l'hardware aggiuntivo necessario per la corretta operazione del sistema. 

> Nota: questo schema é valido solo per la versione dotata di motore brushless, in quanto il motore DC brushed richiede un driver con un pinout differente

![schema.pdf](https://github.com/Engel30/BFMC2024/files/15400843/schema.pdf)
