# Note 06 : Transformer l'erreur en opportunité de conversion

![Couverture](../assets/cover-erreurs.svg)

## Problème
Les messages d'erreur génériques ("Une erreur est survenue", "Champ invalide") sont des points de friction majeurs. Dans un SaaS, une erreur mal gérée est souvent synonyme d'abandon de panier ou de désinscription. L'utilisateur se sent perdu, voire fautif, ce qui brise la confiance et le "flow" de conversion.

## Décision
Passer d'une gestion d'erreur purement technique à une gestion d'erreur **éditoriale et proactive**. Chaque erreur doit être traitée comme une opportunité de guider l'utilisateur. La décision est d'intégrer le copywriting et l'UX dès la définition des codes d'erreur côté serveur.

## Implémentation

1.  **Typage sémantique des erreurs** : Ne jamais renvoyer un code 500 ou 400 brut. Côté backend (tRPC/Express), utiliser des classes d'erreurs explicites :
    ```typescript
    if (!hasEnoughCredits) {
      throw new TRPCError({
        code: 'FORBIDDEN',
        message: 'SOLDE_INSUFFISANT', // Code interne pour le front
      });
    }
    ```

2.  **Copywriting empathique et orienté action** : Au lieu de "Identifiants incorrects", utiliser :
    > "Ce mot de passe ne semble pas correspondre. Voulez-vous le réinitialiser pour accéder à votre compte ?"

3.  **Appel à l'action (CTA) contextuel** : Inclure un lien direct vers la solution dans le composant d'alerte. Si le paiement échoue, le message d'erreur doit contenir un bouton "Mettre à jour ma carte".

4.  **Design non-punitif** : Utiliser des teintes de rouge adoucies ou des couleurs d'accentuation (comme le Terracotta de Maison Kora) et des micro-animations pour dédramatiser l'instant.

## Leçon
Une erreur bien gérée renforce la fidélité. L'utilisateur qui reçoit une aide précise au moment où il échoue se sent accompagné. C'est ici que le rôle de **Dev Writer** prend tout son sens : le code sécurise la transaction, mais le texte sauve la relation client.

## Ressource utile
[Microcopy: The Complete Guide](https://www.microcopybook.com/) — La référence absolue pour transformer chaque message système en levier de rétention et d'engagement.

---
*Marie-Otniel · Le Dev Writer*
