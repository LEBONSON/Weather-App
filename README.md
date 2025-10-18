# Weather App

**Description courte :**
Une application météo simple construite en JavaScript (vanilla) qui affiche la météo actuelle et la prévision à partir d'une API publique (par ex. OpenWeatherMap). L'objectif : démontrer comment consommer une API, utiliser la géolocalisation du navigateur, et afficher les données proprement.

---

## 🚀 Fonctionnalités

* Recherche de la météo par ville
* Détection automatique de la position (API Geolocation)
* Affichage : température, description, humidité, vitesse du vent, icône météo
* Option : basculer entre °C et °F
* Gestion des erreurs (ville non trouvée, refus de géolocalisation, réseau)

---

## 🛠️ Technologies utilisées

* HTML5
* CSS3 (Flexbox / Grid) — style minimal
* JavaScript (ES6+) — Fetch API, async/await
* API météo : OpenWeatherMap (ou autre API similaire)

---

## Prérequis

1. Node.js (optionnel, seulement si vous voulez lancer un serveur local ou builder)
2. Clé API OpenWeatherMap (inscription gratuite) — voir plus bas

---

## Installation et exécution (local)

1. Clonez le dépôt :

```bash
git clone https://github.com/<votre-utilisateur>/weather-app.git
cd weather-app
```

2. Ouvrez `index.html` dans votre navigateur (double‑clic) ou servez via un petit serveur local :

```bash
# avec Python 3
python -m http.server 3000
# ouvrez http://localhost:3000
```

3. Ajoutez votre clé API dans le fichier `config.js` (ou dans `.env` si vous utilisez bundler) :

```js
// config.js
export const API_KEY = 'VOTRE_CLE_API_ICI';
```

---

## Utilisation

* Tapez le nom d'une ville et appuyez sur Entrée ou cliquez sur Rechercher.
* Autorisez la géolocalisation pour obtenir la météo locale.
* Cliquez sur l'icône °C/°F pour changer l'unité.

---

## Structure du projet (exemple)

```
weather-app/
├─ index.html
├─ styles.css
├─ app.js
├─ config.js         # contient API_KEY (ne pas push publique)
├─ images/
│  └─ icons/
└─ README.md
```

---

## Exemple de code essentiel (extrait)

> Le fichier complet est dans le repo. Ici un extrait pour expliquer le flux :

```js
// app.js
import { API_KEY } from './config.js';

async function getWeatherByCity(city) {
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${encodeURIComponent(city)}&appid=${API_KEY}&units=metric&lang=fr`;
  const res = await fetch(url);
  if (!res.ok) throw new Error('Ville non trouvée');
  return await res.json();
}

async function renderCityWeather(city) {
  try {
    const data = await getWeatherByCity(city);
    // mettre à jour le DOM : temperature, description, icone...
  } catch (err) {
    // afficher erreur
  }
}
```

---

## Obtenir une clé API (OpenWeatherMap)

1. Allez sur [https://openweathermap.org/](https://openweathermap.org/)
2. Créez un compte gratuit
3. Générez une clé API dans votre tableau de bord
4. Placez la clé dans `config.js` ou dans une variable d'environnement

> **Sécurité :** Ne poussez jamais votre clé API publique sur un repo public. Utilisez `.gitignore` pour exclure `config.js` ou stockez la clé côté serveur.

---

## Bonnes pratiques

* Gérer les erreurs et afficher des messages clairs à l'utilisateur
* Limiter le nombre d'appels API (debounce sur l'input, caches simples)
* Ajouter des tests simples si vous utilisez un bundler / framework
* Prévoir l'accessibilité (labels, contrastes, focus)

---

## Déploiement

* Hébergez sur GitHub Pages, Netlify, Vercel ou tout hébergeur static.
* Si vous utilisez des variables sensibles, utilisez les variables d'environnement du service (Netlify / Vercel).

---

## Contribution

PR bienvenues ! Pour contribuer :

1. Fork le repo
2. Créez une branche feature: `git checkout -b feature/ma-fonctionnalite`
3. Commit et PR

---

## Licence

MIT

---

## Ressources & lectures complémentaires

* Documentation OpenWeatherMap: [https://openweathermap.org/api](https://openweathermap.org/api)
* MDN Fetch API: [https://developer.mozilla.org/](https://developer.mozilla.org/)

---

*README généré automatiquement par votre assistant. Vous pouvez personnaliser les textes, ajouter des captures d'écran et un GIF de démo.*
