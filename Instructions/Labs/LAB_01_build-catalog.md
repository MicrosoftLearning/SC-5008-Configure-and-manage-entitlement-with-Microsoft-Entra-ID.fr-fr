---
lab:
  title: "Labo\_1\_: créer un catalogue à utiliser dans le droit d’utilisation"
  module: 'Module : Deploying access using Microsoft Entra entitlement management'
---

# Labo 1 : créer un catalogue dans la gestion des droits d’utilisation Microsoft Entra

## Scénario de labo

Dans une entreprise de développement de logiciels de taille moyenne, le service informatique décide d’implémenter Microsoft Entra pour la gestion des droits d’utilisation. L’objectif principal est de simplifier l’accès aux ressources et aux applications au sein de l’organisation. Avec Microsoft Entra, elle peut définir des packages d’accès basés sur des rôles ou des projets, ce qui simplifie le processus d’octroi ou de révocation des droits d’accès. Par exemple, lorsqu’un nouveau développeur rejoint un projet, le service informatique peut facilement lui fournir l’accès nécessaire en lui affectant le package d’accès correspondant. Cela permet non seulement de gagner du temps, mais également de réduire le risque d’accès non autorisé. En outre, les révisions d’accès périodiques de Microsoft Entra garantissent que seules les bonnes personnes ont accès aux ressources sensibles. Dans le labo d’implémentation, l’équipe informatique configure différents packages d’accès, définit des stratégies pour l’affectation et la révocation automatiques des accès et simule une révision d’accès.

## Objectifs

À la fin de ce labo, vous serez en mesure d’effectuer les tâches suivantes :

- Créez un catalogue.
- Configurez un package d’accès.
- Déployez un package d’accès sur un utilisateur.
- Acceptez le droit d’utilisation en tant qu’utilisateur et confirmez l’accès aux ressources.
- Révoquez l’accès à un package.

## Mise en place du labo
  - **Durée estimée : 30 minutes**

### Exercice 1 : créer un catalogue pour l’équipe commerciale

#### Tâche 1 : créer un catalogue

1. Connectez-vous au centre d’administration Microsoft Entra sur `https://Entra.Microsoft.com`.

1. Dans le menu de gauche, accédez à **Gouvernance des identités**, puis **Gestion des droits d’utilisation**.

1. Sélectionnez **Catalogues** dans le menu.

 ![Capture d’écran de la création d’un catalogue avec le bouton nouveau catalogue mis en surbrillance.  Vous avez des champs pour le nom, la description et l’activation.](./Media/create-new-catalog.png)

1. Sélectionnez **+ Nouveau catalogue** en haut de l’écran.

1. Nommez et décrivez votre **nouveau catalogue** avec les valeurs suivantes :

  | Champ | Valeur |
  | :---  | :---  |
  | Nom  | `catSales` |
  | Description | `Use this catalog to assign resources for memebers of the Sales team.` |
  | activé | Oui |
  | Activé pour les utilisateurs externes | Non |
  | | |

1. Sélectionnez **Créer**.

#### Tâche 2 : ajouter des ressources aux catalogues

1. Si vous n’y êtes pas déjà, accédez à la page **Centre d’administration Microsoft Entra**, **Gouvernance des identités**, **Gestion des droits d’utilisation**, puis **Catalogues**.

1. Sélectionnez les **catSales** que nous avons créées dans la tâche précédente.

1. Dans le menu, sélectionnez **Toutes les ressources**.

1. En haut de la page, sélectionnez ensuite **+ Ajouter des ressources**.

 ![Capture d’écran de l’interface utilisateur Ajouter des ressources au catalogue. Vous pouvez ajouter des équipes, des applications, des SharePoints et d’autres éléments.](./Media/add-resources-to-catalog.png)

1. À l’aide des sélecteurs en haut de l’écran, ajoutez les ressources suivantes :

  | Type de ressource | Valeur |
  | :---  | :---  |
  | + Groupes et équipes  | Ventes et marketing, et ventes aux États-Unis |
  | + Applications | LinkedIn |
  | + Sites SharePoint | Ventes et marketing, et ventes aux États-Unis |
  | | |

1. Cliquez sur le bouton **Ajouter**.

#### Tâche 3 : créer un utilisateur pour recevoir le droit d’utilisation

1. Si vous n’y êtes pas encore, accédez au **centre d’administration Microsoft Entra**.

1. Dans le menu de gauche, sélectionnez **Identité**, **Utilisateur**, puis **Tous les utilisateurs** dans les menus.

1. En haut de la page, sélectionnez **+ Nouvel utilisateur**.

1. Renseignez les valeurs dans la page **Informations de base** :

  | Champ | Valeur |
  | :---  | :---  |
  | Nom d’utilisateur principal  | `ChrisGr` |
  | Nom d’affichage | `Christopher Green` |
  | Mot de passe généré automatiquement | Vérifié |
  | Compte activé | Vérifié |
  | | |

1. Copiez et collez le mot de passe dans un emplacement sécurisé tel que le bloc-notes (vous aurez besoin du mot de passe plus tard dans ce labo).

1. Sélectionnez l’onglet Propriétés.

1. En bas de l’écran Propriétés, définissez l’**emplacement d’utilisation sur États-Unis**.

1. Sélectionnez **Examiner et créer**, puis sélectionnez **Créer**.

#### Tâche 4 : générer le package d’accès

1. Dans le Centre d’administration Microsoft Entra, sélectionnez **Gouvernance des identité**, puis **Gestion des droits d’utilisation**.

1. Dans le menu Gestion des droits d’utilisation, sélection **Packages d’accès**.

1. En haut de l’écran, sélectionnez **+ Nouveau package d’accès**.

