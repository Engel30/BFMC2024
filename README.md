Codice di controllo per il basso livello ai fini della _Bosch Future for Mobility Challenge 2024_.

I seguenti codici sono stati utilizzati per pilotare una macchina con motore elettrico brushless, permettendo di:
- Controllo del motore mediante utilizzo di un PI ([versione brushless](https://www.hobbywing.com/en/products/quicrunfusionse.html), [versione brushed]())
- Controllo di un servo motore per lo sterzo
- Acquisizione di dati da un sensore IMU Bosch BNO055 ([AdaFruit board](https://learn.adafruit.com/adafruit-bno055-absolute-orientation-sensor))
- Comunicazione seriale con una raspberry Pi 4

### Scopo dei diversi codici
- **BFMC2024**: controllo del motore brushless
- **BFMC2024_BRUSHED**: stesso codice del precedente, ma il motore brushless è sostituito con un motore a spazzole
- **Lanekeeping v1**: versione di partenza del codice, con motore a spazzole

### Schema di connessione elettrico
Di seguito sono riportate le connessioni tra la scheda STM32F401RE e l'hardware aggiuntivo necessario per la corretta operazione del sistema. 

> Nota: questo schema é valido solo per la versione dotata di motore brushless, in quanto il motore DC brushed richiede un driver con un pinout differente

![schema.pdf](https://github.com/Engel30/BFMC2024/files/15400843/schema.pdf)

## Istruzioni per l'uso del codice

Il codice é stato sviluppato unicamente per il microcontrollore STM32F401RE ([link alla pagina del produttore] (https://www.st.com/en/evaluation-tools/nucleo-f401re.html)) pertanto é compatibile solo con esso. Il codice é stato sviluppato interamente sulla piattaforma STM32CubeIDE ([link per la guida di installazione](https://www.st.com/resource/en/user_manual/um2563-stm32cubeide-installation-guide-stmicroelectronics.pdf)), aggiornato alla versione 1.13.2 . 

> NOTA: Il funzionamento del codice dovrebbe essere indipendente dalla versione dell'IDE. iIn caso di problemi di compatibilitá riferirsi alla versione utilizzata durante il periodo di sviluppo

Una volta installato l'IDE é necessario importare il progetto nel proprio workspace e per fare ció é necessario seguire la procedura di import fornita dall'IDE (File -> Import -> General -> Existing Projects into Workspace) e selezionare le cartelle contenenti i progetti specificandone i percorsi del proprio file system su cui sono stati clonati.

Una volta importati i progetti di interesse é necessario navigare verso il main mediante il percorso <<Progetto>> -> Core -> Src -> main.c . 
Una volta aperto il main.c é necessario collegare la board STM al computer mediante un cavo micro usb type B. 

A seguito della connessione tra i due dispositivi si dovrebbe aprire in automatico una cartella (indice del fatto che é stata stabilita con successo la connessione) e dovrebbe accendersi un LED rosso vicino alla porta USB della scheda. 

Stabilita la connessione, per flashare il codice sulla scheda é necessario premere sul tasto "Run as..." dell'IDE e attendere che il codice venga effettivamente caricato sul microcontrollore. 

Per verificare lo stato dell'upload si puó verificare la corretta riuscita della procedura mediante la console dell'IDE nella sezione in basso dell'applicazione oppure basta aspettare che il LED in prossimitá della porta USB passi dallo stato di blinking (a seguito dell'inizio dell'upload del codice) a uno stato rosso fisso. 

Se tutti i passi precedenti sono andati a buon fine é possibile scollegare il cavo USB dalla scheda, che é pronta per operare in modo autonomo.

> NOTA: il microcontrollore puó essere alimentato in piú modi e lo stato di alimentazione é verificabile mediante lo stato di un LED rosso (LD3 PWR).
>
> LD3 PWR acceso indica che la scheda é alimentata correttamente, altrimenti no.
>
> Se disconnettendo il cavo USB LD3 PWR si spegne ma la scheda é alimentata mediante la batteria del veicolo, é indice del fatto che non é stato cortocircuitato il percorso di alimentazione corretto. La configurazione corretta di alimentazione per il caso d'uso é la seconda mostrata nella seguente figura:
> 
> ![Screenshot 2024-05-23 122846](https://github.com/Engel30/BFMC2024/assets/149259996/86354dbd-96cf-4ab6-a22b-86d42d11abf6)
>
