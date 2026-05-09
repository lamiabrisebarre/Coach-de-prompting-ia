# 🧠 Coach de Prompting IA
> Outil de diagnostic et d'amélioration de prompts pour les équipes métier — construit avec n8n, OpenAI et une interface HTML sur-mesure.

---

## 🎯 Concept

Le **Coach de Prompting** est un agent IA pédagogique conçu pour aider les collaborateurs à mieux formuler leurs demandes aux outils d'intelligence artificielle.

Il ne se contente pas de générer un prompt amélioré : il **explique pourquoi** la demande initiale était insuffisante, identifie les risques, et donne une règle universelle à retenir pour progresser en autonomie.

---

## ✨ Fonctionnalités

| Module | Description |
|---|---|
| 🔍 **Diagnostic** | Score de clarté, type de tâche détecté, stratégie recommandée |
| ⚠️ **Éléments à préciser** | Informations manquantes + risques identifiés |
| 💬 **Aide à la reformulation** | Suggestions, questions à compléter, template vierge |
| 🎓 **Conseil de cadrage** | Niveau utilisateur détecté, erreur principale, règle universelle à retenir |
| ✅ **Prompt amélioré** | Version structurée, claire et directement exploitable dans n'importe quel LLM |
| ⬇️ **Téléchargement** | Export du prompt optimisé en .txt |

---

## 🏗️ Architecture technique

```
Formulaire HTML
      ↓
  Webhook n8n
      ↓
  Modèle 1 — OpenAI GPT
  (Diagnostic + Coaching + Prompt optimisé)
      ↓
  Parse Prompt JSON (nœud Code n8n)
      ↓
  Nœud If (routing)
      ↓
  Modèle 2 — OpenAI GPT
  (Livrable métier final)
      ↓
  Code function → Code JavaScript final
      ↓
  Respond to Webhook → Affichage HTML
```

**Stack :**
- 🔧 **n8n** — orchestration du workflow (cloud)
- 🤖 **OpenAI GPT** — génération et analyse
- 🌐 **HTML / CSS / JS** — interface frontend (fichier unique, sans framework)
- 🔗 **Webhook** — communication entre le formulaire et n8n

---

## 📁 Structure du repo

```
coach-prompting/
│
├── index.html                  # Interface utilisateur complète
│
├── prompts/
│   ├── system_prompt_model1.md # System prompt du modèle de diagnostic
│   ├── user_prompt_model1.md   # Prompt user du modèle de diagnostic
│   ├── system_prompt_model2.md # System prompt du modèle de génération
│   └── user_prompt_model2.md   # Prompt user du modèle de génération
│
└── README.md                   # Documentation du projet
```

---

## 🚀 Utilisation

### Prérequis
- Un compte **n8n** (cloud ou self-hosted)
- Une clé API **OpenAI**
- Un navigateur web

### Installation

1. **Cloner le repo**
```bash
git clone https://github.com/VOTRE_USERNAME/coach-prompting.git
```

2. **Configurer n8n**
   - Créer un workflow avec un nœud **Webhook** (GET)
   - Ajouter deux nœuds **OpenAI** (modèle GPT-4 recommandé)
   - Copier les prompts depuis le dossier `/prompts`
   - Ajouter les nœuds **Code** (Parse JSON + formatage final)

3. **Connecter le webhook**
   - Copier l'URL du webhook n8n
   - Remplacer `WEBHOOK_URL` dans `index.html` :
   ```javascript
   const WEBHOOK_URL = 'https://VOTRE-INSTANCE.n8n.cloud/webhook/VOTRE-ID';
   ```

4. **Ouvrir `index.html`** dans un navigateur — l'outil est prêt.

---

## 💡 Cas d'usage démontrés

- **RH** — Rédaction d'offres d'emploi, analyse de CV, emails de recrutement
- **Commerce** — Synthèse de réunion client, propositions commerciales
- **Communication** — Briefs créatifs, contenus éditoriaux
- **Opérations** — Rapports, comptes-rendus, notes de cadrage

---

## 🧩 Logique pédagogique

L'agent est conçu pour **former**, pas seulement pour produire.

Chaque réponse distingue :
- Ce que l'utilisateur a bien formulé dans sa demande initiale
- Ce que le contexte a permis de compléter
- Ce qui reste manquant pour une demande parfaite

L'objectif : que l'utilisateur **n'ait plus besoin de l'outil** après quelques sessions.

---

## 👤 Auteur

**Lamia Brisebarre**
Consultante en transformation IA & digitale

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Lamia%20Brisebarre-blue?style=flat&logo=linkedin)](https://linkedin.com/in/lamiabrisebarre)

---

## 📄 Licence

Projet de démonstration — tous droits réservés.
