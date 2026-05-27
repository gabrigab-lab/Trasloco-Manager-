# 📦 Trasloco Manager — Guida al Deploy

## Cosa ottieni
- Web app accessibile da qualsiasi dispositivo con un link
- Installabile su iPhone come app (senza App Store)
- Dati e foto sincronizzati in tempo reale su tutti i dispositivi
- Hosting gratuito su Netlify + database Firebase gratuito

---

## PARTE 1 — Firebase (database + storage foto)

### 1.1 Crea il progetto Firebase
1. Vai su https://firebase.google.com e accedi con Google
2. Clicca **"Crea un progetto"**
3. Nome progetto: `trasloco-app` → Avanti
4. Disattiva Google Analytics → **Crea progetto**
5. Aspetta il completamento, poi clicca **Continua**

### 1.2 Crea il database Firestore
1. Nel menu laterale sinistro: **Firestore Database**
2. Clicca **"Crea database"**
3. Scegli **"Inizia in modalità test"** → Avanti
4. Location: **europe-west** → Abilita
5. Aspetta la creazione (30 secondi)

### 1.3 Abilita Storage (per le foto)
1. Nel menu laterale: **Storage**
2. Clicca **"Inizia"**
3. **"Modalità test"** → Avanti
4. Location: **europe-west** → Fatto

### 1.4 Ottieni le credenziali
1. Clicca l'icona ⚙️ in alto a sinistra → **Impostazioni progetto**
2. Scorri in basso fino a **"Le tue app"**
3. Clicca l'icona **</>** (web app)
4. Nickname: `trasloco-web` → **Registra app**
5. Vedrai un blocco `firebaseConfig` con tutti i valori — tienilo aperto

---

## PARTE 2 — Netlify (hosting gratuito)

### 2.1 Pubblica i file
1. Vai su https://netlify.com → **Sign up** con GitHub o email
2. Nella dashboard, clicca **"Add new site"** → **"Deploy manually"**
3. Trascina la cartella `trasloco-app` nell'area di drop
4. In 30 secondi il sito è online con un URL tipo: `https://nome-casuale.netlify.app`

### 2.2 (Opzionale) URL personalizzato
1. Site settings → **Change site name**
2. Cambia in qualcosa come `trasloco-mio` → il link diventa `https://trasloco-mio.netlify.app`

---

## PARTE 3 — Prima apertura dell'app

1. Apri il link su iPhone (Safari)
2. L'app mostra una schermata di configurazione con i campi per Firebase
3. Inserisci i valori dal `firebaseConfig` copiato al passo 1.4
4. Clicca **"Salva e connetti"**
5. L'app si connette e carica le stanze predefinite ✅

> La configurazione viene salvata sul dispositivo: non devi reinserirla ogni volta.
> Su ogni nuovo dispositivo, ripeti il passo 3 una sola volta.

---

## PARTE 4 — Installa su iPhone (come app nativa)

1. Apri il link in **Safari** (non Chrome!)
2. Tocca il pulsante **Condividi** (□↑)
3. Scorri e tocca **"Aggiungi a Home"**
4. Conferma con **Aggiungi**
5. L'icona appare nella home screen — si apre a schermo intero come un'app vera ✅

---

## Note tecniche

- **Firestore piano gratuito (Spark)**: 50.000 letture/giorno, 20.000 scritture/giorno — più che sufficiente per uso personale
- **Storage gratuito**: 5 GB — abbondante per le foto del trasloco
- Le foto vengono caricate su Firebase Storage e accessibili da tutti i dispositivi
- I dati si aggiornano in tempo reale: se aggiorni da iPhone, vedi subito le modifiche su PC

---

## Sicurezza (dopo il trasloco)

Le regole Firebase in "modalità test" scadono dopo 30 giorni. Per estenderle:
1. Firestore → **Regole** → cambia la data di scadenza
2. Storage → **Regole** → stessa cosa

Per bloccare l'accesso solo a te, puoi aggiungere autenticazione Firebase in futuro.
