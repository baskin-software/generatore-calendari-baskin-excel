# Istruzioni per l'uso del file Excel del campionato

Queste istruzioni valgono per il file `.xlsx` prodotto dal **Generatore Campionato Baskin**. Spiegano passo passo cosa compilare, dove e in che ordine, e soprattutto **cosa non fare** perché calendari, classifiche e riepiloghi continuino a funzionare.

> In breve: si scrive solo nelle celle "bianche" previste (squadre, campi, codici squadra, date, campi di gioco, risultati, designazioni, note). Tutto il resto si calcola da solo. Le colonne nascoste e i fogli nascosti non si toccano. Per cambiare la **struttura** del campionato (gironi, numero di squadre, playoff) si rigenera il file con il generatore, che conserva i dati già inseriti.

---

## 0. Prima di iniziare

1. **Apri il file** con Excel (consigliato Microsoft 365 o 2021 e successivi), LibreOffice Calc oppure Google Sheets.
   * Alla prima apertura il file **si calcola da solo**: nei campionati grandi può servire qualche secondo.
   * In **Google Sheets** carica il file su Drive e aprilo (o salvalo) come Foglio Google.
   * I **loghi** (funzione `IMAGE`) si vedono in Google Sheets ed Excel 365; nelle altre versioni la cella resta vuota, senza conseguenze.
2. **Leggi il foglio `MEMO`**: riassume come è stato generato il file (gironi, playoff, opzioni) e contiene una **riga di controllo** (vedi il punto 11).
3. **Controlla quale modalità ha il file**, indicata nel `MEMO`:
   * **Ricerche per numero di gara** (default): si possono spostare, copiare, aggiungere e cancellare gare a mano nei calendari.
   * **Riferimenti fissi** (versione più leggera, per i campionati molto grandi): le gare **non vanno spostate né aggiunte** a mano.
4. **Tieni una copia** del file appena generato: se qualcosa va storto si riparte da lì (o si reimporta il file nel generatore).

---

## 1. Foglio `Campionato` – Parametri (celle `D2`-`D11`)

| Cella | Cosa contiene | Si può cambiare? |
|---|---|---|
| `D2` | Nome del campionato | Sì |
| `D3`, `D4` | Link pubblici alle immagini dei loghi (facoltativi) | Sì (vedi la nota sui loghi) |
| `D5` | Sigle dei gironi, separate da virgola (es. `A,B` oppure `O,E`) | **No**: sono legate ai fogli e alle formule. Per cambiare i gironi si rigenera il file |
| `D6` | Stagione (es. `2026/2027`) | Sì |
| `D7`, `D8`, `D9` | Punti per vittoria, sconfitta e sconfitta per forfait | Sì, se il regolamento cambia |
| `D10` | Punteggio della gara persa a tavolino (es. `40-0`) | Sì |
| `D11` | Nomi dei gironi per la stampa, nello stesso ordine di `D5` (es. `Gold, Silver`) | Sì |

**Loghi.** Usa solo immagini che hai il diritto di usare (per Baskin ed EISI secondo le indicazioni di EISI), pubblicate su un sito stabile. Le immagini sono **collegate, non incorporate**: se il link smette di funzionare il logo sparisce, ma il file non si rompe.

