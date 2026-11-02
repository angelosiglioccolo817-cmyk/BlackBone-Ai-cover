# BlackBone VoiceCover
Cover vocali con l'intelligenza artificiale, tutto in locale sul tuo PC.

## Cosa fa

- Genera cover vocali usando modelli AI (RVC, Seed-VC, Demucs per separazione voce/strumentale)
- Server FastAPI locale con interfaccia desktop nativa (WebView2)
- Sistema licenze (Standard, Studio, Pro) con livelli di accesso differenti
- Esportazione in WAV, MP3, FLAC in base al livello di licenza

## Come installare (senza exe â€” nessun falso positivo antivirus)

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

La licenza Ã¨ firmata digitalmente (Ed25519) e cifrata con DPAPI di Windows: non si puÃ² copiare su un altro computer nÃ© modificare.

## Requisiti

- Windows 10 o 11
- Python 3.10 (python.org)
- Circa 10 GB di spazio libero
- Connessione internet per l'installazione iniziale (PyTorch e dipendenze)

## File nella release

| File | Descrizione |
|------|-------------|
| BlackBoneVoiceCoverAI-Installer.exe | Installer .exe (puÃ² essere segnalato come falso positivo da Windows Defender â€” non Ã¨ firmato) |
| BlackBoneVoiceCoverAI-Source.zip | Codice sorgente completo, nessun exe, nessun problema antivirus |

## Supporto

Per chiavi di licenza, problemi o supporto: apri una Issue su questo repository.

---
Sviluppato da BlackBone AI â€” tutto in locale, niente cloud.

# BlackBone Video AI

Applicazione desktop locale per la generazione video tramite l'API Python documentata di WanGP.

## Architettura

- **Backend**: Flask (Python 3.10+ di sistema) con interfaccia desktop PyWebView
- **Frontend**: HTML/CSS/JavaScript ospitato in finestra dedicata
- **Adapter WanGP**: `wan_adapter.py` eseguito come subprocesso con l'ambiente Python dedicato di WanGP (es. `Wan2GP/env_venv/`, contenente PyTorch e `shared/api.py`)
- **Comunicazione**: subprocesso locale tramite file JSON, non via rete HTTP

## Caratteristiche

- Interfaccia Genera video, Coda, Modelli e Impostazioni
- Coda lavori con rilevamento video completati e deduplicazione
- Text-to-Video, Image-to-Video, Video-to-Video, Continua video
- Rilevamento automatico e manuale di installazioni WanGP (inclusi percorsi Pinokio)
- Verifica PyTorch/CUDA nell'ambiente Python di WanGP
- Download modelli dal catalogo WanGP tramite downloader ufficiale
- Gestione avanzata di output, lavori concorrenti, risoluzione, FPS, seed
- Salvataggio automatico delle impostazioni backend su `config.json`
- Preferenze UI salvate in `localStorage` del browser

## Requisiti

- Python 3.10+ installato da python.org (alias Microsoft Store non supportati)
- Runtime Microsoft Edge WebView2 (Windows)
- Per WanGP: un'installazione WanGP con `shared/api.py` e un ambiente Python dedicato contenente PyTorch/CUDA

## Avvio rapido

```powershell
# 1. Installa le dipendenze dell'interfaccia
python -m pip install -r requirements.txt

# 2. Avvia l'app
python desktop_app.py
```

Oppure usa `start_windows.bat` su Windows.

## Configurazione WanGP

Prima di tutto crea un **.venv** nella cartella di **Wan2GP** se non ci sta già facendo:

```powershell
# 1. cd nella cartella di wan2gp es.
cd /d D:\Wan2GP 
# oppure
cd C:\Wan2GP 

# 2. Crea il venv
scripts\install.bat
```

1. Apri **Impostazioni**
2. Indica la cartella contenente `wgp.py` o `gradio_server.py` (es. `C:\Percorso\Wan2GP`)
3. Clicca **Verifica installazione** o **Rileva WanGP automaticamente**
4. In **Modelli**, clicca **Verifica e rileva modelli**

L'adapter cerca automaticamente l'ambiente Python dentro la cartella WanGP (`.venv`, `venv`, `env_venv`, ecc.) prima di fare fallback a Python di sistema.

## Riferimento API WanGP

L'adapter usa `shared.api` (documentato su [WanGP API docs](https://github.com/deepbeepmeep/WanGP/blob/main/docs/API.md)) con `init(...)`, `get_default_settings(...)` e `submit_task(...)`.

## Note

- WanGP carica modello e pesi in VRAM: un solo lavoro alla volta con motore `wan2gp`
- BlackBone non scarica né installa automaticamente componenti ML/PyTorch
- Non esporre il server Flask su Internet senza autenticazione
