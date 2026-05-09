# User Prompt — Modèle 2

> À coller dans le champ **User** du nœud "Message a model - réponse" dans n8n.
> Les variables entre `{{ }}` sont injectées automatiquement par n8n depuis le nœud précédent.

---

Métier : {{ $json.metier }}
Type de demande : {{ $json.type_demande }}

Prompt à exécuter :
{{ $json.prompt_optimise }}

Contenu source (si disponible) :
{{ $json.demande_initiale.contenu_source }}

Produis le livrable métier final directement, sans introduction.
