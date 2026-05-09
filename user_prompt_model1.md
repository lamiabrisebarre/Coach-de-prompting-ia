# User Prompt — Modèle 1

> À coller dans le champ **User** du nœud "Message a model" dans n8n.
> Les variables entre `{{ }}` sont injectées automatiquement par n8n depuis le webhook.

---

Métier : {{ $json.query.metier }}
Type de demande : {{ $json.query.type_demande }}
Objectif : {{ $json.query.objectif }}
Contexte : {{ $json.query.contexte }}
Contenu source : {{ $json.query.contenu_source }}
Prompt de départ : {{ $json.query.prompt_depart }}

RAPPEL CRITIQUE : Ta réponse JSON doit OBLIGATOIREMENT contenir ces champs sans exception :
- "coach_ia" avec "regle_universelle" : la règle universelle à retenir en une phrase
- "prompt_optimise" : le prompt structuré et directement exploitable
- "aide_utilisateur" : suggestions, questions, template

Si ces champs sont absents, la réponse est invalide.
