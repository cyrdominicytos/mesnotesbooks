

Exigences non fonctionnelles : 

1. **Sécurité et confidentialité des données :**
    
    - Les données des utilisateurs doivent être sécurisées et protégées conformément aux normes de sécurité de l'industrie.
    - Les informations sensibles telles que les mots de passe doivent être stockées de manière sécurisée et cryptée.

2. **Performance et Scalabilité :**
    
    - Le système doit être capable de gérer au moins 10 000 connexions simultanées  sans compromettre les performances.
    - Les temps de réponse maximale de l'application  ne doit pas excéder 2 secondes.
    - Le système doit être conçu pour être évolutif afin de pouvoir s'adapter à une augmentation de la charge de travail et du nombre d'utilisateurs.
3. **Convivialité et Facilité d'utilisation :**
    
    -  L'interface utilisateur doit être conçue en tenant compte des besoins spécifiques des personnes daltoniennes.
    - Les processus d'inscription et de création de profil doivent être simples et rapides, encourageant ainsi l'engagement des utilisateurs dès le départ.
    - Les fonctionnalités de recherche et de filtrage doivent être efficaces et facilement accessibles, permettant aux utilisateurs de trouver rapidement les informations pertinentes.
4. **Fiabilité et Disponibilité :**
    
    - Le système doit être opérationnel 24 heures sur 24, 7 jours sur 7, avec un temps d'arrêt planifié minimal pour la maintenance
    - L'application doit proposer l'anglais et le français pour afficher les contenus
    - Des mécanismes de sauvegarde et de récupération des données doivent être en place pour garantir la disponibilité continue des informations critiques en cas de panne du système.
5. **Conformité aux Règlementations :**
    
    - Le système doit être conforme aux réglementations en matière de protection des données telles que le RGPD (Règlement Général sur la Protection des Données) pour assurer la confidentialité et la sécurité des données personnelles des utilisateurs.
    - Les transactions financières doivent être conformes aux réglementations en vigueur dans les juridictions où l'application est utilisée.
6. **Support et Maintenance :**
    
    - Un support technique efficace doit être disponible pour répondre aux questions des utilisateurs, résoudre les problèmes techniques et fournir une assistance générale.
    - Des mises à jour régulières du système doivent être effectuées pour corriger les bogues, améliorer les performances et ajouter de nouvelles fonctionnalités en réponse aux besoins des utilisateurs et aux évolutions du marché.


# 3. Périmètre du projet - Identification des PP - Les macro exigences ou exigences métier (dérivées du besoin) : Sona


Le périmètre du projet comprend tous les aspects inclus et exclus de l'initiative, ainsi que l'identification des principales parties prenantes et de leurs attentes.

**Inclus dans le Périmètre du Projet :**

- Développement de l'application web Co-Create, y compris toutes les fonctionnalités spécifiées pour faciliter la recherche et la facilitation de partenariats entre les utilisateurs.
- Création des profils utilisateurs pour les promoteurs de projet, les investisseurs, les collaborateurs et les administrateurs.
- Mise en place des fonctionnalités de gestion de projets collaboratifs permettant aux utilisateurs de créer, gérer et collaborer sur des projets.
- Intégration des outils de recherche et de suggestion automatique pour faciliter la mise en relation entre les utilisateurs.
- Développement des mécanismes d'évaluation et de notation des utilisateurs pour renforcer la confiance et la transparence au sein de la communauté.
- Implémentation des fonctionnalités d'administration pour gérer les inscriptions, les profils, les signalements et les politiques de modération.

**Exclus du Périmètre du Projet :**

- Toute activité ou fonctionnalité qui ne contribue pas directement à la réalisation des objectifs principaux de l'application Co-Create.
- Développement de fonctionnalités supplémentaires non spécifiées dans les exigences initiales du projet.
- Intégration avec des services tiers ou des plateformes externes qui ne sont pas explicitement mentionnés dans le cadre du projet.

**Principales Parties Prenantes et Leurs Attentes :**

1. **Promoteur de Projet :** Attendent une plateforme conviviale pour présenter leurs idées et trouver des collaborateurs et des investisseurs pour concrétiser leurs projets.
2. **Investisseurs :** Attendent une plateforme leur permettant de découvrir de nouvelles opportunités d'investissement prometteuses et de se connecter facilement avec des porteurs de projets talentueux.
3. **Collaborateurs :** Attendent une plateforme où ils peuvent mettre en valeur leurs compétences et leur expertise tout en ayant la possibilité de participer à des projets intéressants en échange de parts.
4. **Administrateurs :** Attendent des outils efficaces pour gérer les inscriptions, les profils, les signalements et assurer la maintenance générale de l'application tout en maintenant un environnement sûr et transparent pour les utilisateurs.

# Macro exigences : 

**Création de Profils Utilisateurs :** Le système doit permettre aux utilisateurs (promoteurs de projets, investisseurs, administrateurs) de créer des profils distincts en fournissant des informations telles que le nom d'utilisateur, l'adresse électronique et un mot de passe.
 
**Gestion de Projets Collaboratifs :** Les promoteurs de projets doivent pouvoir créer et gérer des projets collaboratifs sur la plateforme.
    
 **Recherche de Collaborateurs :** N'importe quel utilisateur de la plateforme doit pouvoir consulter les profils des autres, voir sa localisation, ses compétences, ses statistiques sur la plateforme.
    
 **Évaluation des Collaborateurs :** Les promoteurs de projets doivent avoir la possibilité de laisser des commentaires et des évaluations sur les collaborateurs avec lesquels ils ont travaillé, avec une option de notation sur une échelle de 1 à 5 étoiles.
    
 **Recherche de Projets :** Tout utilisateur doit être en mesure de rechercher des projets correspondant à ses critères et intérêts spécifiques.
    
 **Fonctionnalités d'Administration :** Les administrateurs doivent disposer de fonctionnalités pour valider les inscriptions des utilisateurs, examiner les profils, traiter les signalements d'utilisateurs et mettre en place des politiques pour assurer une utilisation appropriée de l'application.
    
 **Analyse des Données :** Les administrateurs doivent pouvoir analyser les données et les statistiques pour évaluer la performance de l'application et identifier les tendances et les opportunités d'amélioration.

# Fonctionnelles :

**Connexion à la Plateforme :** Les utilisateurs doivent pouvoir se connecter à la plateforme à l'aide de leurs identifiants personnels (nom d'utilisateur et mot de passe).

**Description de Projets :** Les promoteurs de projets doivent avoir la possibilité de décrire leurs projets en fournissant un titre, une description détaillée, les compétences requises et préciser le montant de financement requis.

**Suggestions Automatiques :** Le système doit être capable de suggérer automatiquement des collaborateurs compatibles basés sur les compétences renseignées par les utilisateurs.

 **Suggestions Automatiques de Projets :** Le système doit suggérer automatiquement des projets d'investissement compatibles basés sur les préférences et critères renseignés par les investisseurs.