1. Entrez les valeurs demandées :

  | Champ | Valeur |
  | :---  | :---  |
  | Nom  | `pckSales` |
  | Nom d’affichage | `Use this access package to assign resources to members of the Sales team.` |
  | Catalogue | catSales |
  | | |

  **Note** : vous devez sélectionner le catalogue catSales que nous avons créé dans la tâche précédente. Vous obtiendrez ainsi la liste des ressources qui peuvent être affectées dans ce package.  Il existe un package général répertorié comme étant la valeur par défaut.  Si vous avez choisi cela accidentellement, vous ne verrez aucune ressource disponible.

1. Sélectionnez l’onglet Rôles des ressources.

1. Sélectionnez les ressources que vous souhaitez fournir dans son package d’accès, parmi les éléments du catalogue catSales. Utilisez ensuite la liste déroulante **Sélectionner un rôle** pour définir le rôle indiqué dans le tableau ci-dessous.

  | Type de ressource | Valeur | Rôle |
  | :---  | :---  | :--- |
  | + Groupes et équipes  | Vente et marketing | Membre |
  | + Applications | LinkedIn | msiam_access |
  | + Sites SharePoint | Ventes aux États-Unis | Membres des ventes aux États-Unis |
  | | |

1. Définissez la liste déroulante **Sélectionner un rôle** pour définir le rôle sur **Membre** pour chaque élément.

1. Utilisez **Suivant : Demandes>** pour accéder à l’onglet Demandes.

1. Dans la liste **Utilisateurs qui peuvent demander l’accès**, sélectionnez l’option **Aucun (affectations directes d’administrateur uniquement).

1. Définissez la valeur **Activer** sur **Oui**.

1. Accédez à l’onglet **Cycle de vie** à l’aide des étiquettes situées en haut de l’écran.

1. Choisissez les valeurs pour définir le cycle de vie du pacakge :

  | Champ | Valeur |
  | :---  | :---  |
  | Expiration des affectations de package d’accès  | Nombre de jours |
  | Délai d’expiration des affectations | 30 |
  | Les utilisateurs peuvent demander une chronologie spécifique. | Non |
  | Exiger des révisions d’accès | Non |
  | | |

1. En bas de l’écran, sélectionnez **Examiner et créer**.

1. Passez en revue les valeurs que vous avez choisies sur l’écran Examiner et créer.

1. Sélectionnez **Créer** pour générer votre package d’accès.

#### Tâche 5 : affecter le package à Christopher

1. Vérifiez que vous êtes dans **Centre d’administration Microsoft Entra**, ** Gouvernance des identités**, **Gestion des droits d’utilisation** et que le menu **Packages Access** est ouvert.

1. Sélectionnez les **pckSales** que nous avons créés dans la tâche précédente.

1. Dans le menu, sélectionnez **Affectations**.

1. En haut de l’écran, sélectionnez **+ Nouvelle affectation**.

1. Pour **Sélectionner une stratégie **, utilisez la **stratégie initiale** fournie dans la liste déroulante.

1. Vérifiez que la case **Utilisateur déjà dans mon répertoire** est cochée.

1. Dans la boîte de dialogue, sélectionnez l’élément **Ajouter des utilisateurs**.

1. Dans la liste des utilisateurs, rcherchez **Christopher Green**.  Cochez la case en regard de ce nom.  En bas de l’écran, cliquez ensuite sur le bouton **Sélectionner**.

1. Conservez les valeurs par défaut pour les autres éléments.

1. Sélectionnez le bouton **Ajouter** en bas de la page.

#### Tâche 6 : vérifier si Christopher Green a été ajouté

1. Dans votre navigateurs, ouvrez une **nouvelle fenêtre de navigation privée**.

1. Connectez-vous au **centre d’administration Microsoft Entra** à l’adresse `https://entra.microsoft.com`.

1. Connectez-vous au site à l’aide de votre compte Chistopher Green et du mot de passe créés précédemment.

1. Vous serez invité à modifier votre mot de passe.  Définissez un nouveau mot de passe et enregistrez-le dans un outil tel que le Bloc-notes pour une utilisation ultérieure.

1. Sélectionnez **Identité**, **Utilisateurs**, **Tous les utilisateurs**, puis **Christopher Green**.

1. Dans le menu de gauche, sélectionnez **Groupes**.

1. Vérifiez que vous avez reçu l’accès au groupe **Ventes et Marketing**, conformément au package d’accès.

1. Dans le menu de gauche, sélectionnez **Applications**.

1. Vérifiez que **LinkedIn** fait partie de vos applications affectées.

#### Tâche 7 : défi - Modifications dynamiques apportées au package d’accès

  **Note** : cette tâche n’a pas d’instructions détaillées. Vous avez accès à l’ensemble des tâches et vous pouvez vous référer aux étapes précédentes ci-dessus pour savoir où apporter des modifications spécifiques.

- Veillez à vous connecter au **centre d’administration Microsoft Entra** avec votre compte Administrateur.
- Ouvrez votre package d’accès **pckSales**.
- Accédez à **Rôles des ressources** et choisissez de supprimer le groupe **Ventes et Marketing** et ajoutez plutôt le groupe **Ventes aux États-Unis**.
- Utilisez l’onglet **Affectations** pour **retraiter** l’affectation.
- Déconnectez-vous et reconnectez-vous en tant que Christopher Green.  Notez que les affectations de groupe ont changé.  C’est rapide et facile.
- Révoquez l’accès en supprimant l’affectation pour Christopher Green.

### Conclusion
Il s’agit d’un labo simple pour démontrer les fonctionnalités de base de la gestion des droits d’utilisation.  Pensez à l’option pour laquelle vous pouvez utiliser cette fonctionnalité, et aux options de configuration avancées que vous pouvez configurer dans le labo.