**Provvedimenti a parte** (solo se l'opzione è stata scelta): in `F2:H4` ci sono il nome del file dei provvedimenti (`H2`), il link per Google Sheets (`H3`) e il nome effettivamente cercato (`H4`). Vedi il punto 8.

---

## 2. Foglio `Campionato` – Squadre (dalla riga 14)

Ogni riga è una squadra.

| Colonna | Cosa scrivere | Attenzione |
|---|---|---|
| `B` – codice | Già compilato (es. `A01`) | **Non cambiarlo**: risultati e classifiche sono collegati al codice. Se proprio serve, va cambiato **anche in tutte le gare dei calendari** (colonne `C` ed `E`) e nel blocco campi; meglio farlo dal generatore |
| `C` – nome | Nome della squadra, nella forma consigliata `Nome-Città PR` | Si può cambiare quando vuoi: calendari e classifiche si aggiornano. Nei calendari compare solo la parte prima del trattino |
| `D` – penalizzazione | Punti di penalizzazione, **con il segno meno** (es. `-2`) | Il valore viene sommato ai punti in classifica: un numero positivo darebbe punti in più |
| `E` – girone | Sigla del girone | Cambiarla **sposta la squadra in classifica**, ma non sposta le sue gare: per dividere o ricomporre i gironi usa il generatore |
| `F` – FC | `S` se la squadra è **fuori classifica** | Le sue gare restano a calendario ma non contano per nessuna delle due squadre; in classifica va in fondo, in giallo |

**Non fare**

* Non inserire o cancellare righe nella tabella squadre e non riordinarla: per aggiungere squadre si rigenera il file.
* Non scrivere nelle colonne grigie o nascoste a destra (posizione, coefficienti, matrici degli scontri diretti).
* Non lasciare due squadre con lo stesso codice.

---

## 3. Foglio `Campionato` – Campi

Sotto la tabella squadre c'è il blocco **CAMPI**:

* una riga per squadra, con lo **stesso codice** della squadra (`A01` = campo di casa di `A01`): nome del campo e link alla mappa;
* le righe `PO1`-`PO8` sono i **campi neutri** (fasi finali, concentramenti);
* `TBD` indica un campo **ancora da definire** (evidenziato in verde nei calendari).

Puoi cambiare nomi e link quando vuoi. I codici non vanno cambiati.

---

## 4. Fogli `Calendario …` – Gare di girone

Ogni gara occupa **tre righe**: intestazione ("Gara N."), riga della gara, riga del campo.

### Cosa compilare per ogni gara

1. **Colonna `C`**: codice della squadra di casa (es. `A03`). **Colonna `E`**: codice della squadra ospite. Il nome compare da solo.
2. **Colonna `F`**: data e ora insieme (es. `12/10/2026 15:30`).
3. **Riga sotto, colonna `I`**: codice del campo (di solito il codice della squadra di casa, oppure `PO1`-`PO8` o `TBD`). Il nome del campo compare da solo.
4. **Colonne `J` e `L`**: punti delle due squadre, a gara giocata.
   * **Gara persa a tavolino**: scrivi il punteggio di `D10` (es. `40` e `0` se perde la squadra ospite, `0` e `40` se perde quella di casa). La classifica applica i punti forfait e il RIEPILOGO la segnala in "Esiti Speciali".
   * **Gara non ancora giocata**: lascia `J` e `L` vuoti (non scrivere `0-0`).

### Cosa non fare

* **Non scrivere i nomi delle squadre** in `C` ed `E`: servono i **codici**.
* **Non scrivere risultati come testo** (es. `"80 - 60"` in una sola cella, oppure `nd`): solo numeri, in `J` e `L`.
* **Non scrivere la data come testo** (es. `16 Mar`): scrivila come data, oppure lascia la cella vuota.
* **Non modificare la colonna `A`** (numero di gara) delle gare esistenti, né la barra "GIORNATA" in cima a ogni giornata.
* **Non toccare le colonne nascoste** a destra (`M` e seguenti): fanno i conti per le classifiche.

### Modifiche a mano: con le **ricerche per numero di gara** (default)

* **Spostare una gara** (es. in un'altra giornata): taglia le sue **tre righe** e incollale sotto la barra della giornata giusta. La giornata si legge dalla barra "GIORNATA" più vicina sopra la gara.
* **Copiare / aggiungere una gara** (recupero, spareggio): copia le **tre righe** di una gara esistente dello stesso foglio, incollale dove serve e poi:
  1. scrivi in colonna `A` un **numero di gara nuovo**, nell'intervallo indicato nel `MEMO` (le gare aggiunte compaiono in fondo a RIEPILOGO, Calendario.ics e Designazioni);
  2. aggiorna codici squadra, data, campo e risultato.
* **Cancellare una gara**: elimina le sue tre righe (oppure svuota codici e risultati). Sparisce da classifiche e riepiloghi senza errori.
* I **numeri di gara ripetuti** nello stesso foglio diventano **rossi**: correggili subito.
* **Non spostare una gara da un foglio calendario a un altro**: ogni gara esistente viene cercata nel suo foglio, e altrove non verrebbe più contata (il controllo del `MEMO` lo segnala). Le gare **aggiunte** con un numero nuovo, invece, vengono trovate in qualunque foglio calendario.
* Un **foglio calendario nuovo** creato a mano **non viene visto**: per aggiungere gironi si rigenera il file.

### Modifiche a mano: con i **riferimenti fissi**

* Compila solo le celle previste (codici, data, campo, risultati).
* **Non spostare, copiare, inserire o cancellare righe** nei calendari: le gare aggiunte non verrebbero contate e quelle spostate verrebbero lette nella posizione sbagliata.
* Per cambiare la struttura (gare in più, giornate diverse) rigenera il file con il generatore.

---

## 5. Fogli `Playoff` e `Torneo Primavera`

* Le squadre del primo turno si riempiono **da sole** dalla classifica (es. `A1` = prima del girone A). I turni successivi prendono vincenti e perdenti delle gare precedenti.
* **Compila solo**: data e ora (`F`), campo (`I` nella riga sotto: di solito `PO1`-`PO8` o `TBD`) e risultato (`J` e `L`). **Nei playoff non ci sono pareggi**: deve sempre esserci una vincente.
* **BYE**: la squadra passa il turno senza giocare. Non scrivere niente in quella gara.
* **Andata e ritorno** (se previsto): sotto la gara di ritorno c'è la **riga dell'esito**, con il totale e la squadra che passa (migliore differenza canestri). In caso di **parità** scrivi `A` (prima squadra dell'andata) o `B` nella casella a destra della riga dell'esito. Le finali sono in gara unica.
* **Tabellone importato con lo schema del file di origine** (indicato nelle note in fondo al foglio): le squadre sono scritte gara per gara nelle colonne `C` ed `E`, con il codice squadra (`A03`) oppure con girone e posizione (`A3`), e i turni successivi non si riempiono da soli.
* **Non fare**: non scrivere i nomi al posto delle formule nelle colonne `B` e `D` e non cambiare gli accoppiamenti del primo turno se non sai cosa stai facendo. Per un tabellone diverso, rigenera il file.

---

## 6. Fogli `Classifica` e `Classifica Finale`

Sono **di sola lettura**: si aggiornano da soli.

* Ordine: punti, poi vittorie negli scontri diretti, quoziente canestri negli scontri diretti, quoziente canestri totale, ordine alfabetico. Le colonne dei criteri di spareggio mostrano un valore solo quando servono davvero.
* Le squadre **fuori classifica** sono in fondo, in giallo, con tutti i valori a `-`.
* Lo sfondo colorato indica le squadre qualificate al playoff.
* **Non scrivere** in questi fogli: ogni valore inserito a mano cancellerebbe una formula.

---

## 7. Designazioni, `Arbitri` e `UdC`

1. Nei fogli **`Arbitri`** e **`UdC`** scrivi, una persona per riga: **nome** (colonna `D`), **email** (colonna `E`, facoltativa) e **indisponibilità / note** (colonna `F`). Le colonne a destra contano da sole quante designazioni ha ciascuno.
2. Nel foglio **`Designazioni`** scegli dagli **elenchi a discesa** gli arbitri (colonne `M`-`O`) e gli Ufficiali di Campo (colonne `P`-`R`) di ogni gara. Le informazioni della gara (squadre, data, campo) si leggono da sole dal calendario.
3. Se la stessa persona è designata **due volte nella stessa gara**, la cella diventa rossa.

**Non fare**

* Non scrivere nomi a mano nelle colonne delle designazioni: usa l'elenco a discesa, altrimenti i conteggi non tornano.
* Non cambiare un nome in `Arbitri`/`UdC` dopo averlo designato: le designazioni già fatte non si aggiornano e vanno riscelte.
* Non inserire righe nel foglio `Designazioni`. Con le ricerche, le gare aggiunte a mano hanno già le loro righe in fondo al foglio.

---

## 8. Note e Provvedimenti disciplinari

* Nei fogli **`Note`** e **`Provvedimenti Disciplinari`** scrivi in colonna `A` il **numero di gara** e in colonna `B` il testo, **una riga per gara**. Il testo compare nel `RIEPILOGO`, nella colonna corrispondente, accanto alla gara giusta, anche se la gara viene spostata.
* **Provvedimenti in una cartella di lavoro a parte** (se l'opzione è stata scelta): i provvedimenti stanno nel file `<nome del calendario> - Provvedimenti.xlsx`, che **non va dato** a chi inserisce i risultati.
  * **Excel**: il `RIEPILOGO` mostra i provvedimenti quando il file dei provvedimenti è **aperto insieme** al calendario (in qualunque cartella). Se rinomini il calendario, rinomina allo stesso modo il file dei provvedimenti, oppure scrivi il suo nome in `Campionato!H2`; il nome cercato si vede in `Campionato!H4`. Se il file manca, la colonna resta vuota senza errori e torna a riempirsi appena lo riapri.
  * **Google Sheets**: carica anche il file dei provvedimenti e salvalo come Foglio Google, scrivine il link in `Campionato!H3` e, la prima volta, clicca su "Consenti l'accesso" nella cella `A3` del foglio `Collegamento Provvedimenti`.
  * LibreOffice non legge questo collegamento: la colonna resta vuota.
* **Non fare**: non scrivere due righe con lo stesso numero di gara (viene letta solo la prima) e non rinominare i fogli `Note` e `Provvedimenti Disciplinari`.

---

## 9. Foglio `RIEPILOGO`

È l'**ultimo foglio** del file e contiene **una gara per riga**: numero, girone, giornata, fase, squadre, data, ora, campo, punti, esiti speciali (forfait), `FC` (squadra fuori classifica: `A`, `B` o `AB`), note e provvedimenti.

* È **di sola lettura**: serve per controllare, filtrare, stampare o copiare i dati altrove.
* Per usarlo fuori dal file: seleziona, copia e **incolla come valori** in un altro foglio, oppure salvalo in CSV.
* **Non scrivere** al suo interno e non ordinarlo "sul posto": copialo prima.

---

## 10. Foglio `Calendario.ics` – Calendario per smartphone e agende

1. Copia la **colonna `A`**, dalla prima riga (`BEGIN:VCALENDAR`) fino a quella con `END:VCALENDAR`.
2. Incollala in un editor di testo semplice (Blocco note, TextEdit in modalità testo, ecc.).
3. Salva il file con estensione **`.ics`** e codifica **UTF-8**, ed eliminate le eventuali virgolette aggiunte all'inizio e alla fine di ogni blocco.
4. Importalo in Google Calendar, Outlook o nel calendario del telefono.

Il titolo di ogni evento è breve (`G12: Squadra A vs Squadra B`); campionato, stagione e girone o turno sono nella descrizione. Se cambi date o campi, ripeti l'esportazione.

---

## 11. Foglio `MEMO` – Controllo

Con le ricerche per numero di gara, nel `MEMO` c'è una riga di controllo del tipo:

> Controllo: gare nei calendari 90, gare contate in classifica 90 - OK

Se compare **ATTENZIONE**, i due numeri non coincidono. Di solito significa che:

* due gare hanno lo **stesso numero** (sono rosse nel calendario);
* una gara aggiunta ha un **numero fuori dall'intervallo** indicato nel `MEMO`;
* una gara esistente è stata spostata in un **altro foglio calendario**, o in un foglio calendario creato a mano.

Correggi il numero e il controllo torna su OK.

---

## 12. Condivisione e pubblicazione

* Per pubblicare calendari e classifiche, carica il file su **Google Sheets** e condividilo **in sola lettura**.
* Il file contiene **dati personali** (nomi ed email di arbitri e Ufficiali di Campo, designazioni, note, provvedimenti): condividilo solo con chi deve usarlo. Per una pubblicazione aperta, condividi una copia senza quei fogli, oppure usa l'opzione dei provvedimenti in un file a parte.
* La riga del `MEMO` che cita il generatore è gradita ma si può togliere.

---

## 13. Quando rigenerare il file con il generatore

Alcune modifiche non si fanno a mano. Si caricano nel generatore il file attuale (e, se c'è, quello dei provvedimenti), si cambia quello che serve e si genera un file nuovo. **I dati già inseriti vengono conservati**: squadre, campi, gare, risultati, designazioni, note e provvedimenti.

Rigenera quando devi:

* aggiungere o togliere **gironi**, o **dividere** un girone (anche mantenendo un unico calendario);
* aggiungere **squadre** oltre i posti disponibili;
* cambiare **codici** squadra o campo;
* cambiare il **playoff** (numero di squadre, gironi qualificati, andata e ritorno, Torneo Primavera);
* aggiungere i fogli **Note**, **Provvedimenti** o **Designazioni**, o le righe di arbitri e Ufficiali di Campo;
* passare tra **ricerche** e **riferimenti fissi**.

---

## 14. Riepilogo: cosa NON fare

* ❌ Scrivere nomi di squadra al posto dei **codici** nei calendari.
* ❌ Scrivere risultati o date **come testo**.
* ❌ Scrivere in classifiche, `RIEPILOGO`, colonne **nascoste** o nel foglio nascosto `Dati`.
* ❌ Inserire, cancellare o riordinare righe nella tabella **squadre** di `Campionato`.
* ❌ Cambiare i **codici** squadra o campo, le sigle dei gironi (`D5`) o i nomi dei fogli.
* ❌ Cambiare il **numero di gara** di una gara esistente o usare lo stesso numero due volte.
* ❌ Con i **riferimenti fissi**: spostare, copiare o aggiungere gare a mano.
* ❌ Creare a mano nuovi fogli calendario o playoff.
* ❌ Scrivere nomi a mano nelle **designazioni** invece di usare l'elenco a discesa.

## Problemi frequenti

| Cosa vedo | Causa probabile | Cosa fare |
|---|---|---|
| Il nome della squadra non compare in una gara | Codice sbagliato o scritto il nome in `C`/`E` | Scrivi il codice esatto della tabella squadre |
| Una gara giocata non conta in classifica | Risultato scritto come testo, gara con squadra fuori classifica, numero di gara ripetuto o fuori intervallo, gara spostata in un altro foglio calendario | Controlla `J`/`L`, la colonna `FC` e la riga di controllo del `MEMO` |
| Numero di gara in rosso | Numero ripetuto nello stesso foglio | Dai alla gara un numero nuovo nell'intervallo del `MEMO` |
| La giornata di una gara nel `RIEPILOGO` è sbagliata | La gara è sotto la barra di un'altra giornata | Spostala sotto la barra giusta |
| Il campo non compare | Codice campo mancante o sbagliato nella riga sotto la gara | Scrivi il codice in colonna `I` della riga del campo |
| Il logo non si vede | Link non pubblico o non più valido, oppure versione di Excel senza `IMAGE` | Usa un link pubblico e stabile all'immagine |
| La colonna dei provvedimenti nel `RIEPILOGO` è vuota | File dei provvedimenti non aperto (Excel) o link mancante (Google Sheets) | Vedi il punto 8 |
| `#NOME?` nel foglio `Collegamento Provvedimenti` | Normale in Excel e LibreOffice: quel foglio serve solo a Google Sheets | Nessuna azione |
