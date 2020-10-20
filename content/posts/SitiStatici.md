---
title: "La relazione di trust.."
date: 2020-10-20T14:55:20+02:00
draft: false
---
La collega mi chiama: il computer è bloccato non riesco ad accedere.
Mi siedo alla postazione e controllo il PC fermo nella schermata CTRL + ALT + CANC.
Premo la combinazione e provo il login come Administrator nella rete locale.

> “La relazione di trust tra questa workstation e il dominio primario non riuscita”.

Mi pareva di aver già sistemato un tempo la cosa e probabilmente DuckDuckGo mi rinfrescherà la memoria.
Sembra in effetti semplice la risoluzione che il supporto tecnico di Windows fornisce a questa pagina:
[https://support.microsoft.com/it-it/help/2771040/the-trust-relationship-between-this-workstation-and-the-primary-domain](https://support.microsoft.com/it-it/help/2771040/the-trust-relationship-between-this-workstation-and-the-primary-domain)

Ritorno al PC riavvio e accedo ad Administrator del PC (e non della rete locale).
**La password. Primo tentativo vuota, a vuoto.**
Riprovo con le password conosciute.
Niente.
Panico.
Inizio la mia lunga giornata a cercare una soluzione. Connessione da ufficio lentissima, non riesco a scaricare a modo i tool che la ricerca su Internet mi dice.
La ricerca si concentra su come resettare la password di Administrator. In rete si trova di tutto. Provo con il safe mode: niente.
Tento con il safe mode con console. Di nuovo nulla di fatto, la console non esce e mi presenta sempre il famigerato CTRL + ALT + CANC.
Provo a scaricare windows password recovery ma la versione free non consente nulla.
Ancora ricerca su internet ma pare nessuno abbia questo problema.
Ritorno allora su un tool di reset della password. Scarico (in oltre 45 minuti..) Ophcrack.
Lo carico su una penna USB che rendo bootabile.
Procedo sul pc “malato” ma dei 3 account presenti non riesce a risolvere la password di nessuno di essi.
**E’ quasi ora di pranzo e il computer è sempre bloccato.**
Ancora rete, ancora forum, ancora tentativi.
Lancio il download di un programmino che promette bene: [http://pogostick.net/~pnh/ntpasswd/](http://pogostick.net/~pnh/ntpasswd/)
Fantastico il loro sito (schermata grigio con caratteri neri e bottoni “primi anni 2000 style”. Parte il download. Oltre 20 minuti.
Seguo le istruzioni:
>How to make an bootable USB drive
Copy all the files that is inside the usbXXXXXX.zip or on the CD onto an usb drive, directly on the drive, not inside any directory/folder.
It is OK if there are other files on the USB drive from before, they will not be removed.
Install bootloader on the USB drive, from command prompt in windows (start the command line with “run as administrator” if possible)
X:syslinux.exe -ma X:
Replace X: with the drive letter the USB drive shows up as (DO NOT USE C:)
If it seems like nothing happened, it is usually done.
However, a file named ldlinux.sys may appear on the USB drive, that is normal.
It should now in theory be bootable.
Please know that getting some computers to boot from USB is worse than from CD, you may have to change settings, or some will not simply work at all.

Però io sto lavorando da mac… Prendo un altro computer, windows e dopo qualche minuto lancio un prompt dei comandi come amministratore (certo che il terminale mac o la shell di linux sono più comodi ma il prompt per renderlo amministratore lo fai cliccando con tasto destro e lanciarlo come “Run as administrator”.
Seguo i dettami del sito e finalmente ho la penna usb pronta.
Inserisco nel PC bloccato e lancio il boot da USB.
Mi carica un OS minimale senza grafica. Seguo i passi.
Mi chiede quale utente voglio modificare e scelgo un utente terzo (rispetto l’admin e il guest) ma sempre con diritti di amministratore del sistema.
Resetto la password ed esco.
Riavvio il pc ma nulla, l’inserimento della password vuota non funziona ed anzi mi blocca l’utente.
Ci riprovo. Ma questa volta salvo la modifica (nei precedenti tentativi lasciavo l’opzione di default N).
Finalmente al riavvio e alla selezione dell’utente la password vuota funziona.
Accedo al PC. E da questo punto in poi posso modificare le password (anche quella da Amministratore!) e così poi seguire la prima semplice guida per sistemare l’errore iniziale:


```sh
Utilizzare un account di amministratore locale per l’accesso al computer.
```
```sh
Selezionare Start, premere e tenere premuto (o destro) Computer > , proprietà.
```
```sh
Selezionare Modifica impostazioni accanto al nome del computer.
```
```sh
Nella scheda Nome Computer , selezionare Modifica.
```
```sh
Sotto il titolo di membro di , selezionare gruppo di lavoro, digitare un nome di gruppo di lavoro e quindi scegliere OK.
```
```sh
Quando viene chiesto di riavviare il computer, scegliere OK.
```
```sh
Nella scheda Nome Computer , selezionare Modifica nuovamente.
```
```sh
Sotto il titolo, membro del dominio selezionare e quindi digitare il nome di dominio.
```
```sh
Fare clic su OK e quindi digitare le credenziali dell’utente che disponga delle autorizzazioni nel dominio.
```
```sh
Quando viene chiesto di riavviare il computer, scegliere OK.
```
```sh
Riavviare il computer.
```
Finalmente dopo una estenuante giornata a surfare sul web la collega accede al suo Computer.
