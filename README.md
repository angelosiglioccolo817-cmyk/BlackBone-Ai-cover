# BlackBone VoiceCover AI 3.02 ALPHA

Cover vocali con l'intelligenza artificiale, tutto in locale sul tuo PC.

## Cosa fa

- Genera cover vocali usando modelli AI (RVC, Seed-VC, Demucs per separazione voce/strumentale)
- Server FastAPI locale con interfaccia desktop nativa (WebView2)
- Sistema licenze (Standard, Studio, Pro) con livelli di accesso differenti
- Esportazione in WAV, MP3, FLAC in base al livello di licenza

## Come installare (senza exe — nessun falso positivo antivirus)

1. Scarica e estrai BlackBoneVoiceCoverAI-Source.zip dalla [Release v3.02-ALPHA](https://github.com/angelosiglioccolo817-cmyk/BlackBone-Ai-cover/releases/tag/CoverAI-v3.02-ALPHA)
2. Installa Python 3.10 da [python.org](https://python.org) (non Microsoft Store)
3. Apri PowerShell nella cartella estratta
4. Esegui:

   `powershell
   python installer.py
   `

   Oppure avvia direttamente il server:

   `powershell
   cd setup\backend
   python app.py
   `

## Sistema licenze

Durante l'installazione ti viene richiesta una chiave di licenza obbligatoria. Senza chiave valida l'installazione non procede.

Livelli disponibili:
- **Standard**: 3 modelli, solo WAV, 1 canzone alla volta
- **Studio**: 10 modelli, WAV e MP3, allenamento, 3 canzoni alla volta
- **Pro**: tutto, formati WAV/MP3/FLAC, coda illimitata

La licenza è firmata digitalmente (Ed25519) e cifrata con DPAPI di Windows: non si può copiare su un altro computer né modificare.

## Requisiti

- Windows 10 o 11
- Python 3.10 (python.org)
- Circa 4 GB di spazio libero
- Connessione internet per l'installazione iniziale (PyTorch e dipendenze)

## File nella release

| File | Descrizione |
|------|-------------|
| BlackBoneVoiceCoverAI-Installer.exe | Installer .exe (può essere segnalato come falso positivo da Windows Defender — non è firmato) |
| BlackBoneVoiceCoverAI-Source.zip | Codice sorgente completo, nessun exe, nessun problema antivirus |

## Supporto

Per chiavi di licenza, problemi o supporto: apri una Issue su questo repository.

---
Sviluppato da BlackBone AI — tutto in locale, niente cloud.