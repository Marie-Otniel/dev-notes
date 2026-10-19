# Note 09 : L'IA comme miroir — Auditer son architecture avant de coder

![Couverture](../assets/cover-ai-audit.svg)

## Problème
Lorsqu'on lance une nouvelle fonctionnalité ou un SaaS, le premier réflexe est souvent de coder immédiatement le schéma de données. Le risque ? Oublier une relation critique, une contrainte de scalabilité ou un cas limite (edge case) qui obligera à une migration douloureuse dans trois mois. La complexité est souvent invisible tant qu'elle n'est pas confrontée à la réalité.

## Décision
Utiliser les LLM (Large Language Models) non pas pour générer le code, mais pour **auditer l'architecture**. La décision est de traiter l'IA comme un "Senior Architect" à qui l'on présente son plan avant de poser la première brique. L'objectif est de transformer l'IA en miroir critique pour révéler les failles logiques de notre conception.

## Implémentation

1.  **Le Prompt de "Stress Test"** : Ne demandez pas "Génère-moi ce schéma". Donnez votre schéma et demandez :
    > "Voici mon schéma Drizzle pour une application de gestion de flotte. Identifie 3 scénarios où ce schéma échouera à mesure que le volume de données décuple ou si un utilisateur tente de faire [action complexe]."

2.  **L'Audit de Cohérence** : Présentez vos choix technologiques (Stack) et demandez à l'IA de trouver les "mismatchs" opérationnels.
    > "J'utilise Supabase Auth avec un backend Express custom. Quels sont les risques de désynchronisation de session et comment les mitiger ?"

3.  **La Documentation par l'IA** : Demandez à l'IA de rédiger les "Conséquences" d'une ADR (Architecture Decision Record) à partir de votre décision. Elle verra souvent des impacts sur la maintenance que vous avez omis.

## Leçon
L'IA est bien plus puissante comme **auditeur** que comme **générateur**. En tant que **Product Builder**, déléguer la réflexion critique à un LLM permet de gagner des semaines de refactorisation. La valeur n'est pas dans la réponse, mais dans la question qui vous force à repenser votre structure.

## Ressource utile
[Data Modeling 101](https://www.mongodb.com/resources/basics/databases/data-modeling) — Un guide fondamental pour comprendre les bases de la modélisation avant même d'ouvrir votre éditeur de prompt.

---
*Marie-Otniel · Le Dev Writer*
