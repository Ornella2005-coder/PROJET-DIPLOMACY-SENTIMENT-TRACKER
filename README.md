# 🇫🇷 Diplomacy Sentiment Tracker — 60 ans de discours politiques français

Analyse textuelle d'environ **110 000 discours publics français (1958-2022)** pour comprendre comment le **ton**, les **thématiques** et le **vocabulaire** de la parole politique ont évolué avec les priorités du pays.

![Python](https://img.shields.io/badge/Python-3.11-blue)
![pandas](https://img.shields.io/badge/pandas-analyse-150458)
![TextBlob-fr](https://img.shields.io/badge/TextBlob--fr-sentiment-green)
![NLTK](https://img.shields.io/badge/NLTK-NLP-orange)

---

## 🎯 Problématique

> **Comment les discours politiques français de 1958 à 2022 traduisent-ils l'évolution des priorités économiques, sociales et diplomatiques du pays à travers le ton, les thématiques et le vocabulaire employé ?**

L'étude s'organise en trois axes :

| Axe | Question | Méthode |
|---|---|---|
| **1. Thématiques** | De quoi parle-t-on à chaque période ? Quelle place pour l'international selon les présidences ? | Fréquence des thématiques, en % des discours |
| **2. Ton** | Le ton est-il plus positif ou négatif selon les années, les présidents, les crises, les fonctions ? | Analyse de sentiment (TextBlob-fr) : polarité et subjectivité |
| **3. Vocabulaire** | Les discours sont-ils plus techniques ou plus émotionnels ? Quels mots émergent ? | Fréquences de mots, nuages de mots, mots émergents |

---

## 📊 Données

| | |
|---|---|
| **Volume** | ~110 000 discours avec texte (≈95 000 textes intégraux) |
| **Période** | 1958 → 2022 |
| **Champs** | titre, orateurs et fonctions, thématiques, mots-clés, date, type, texte |
| **Types** | interviews, déclarations, conférences de presse, communiqués… |

⚠️ La répartition dans le temps est très inégale : quelques discours par an avant les années 1980, plus de 2 000 par an à la fin des années 2010. Les analyses raisonnent donc en **proportions**, et les résultats des premières décennies sont à lire avec prudence.

Le fichier de données n'est pas versionné (trop volumineux) : voir [`data/README.md`](data/README.md).

---

## 🔍 Principaux enseignements

- **Trois thèmes structurent la parole politique** : *Société* (~32 000 mentions), *International* (~27 000) et *Institutions* (~24 000). L'État s'adresse à sa société, se positionne dans le monde et parle de son fonctionnement.
- **Les crises redessinent les priorités** : la pandémie de COVID-19 fait émerger des thématiques (*Santé*, *Epidémie*) quasi absentes des autres périodes.
- **Un ton globalement mesuré** : les discours officiels ne sont ni euphoriques ni alarmistes. Les écarts entre présidents ou entre fonctions sont faibles.

---

## 🧪 Méthode

1. **Nettoyage** : suppression des discours sans texte et des doublons, conservation des seuls *textes intégraux*, année tirée de la date du discours.
2. **Variables d'analyse** : fonction de l'orateur, président qui s'exprime, présidence en exercice à la date du discours.
3. **Thématiques** : part des discours abordant chaque thème, par décennie, par crise et par présidence.
4. **Ton** : polarité (-1 négatif → +1 positif) et subjectivité (0 factuel → 1 émotionnel) calculées avec **TextBlob-fr**. Les années comptant moins de 20 discours sont exclues des courbes.
5. **Vocabulaire** : mots techniques pour 1 000 mots, nuages de mots par président, mots dont la fréquence augmente le plus après 2000.

---

## 📁 Structure du projet

```
PROJET-DIPLOMACY-SENTIMENT-TRACKER/
├── README.md
├── requirements.txt
├── notebooks/
│   └── diplomacy_sentiment_tracker.ipynb   ← analyse complète, commentée pas à pas
└── data/
    └── README.md                           ← où placer speechs_data.json
```

---

## ▶️ Lancer le projet

```bash
# 1. Cloner le dépôt
git clone https://github.com/Ornella2005-coder/PROJET-DIPLOMACY-SENTIMENT-TRACKER.git
cd PROJET-DIPLOMACY-SENTIMENT-TRACKER

# 2. Installer les librairies
pip install -r requirements.txt

# 3. Placer speechs_data.json dans le dossier data/

# 4. Ouvrir le notebook et tout exécuter (Kernel > Restart & Run All)
jupyter notebook notebooks/diplomacy_sentiment_tracker.ipynb
```

⏱️ L'analyse de sentiment sur ~95 000 textes peut prendre plusieurs dizaines de minutes. Pour un test rapide, une ligne du notebook permet de travailler sur un échantillon.

---

## ⚠️ Limites

- **Couverture inégale** : très peu de discours avant les années 1980.
- **Sentiment par dictionnaire** : TextBlob-fr ne comprend ni l'ironie, ni le contexte, ni les nuances diplomatiques.
- **Thématiques imposées** : elles proviennent de l'indexation de la source, pas d'une analyse automatique du texte.
- **Interviews** : le texte inclut les questions des journalistes.

## 🚀 Pistes d'amélioration

- Modèle de langue français plus performant (CamemBERT) pour le sentiment.
- Modélisation de sujets (BERTopic) pour découvrir des thèmes sans dépendre de l'indexation.
- Isoler les seules réponses de l'orateur dans les interviews.
