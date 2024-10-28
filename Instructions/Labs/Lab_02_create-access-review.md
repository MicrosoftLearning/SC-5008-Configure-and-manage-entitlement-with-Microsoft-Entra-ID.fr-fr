---
lab:
  title: "Labo 2\_: créer et gérer une révision d’accès"
  module: 'Module : Deploying access using Microsoft Entra entitlement management'
---

# Labo 2 : créer et gérer une révision d’accès

## Scénario de labo

Les révisions d’accès permettent de garantir que seules les bonnes personnes ont accès aux ressources et aux informations. Une révision d’accès peut être configurée pour des périodes ponctuelles ou périodiques, et permet aux réviseurs d’approuver ou de refuser l’accès en fonction de facteurs tels que le rôle d’utilisateur, la dernière connexion ou le niveau de risque. Les résultats de ces révisions peuvent ensuite être utilisés pour mettre à jour les droits d’accès des utilisateurs, en s’assurant qu’ils respectent les stratégies et les exigences de conformité de l’entreprise. Pour cette entreprise, une révision d’accès est effectuée lorsqu’un employé modifie des rôles au sein d’une entreprise. Par exemple, si un employé passe d’un rôle de vente à un rôle marketing, il peut ne plus avoir besoin d’accéder à certaines bases de données ou applications de vente. Une révision d’accès permet d’identifier ces autorisations inutiles et permet à l’entreprise de les révoquer, réduisant ainsi le risque d’accès non autorisé ou de fuites de données.

#### Durée estimée : 15 minutes

### Exercice 1 : vérifiez si des utilisateurs ont accès à LinkedIn alors qu’ils ne devraient pas utiliser cette ressource.

#### Tâche 1 : créer une révision d’accès - Type de révision

1. Connectez-vous à [https://entra.microsoft.com](https://entra.microsoft.com) en utilisant un compte d’administrateur général.

1. Ouvrez le menu **Identité**, puis sélectionnez  **Gouvernance d’identité**.

1. Dans le menu de gauche, sélectionnez **Révisions d’accès**.

1. Dans le menu supérieur, sélectionnez **+ Nouvelle révision d’accès**.

1. Dans le volet Nouvelle révision d’accès, dans la liste déroulante Sélectionner ce qui doit être examiné, sélectionnez l’élément **Applications**.

1. Utilisez **+ Sélectionner des applications** pour choisir **LinkedIn ** dans la liste.

1. Pour l’**étendue**, sélectionnez **Tous les utilisateurs**.

1. Sélectionnez le bouton **Suivant : révisions** en bas de l’écran.

#### Tâche 2 : créer une révision d’accès - Révisions

1. Cochez temporairement la case **Révision en plusieurs étapes**.

 **Note** : c’est là que vous pouvez choisir d’avoir plusieurs couches à votre révision d’accès.  Utilisez cette option pour des ressources très importantes, afin que la révision d’une seule personne n’ajoute ni ne supprime une ressource critique pour l’accès de l’utilisateur.  Nous ne allons pas générer ni tester une révision en plusieurs étapes, mais le processus est très similaire.

1. Décochez la case **Révision en plusieurs étapes**.

1. Dans la page Révision, renseignez les valeurs ci-dessous :

| Nom du champ | Valeur |
| :--- | :--- |
| Sélectionner des réviseurs | Utilisateurs ou groupes sélectionnés - Adele Vance |
| Durée (en jours) | 5 |
| Récurrence de la révision | Mensuelle |
| Date de début | Date du jour |
| Fin | Terminer après le nombre d’occurrences |
| Occurences | 3 |
| | |

1. Sélectionnez l’option **Suivant : paramètres**.

#### Tâche 3 : créer une révision d’accès - Paramètres

1. Laissez la case **Appliquer automatiquement les résultats aux ressources** décochée.

 **Note** : nous voulons nous assurer que nous validons les résultats une fois la révision terminée.

1. Choisissez l’option **Supprimer l’accès** pour **Si le réviseur ne répond pas**.

 **Note :** il s’agit d’un paramètre que vous pouvez utiliser pour contrôler votre niveau de sécurité.  Si aucune révision ne répond dans une posture de sécurité moins sécurisée, vous pouvez utiliser Approuver l’accès.  Dans une posture de sécurité très sécurisée, vous pouvez utiliser l’option Supprimer l’accès.  Lorsque vous implémentez vos propres solutions, choisissez ce qui convient le mieux à votre entreprise.

1. Pour l’option **À la fin de la révision, envoyer une notification à** sélectionnez le compte Administrateur que vous utilisez dans ce labo.

1. Laissez les valeurs par défaut pour **Activer l’assistance aux décisions de révision**.

1. Pour **Contenu supplémentaire de l’e-mail du réviseur** entrez la valeur `Please complete your Access Review as soon as you can.`.

1. Sélectionnez **Suivant : examiner et créer **.

1. Entrez les valeurs ci-dessous pour le nom et la description.

| Nom du champ | Valeur |
| :--- | :--- |
| Nom de la révision | `Check LinkedIn` |
| Description | `In this access review, we check to see if the right people have access to LinkedIn.` |
| | | 

1. Sélectionnez **Créer**.

#### Tâche 4 : de connecter en tant qu’Adele pour exécuter la révision d’accès

1. Fermez votre navigateur, si vous l’avez ouvert.

1. Ouvrez le navigateur et connectez-vous à `https://outlook.office.com/`.

1. Vous serez invité à modifier votre mot de passe une fois que vous vous connectez en tant qu’Adele.

1. Connectez-vous en tant qu’Adele Vance en fonction de votre locataire.

 **Note** : vous devez avoir reçu un e-mail de **Sécurité Microsoft** dont l’objet est **Action requise : révisez l’accès à LinkedIn...**. L’envoi de cet e-mail peut prendre jusqu’à 10 minutes.

1. Sélectionnez le bouton **Commencer la révision >**.

 ![Capture d’écran de la page Révision d’accès d’Adele V en cliquant sur le lien dans l’e-mail.  Notez qu’il est recommandé de supprimer Christopher Green.](./Media/access-review-page.png)

1. Cochez le cercle à côté de **Christopher Green**.

1. Dans le menu supérieur, sélectionnez l’option **Refuser**.

1. Entrez une raison de refuser l’accès à la ressource. Exemple : `The sales campaign is over and Christopher does not need access any more`.

1. Sélectionnez le bouton **Envoyer** pour envoyer votre recommandation.

#### Tâche 5 : confirmer les résultats de la révision d’accès

1. Fermez votre navigateur, si vous l’avez ouvert.

1. Ouvrez le navigateur et connectez-vous à `https://Entra.Microsoft.com/`.

1. Connectez-vous à Microsoft Entra avec votre compte Administrateur.

1. Dans le menu gauche, ouvrez **Gouvernance des identités**.

1. Sélectionner des **révisions d’accès**

1. Sélectionnez la révision **LinkedIn** que nous avons créée précédemment dans ce labo.

1. Passez en revue la réponse d’Adele V.
