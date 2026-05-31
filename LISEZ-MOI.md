# FORGE PWA — Instructions d'installation iOS

## Fichiers dans ce dossier
- `index.html` — L'app complète (modifiée pour PWA)
- `manifest.json` — Déclaration PWA pour Safari
- `sw.js` — Service Worker (cache offline)
- `icon-192.png` — Icône app
- `icon-512.png` — Icône app HD
- `LISEZ-MOI.md` — Ce fichier

---

## ÉTAPE 1 — Mettre en ligne sur GitHub Pages (5 min, gratuit)

### 1.1 Créer un compte GitHub (si pas déjà fait)
→ https://github.com/signup

### 1.2 Créer un nouveau repository
1. Va sur https://github.com/new
2. Repository name : `forge-app` (ou ce que tu veux)
3. Coche **Public** (obligatoire pour GitHub Pages gratuit)
4. Clique **Create repository**

### 1.3 Upload les fichiers
1. Clique **uploading an existing file**
2. Glisse-dépose ces 5 fichiers :
   - index.html
   - manifest.json
   - sw.js
   - icon-192.png
   - icon-512.png
3. Clique **Commit changes**

### 1.4 Activer GitHub Pages
1. Va dans **Settings** (onglet du repo)
2. Clique **Pages** dans le menu gauche
3. Source : **Deploy from a branch**
4. Branch : **main** / **(root)**
5. Clique **Save**

### 1.5 Ton URL (attends 2 min)
```
https://TON-USERNAME.github.io/forge-app/
```
⚠️ Important : note bien cette URL avec le `/` final

---

## ÉTAPE 2 — Mettre à jour le Service Worker avec ta vraie URL

Ouvre `sw.js` et remplace la ligne :
```js
const ASSETS = ['/', '/index.html'];
```
Par :
```js
const ASSETS = [
  '/forge-app/',
  '/forge-app/index.html',
  '/forge-app/manifest.json',
  '/forge-app/icon-192.png',
  '/forge-app/sw.js'
];
```
(remplace `forge-app` par le nom exact de ton repo)

Re-upload `sw.js` sur GitHub.

---

## ÉTAPE 3 — Installer l'app sur iPhone

1. Ouvre **Safari** sur ton iPhone 14
2. Va sur ton URL GitHub Pages
3. Attends que la page charge complètement
4. Appuie sur le bouton **Partager** (carré avec flèche vers le haut) en bas
5. Fais défiler → **Sur l'écran d'accueil**
6. Nomme l'app **FORGE** → **Ajouter**

✅ L'icône FORGE apparaît sur ton écran d'accueil.
✅ Elle s'ouvre en plein écran sans barre Safari.
✅ Elle fonctionne OFFLINE (coupe le WiFi pour tester).
✅ Toutes tes données sont sauvegardées en local (localStorage).

---

## FAQ

**Est-ce que mes données sont sauvegardées ?**
Oui, tout est en localStorage sur ton iPhone. Tant que tu ne vides pas Safari, tes données restent.

**Est-ce que ça se déconnecte ?**
Non. Contrairement à Netlify, GitHub Pages est permanent. Pas de reconnexion.

**Comment faire une sauvegarde de mes données ?**
Dans l'app → Progrès → "EXPORTER MES DONNÉES" → fichier JSON sauvegardé dans Fichiers.

**Comment mettre à jour l'app ?**
Re-upload le nouveau `index.html` sur GitHub. L'app se met à jour automatiquement au prochain WiFi.

**Safari bloque quelque chose ?**
Assure-toi d'ouvrir l'URL avec Safari (pas Chrome). Seul Safari supporte "Sur l'écran d'accueil" sur iOS.

---

## ALTERNATIVE si GitHub Pages est trop compliqué

### Option B — Serve local sur Mac
Si tu as un Mac sur le même WiFi :
```bash
cd dossier-forge
python3 -m http.server 8080
```
Puis sur iPhone Safari : `http://IP-MAC:8080`
→ Installe en PWA → fonctionne offline après installation.

### Option C — Cloudflare Pages
1. Va sur https://pages.cloudflare.com
2. Upload le dossier
3. URL permanente gratuite
Plus rapide que GitHub Pages pour les mises à jour.
