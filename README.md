# Coach de Prompting IA
Outil pédagogique d'analyse et d'amélioration de prompts pour les équipes métier : diagnostique une demande utilisateur, identifie ses lacunes, et génère un prompt structuré et directement exploitable dans n'importe quel outil d'IA générative.

## Objectif
Accompagner les collaborateurs dans l'apprentissage du prompt engineering en transformant une demande floue en prompt optimisé, tout en expliquant les erreurs commises et les règles à retenir — pour développer l'autonomie et réduire le temps de formulation de plus de 70%.

## Stack technique

| Outil | Usage |
|---|---|
| n8n | Orchestration du workflow complet |
| OpenAI GPT | Diagnostic, coaching et génération du prompt optimisé |
| Webhook n8n | Communication entre le formulaire et le workflow |
| HTML / CSS / JS | Interface utilisateur (fichier unique, sans framework) |

## Architecture du pipeline

```
Formulaire HTML (saisie utilisateur)
        ↓
  Webhook n8n (GET)
        ↓
  Message a model — OpenAI GPT
  (Diagnostic + Coaching + Prompt optimisé)
        ↓
  Parse Prompt JSON (nœud Code)
        ↓
  Nœud If (routing succès / fallback)
        ↓
        ├──────────────────────────┐
        ↓                         ↓
  BRANCHE SUCCÈS           BRANCHE FALLBACK
  Message a model          Fallback JSON invalide
  (Livrable métier)
        ↓
  Code function (extraction livrable)
        ↓
  Code JavaScript final (formatage réponse complète)
        ↓
  Respond to Webhook → Affichage HTML
```

## Fonctionnalités clés

**Diagnostic intelligent**
L'agent évalue automatiquement la qualité de la demande initiale : niveau de clarté (faible / moyen / élevé), score sur 10, type de tâche détecté et stratégie recommandée pour améliorer la demande.

**Identification des lacunes et des risques**
Le système détecte les informations manquantes et les risques concrets liés à une demande trop vague — par exemple, une offre d'emploi peu attractive ou une analyse de CV non ciblée.

**Aide à la reformulation**
Trois leviers d'aide sont proposés simultanément : suggestions concrètes, questions à compléter, et template vierge adapté au type de demande et au pôle métier.

**Coaching personnalisé**
L'agent détecte le niveau de l'utilisateur (débutant / intermédiaire / avancé), identifie son erreur principale et formule une règle universelle à retenir — pour que chaque session soit une leçon, pas juste un résultat.

**Prompt optimisé téléchargeable**
La demande initiale est transformée en prompt structuré, clair et réutilisable, directement exploitable dans ChatGPT, Claude ou tout autre LLM. Exportable en .txt en un clic.

**Adapté aux métiers**
L'analyse et le ton sont adaptés automatiquement au pôle métier sélectionné : RH, Commerce, Opérations ou Communication.

## Résultats
- Temps de formulation d'un prompt réduit de plus de 70%
- Prompt exploitable généré en moins de 15 secondes
- Compréhension des erreurs de formulation dès la première utilisation
- Applicable à tous les cas d'usage métier sans configuration supplémentaire

## Contenu du repository

```
coach-prompting-ia/
│
├── index.html                    # Interface utilisateur complète
│
├── prompts/
│   ├── system_prompt_model1.md   # System prompt — diagnostic et coaching
│   ├── user_prompt_model1.md     # User prompt — modèle 1
│   ├── system_prompt_model2.md   # System prompt — génération du livrable
│   └── user_prompt_model2.md     # User prompt — modèle 2
│
└── README.md
```

## Ce que ce projet m'a appris
- Concevoir un agent IA à visée pédagogique, pas seulement productiviste
- Structurer un system prompt complexe pour obtenir un JSON enrichi et cohérent
- Gérer la robustesse d'un pipeline face aux erreurs de parsing JSON (guillemets non échappés, fallback, réparation automatique)
- Intégrer une logique de routing conditionnel dans n8n (nœud If + branches parallèles)
- Adapter dynamiquement le ton et le contenu d'une réponse IA selon le profil utilisateur détecté
