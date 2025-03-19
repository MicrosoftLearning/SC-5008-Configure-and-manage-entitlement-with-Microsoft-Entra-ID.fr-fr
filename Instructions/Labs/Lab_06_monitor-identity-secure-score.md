---
lab:
  title: "Labo\_6\_: surveiller et gérer la posture de sécurité avec le score d’identité sécurisée"
  module: 'Module : Deploying access using Microsoft Entra entitlement management'
---

# Labo 6 : surveiller et gérer la posture de sécurité avec le score d’identité sécurisée

## Scénario de labo

Microsoft Entra Identity Protection fournit une détection et une correction automatisées des risques basés sur l’identité ainsi que des données dans le portail pour examiner les risques potentiels. Protection des ID Microsoft Entra fournit également un score d’identité sécurisée pour surveiller et améliorer votre posture des identités.  De la même manière que Microsoft Defender XDR et Microsoft Defender pour le cloud, le score d’identité sécurisée offre des suggestions et des actions d’amélioration qui peuvent améliorer votre posture de sécurité globale pour les identités dans Microsoft Entra ID.  Ce labo va vous permettre d’explorer cette fonctionnalité. 

#### Durée estimée : 15 minutes

### Exercice 1 : Utilisation du score de sécurisation des identités pour surveiller et gérer la posture de sécurité des identités

#### Tâche 1 : passer en revue le score sécurisé des identités et les actions d’amélioration

1. Connectez-vous à la plateforme  [https://entra.microsoft.com](https://entra.microsoft.com) en tant qu’administrateur global.

2. Ouvrez le **menu Protection** et sélectionnez **Score d’identité sécurisée**

**NOTE** : vous accédez ainsi au tableau de bord Score d’identité sécurisée.

3. Faites défiler vers le bas pour afficher les **actions d’amélioration**.

4. Contrairement aux actions d’amélioration dans Microsoft Defender pour le cloud et Microsoft Defender XDR, ces actions d’amélioration sont spécifiques aux identités.  Cet outil fournit une liste plus ciblée d’actions potentielles pour votre gestion de la posture de sécurité.  Toutes les actions d’amélioration lancées à partir de cette liste agissent également sur votre posture globale de sécurité des locataires. 

#### Tâche 2 : exécuter une action d’amélioration

1. Pour améliorer un domaine de la posture de sécurité des identités, sélectionnez **Activer les stratégies de risque de connexion à Microsoft Entra ID Identity Protection**.

3. Dans le menu de gauche, ouvrez **Identity Protection | Stratégie de connexion à risque**.

4. Sélectionnez **Tous les utilisateurs** sous **Affectations**.

5. Sous **Connexion à risque**, sélectionnez **Moyen et supérieur**.

6. Sous **Contrôles** - , sélectionnez **Autoriser****Exiger une authentification multifacteur**.

7. **Activez** **Application de la stratégie** (si ce n’est pas déjà fait), puis sélectionnez **Enregistrer**.

8. Vous avez créé une stratégie de connexion à risque qui doit maintenant augmenter votre score d’identité sécurisée.  Cela prendra jusqu’à 24 heures pour que votre score d’identité sécurisée soit affecté.

9. Passez en revue les autres actions d’amélioration et les étapes à suivre pour les créer et les activer.
