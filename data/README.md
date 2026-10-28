# Données

Le fichier `speechs_data.json` (≈110 000 discours) est **trop volumineux pour GitHub** : il n'est pas inclus dans ce dépôt.

Pour exécuter le notebook, placez-le ici :

```
data/
└── speechs_data.json
```

Structure attendue :

```json
{
  "speechs": [
    {
      "title": "Interview de M. ..., ministre ...",
      "speakers": [{"name": "Nom Prénom", "function": "Fonction"}],
      "context": null,
      "keywords": ["Mot-clé 1", "Mot-clé 2"],
      "thematics": ["Société", "International"],
      "datetime": "2021-11-03T12:00:00Z",
      "readtime": "18 minutes",
      "kind": "Texte intégral",
      "text": "Texte du discours..."
    }
  ]
}
```
