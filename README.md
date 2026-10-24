# BlackBone AI
**DISCORD SERVER https://discord.gg/nRfSCHUA4**
**Coperture vocali con l'intelligenza artificiale, in locale.**
Separa la voce dalla canzone, la converte con il modello che scegli e la rimette
al posto con l'originale. Tutto gira sulla tua scheda video: niente account,
niente cloud, niente limiti di minuti.

- Versione attuale: **1.01-ALPHA** (build 2026.10)
- Sistema: Windows 10/11 (funziona anche su macchina virtuale con GPU pass-through)

---

## Come si installa

1. Apri la pagina delle [release](https://github.com/angelosiglioccolo817-cmyk/BlackBone-Ai-cover/releases).
2. Scarica **`BlackBoneAI-Installer.exe`** (circa 10 MB).
3. Doppio clic. L'installer fa tutto lui.

L'installer è **leggero di proposito**: porta solo il codice dell'app.
Sul tuo computer vengono scaricati solo quando servono:

| Cosa | Quando |
|---|---|
| Python 3.10 + ambiente virtuale | se non c'e' gia' un Python adatto |
| PyTorch con la build CUDA giusta | in base alla scheda video che trova |
| Modelli base (hubert, rmvpe, campplus) | circa 400 MB, una volta sola |
| ffmpeg | facoltativo, serve per l'export in MP3 |

La build di PyTorch viene scelta da sola:

| Scheda video | PyTorch | CUDA |
|---|---|---|
| Serie 50 (RTX 5050/5080/5090) | 2.7.0 | 12.8 |
| Serie 40 e 30 (RTX 3060-4090) | 2.6.0 | 12.4 |
| Serie 20, GTX 16xx e 10xx | 2.5.1 | 12.1 |
| Nessuna GPU NVIDIA | 2.6.0 | solo CPU |

L'app si installa in `%LOCALAPPDATA%\BlackBoneAI` e crea il collegamento sul
desktop e nel menu Start. Per disinstallarla: **Disinstalla BlackBone AI.cmd**
nella cartella di installazione.

---

## Aggiornamenti automatici

L'app controlla da sola, ogni tanto, se e' uscita una versione nuova su
GitHub. Quando la trova ti chiede:

> *Vuoi installare l'aggiornamento?*

Se dici si' succede questo, senza che tu debba toccare nulla:

1. l'app scarica l'installer della versione nuova;
2. l'app si chiude;
3. l'installer sostituisce i file dell'app **senza toccare** le tue voci, le
   canzoni gia' convertite, la cronologia e la licenza;
4. l'app si riapre.

Niente pacchetti da scaricare a mano, niente reinstallazione: il passaggio e'
sempre l'installer.

---

## Livelli di licenza

Il livello e' scritto dentro la chiave firmata: non si puo' cambiare a mano.

| | Standard | Studio | Pro |
|---|---|---|---|
| Formati di export | WAV | WAV + MP3 | WAV + MP3 |
| Voci (modelli) contemporanee | 3 | 10 | 19 |
| Lavori in coda | 1 | 3 | senza limite |
| Allenamento della voce | - | si' | si' |
| Copertina dentro il file esportato | si' | si' | si' |

La chiave resta valida anche offline: l'app controlla la lista delle licenze
revocate quando c'e' rete e continua a funzionare anche senza.

---

## Cosa c'e' dentro

- separazione voce/strumentale con Demucs;
- conversione con RVC v2 o Seed-VC (zero-shot);
- mix con loudness match e volume originale sotto la cover;
- copertina generata per ogni brano e salvata dentro WAV, MP3 e FLAC;
- interfaccia che si organizza come vuoi (riordini i blocchi, li allarghi o li
  nascondi: la scelta resta anche chiudendo l'app);
- interfaccia anche dal telefono, sulla rete locale, con codice di accesso.

---

## Domande frequenti

**Serve una connessione internet?** Serve solo per l'installazione (Python,
PyTorch, modelli) e per gli aggiornamenti. Una volta installata l'app lavora
in locale.

**Dove finiscono le mie canzoni?** Nella cartella di installazione, in
`backend\storage\`. Nulla esce dal tuo computer.

**Posso usare le voci che alleno qui su un altro computer?** Ogni voce e' un
modello RVC: basta copiare la cartella del modello.

---

**Dove posso trovare la licenza?**
Basta scrivermi su discord nome:sharp_s_s per la licenza base gratis!


---

## Licenza

Il codice e' rilasciato con licenza **GPL-3.0** (vedi il file `LICENSE`).
I modelli di terze parti scaricati durante l'installazione (RVC, Seed-VC,
Demucs) hanno le rispettive licenze dei loro progetti.
