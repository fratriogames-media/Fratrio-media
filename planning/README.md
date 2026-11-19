# Planning de publication Instagram — @quiestleplusfrance

## Rythme (jusqu'au 24 décembre 2026)
Minimum par semaine : **4 posts + 5 stories**.

## Fonctionnement
1. **Le dimanche** : préparation de la semaine avec Tom (visuels + légendes), puis validation.
2. Les visuels validés sont déposés dans `AAAA-MM-JJ/` (JPEG, post 1080×1080 ou 1080×1350, story 1080×1920).
3. Le planning de la semaine est écrit dans `planning/AAAA-Sxx.json`, avec `"valide": true` une fois que Tom a dit « go ».
4. Une tâche planifiée tourne chaque jour (vers 11h45 et 18h15, heure de Paris) : elle publie via Windsor.ai chaque publication validée dont l'heure est passée, puis la marque `"publie"` avec son `media_id`.

Rien n'est publié si `"valide"` vaut `false`.

## Format d'un fichier de semaine
```json
{
  "semaine": "2026-S48",
  "du": "2026-11-23",
  "au": "2026-11-29",
  "valide": false,
  "publications": [
    {
      "id": "s48-01",
      "type": "post",
      "date": "2026-11-23T12:00",
      "image": "2026-11-23/post-exemple.jpg",
      "legende": "Texte du post, hashtags compris",
      "statut": "a_publier",
      "media_id": null
    },
    {
      "id": "s48-02",
      "type": "story",
      "date": "2026-11-23T18:30",
      "image": "2026-11-23/story-exemple.jpg",
      "legende": null,
      "statut": "a_publier",
      "media_id": null
    }
  ]
}
```

- `type` : `post` ou `story` (une story n'a pas de légende).
- `date` : heure de Paris, au plus tôt à laquelle publier.
- `statut` : `a_publier`, `publie` ou `erreur` (avec un champ `erreur` qui explique).
- URL publique d'une image : `https://raw.githubusercontent.com/fratriogames-media/fratrio-media/main/<image>`

## Limites connues
- Les stories publiées par l'API n'ont ni mention, ni sondage, ni lien : à ajouter à la main dans l'appli si besoin.
- Compte Instagram (Windsor.ai) : `17841475482921653`.
