# Brief — refonte du discours du portfolio (2026)

## Prompt pour une future session Claude Code

Tu es sur le repo `sebzz07/portfolio` (Astro). Le CV de Sébastien vient d'être entièrement retravaillé (voir `docs/cv_data.json` et le reste de ce brief) suite à une analyse de son activité GitHub réelle. Le discours actuel du site (`src/pages/about.astro`, `src/pages/index.astro`) est celui de l'ancien CV 2023 et ne reflète plus son positionnement actuel. Ta tâche : mettre à jour le contenu textuel de ces pages pour qu'il corresponde aux informations ci-dessous, en conservant la structure/design existants (composants Astro, styles) sauf si Sébastien demande explicitement une refonte visuelle. Travaille sur une branche dédiée et ouvre une PR, comme indiqué dans `CLAUDE.md`. Demande confirmation à Sébastien avant de merger — le discours touche à son image professionnelle, pas seulement à du code.

Ne mentionne nulle part sur le site : le volume "2 jours/semaine" ni l'emploi non-dev en parallèle du freelance (cf. section "Point de vigilance" plus bas).

## Titre / positionnement retenu

**Développeur Web Full-Stack — PHP/WordPress & JavaScript/TypeScript**

(remplace le positionnement actuel "Développeur Web Freelance · Angular & Node.js", qui surestime Angular/Node — sa pratique la plus solide et la plus récente est en fait PHP/WordPress). Alternatives possibles si Sébastien préfère : *Développeur PHP/WordPress* (plus spécialisé) ou *Développeur Web & Chef de Projet Technique* (met en avant la coordination de projet).

## Ce qui doit changer, fichier par fichier

### `src/pages/index.astro` (accueil)

Actuel :
```
title="Sébastien Dru — Développeur Web Freelance"
tagline="Développeur Angular & Node.js, disponible pour vos projets"
```
avec des Pills : Angular, Node.js, WordPress.

À corriger : le titre/tagline et les pills mettent Angular/Node en premier alors que PHP/WordPress est le cœur réel de son activité. Proposition :
```
title="Sébastien Dru — Développeur Web Full-Stack"
tagline="PHP/WordPress & JavaScript/TypeScript — disponible pour vos projets"
```
Pills proposées : PHP, WordPress, TypeScript (ordre reflétant le poids réel des compétences).

### `src/pages/about.astro`

Plusieurs blocs à revoir :

**Sous-titre** — actuel : `Développeur Web Freelance · Angular & Node.js` → remplacer par `Développeur Web Full-Stack · PHP/WordPress & JavaScript/TypeScript`

**Tagline / accroche** — actuelle :
> "Passionné d'informatique depuis mes études, j'ai entamé ma reconversion vers le développement web après plus de 10 ans dans le commerce. Aujourd'hui développeur indépendant (auto-entrepreneur), j'accompagne mes clients dans la conception et le développement d'applications web. J'interviens principalement sur des projets Angular et Node.js, ainsi que WordPress pour les sites vitrine."

Proposition (voir aussi variantes "double discours" plus bas) :
> "Développeur web PHP/WordPress avec une bonne pratique de JavaScript/TypeScript, à l'aise aussi bien en développement qu'en coordination technique de projet. J'intègre les outils de développement assisté par IA à mon flux de travail pour livrer vite sans sacrifier la qualité. Parcours atypique — reconversion réussie vers le développement après plusieurs années en gestion — qui m'apporte autonomie et sens du concret."

**Section "Technologies"** — actuelle :
- Front End : Angular, TypeScript, HTML, SCSS
- Back End : Node.js, PHP, WordPress
- Outils : GitHub, Linux, Bootstrap

Proposition (voir `docs/cv_data.json` → `skills`) :
- Back-end : PHP, Symfony, WordPress (thèmes avancés Sage/Roots), Node.js
- Front-end : JavaScript, TypeScript, Angular, HTML/CSS/SCSS, Twig
- Outils & pratiques : Git/GitHub, Linux, Développement assisté par IA (Claude Code), Coordination technique de projet

**Section "Expériences"** — actuelle : une seule entrée générique "Développeur indépendant (auto-entrepreneur), 2023 - Actuellement" avec description Angular/Node.

Proposition — reprendre telle quelle l'expérience du CV (voir `docs/cv_data.json` → `experience[0]`), qui est beaucoup plus précise et à jour :
> **Développeur Web Freelance — Groupe Canalous** (secteur nautique/fluvial — plusieurs marques : Les Canalous, France Passion Plaisance, CPC Chantier Naval, FluvialNet), 2023 — Aujourd'hui
> - Chef de projet sur le lot thème/WordPress lors de la migration d'un site vers une infrastructure AWS, en coordination avec un DevOps et un développeur (moteur de recherche & paiement)
> - Maintenance du module Symfony (gestion des utilisateurs, archives PDF du magazine) sur FluvialNet, site multi-stack racheté par le groupe
> - Développement de thèmes WordPress avancés (Sage/Roots, Blade) sur plusieurs marques du groupe
> - Intégration de fonctionnalités sur une application de planning en Angular/Node.js/TypeScript
> - Développement assisté par IA au quotidien, et prototypage d'un MVP de génération d'articles (Python) pour FluvialNet, encore en R&D

Garder l'entrée stage Networks Technology telle quelle (déjà à jour).

**Formations / Centres d'intérêt** : déjà corrects, ne rien changer.

### `src/components/Skills.astro`

À vérifier/mettre à jour dans le même esprit (probablement les mêmes tags Angular/Node/WordPress à rééquilibrer vers PHP/WordPress en premier).

### `src/components/CvCTA.astro`

Aucun changement de code nécessaire — le fichier PDF `public/assets/CV_Sebastien_Dru.pdf` a déjà été remplacé par la nouvelle version dans ce brief.

## Argumentaire — double discours à intégrer

Le site s'adresse à deux publics différents. Deux implémentations possibles (à trancher avec Sébastien) : (a) deux blocs/CTA distincts sur la home ("Vous cherchez un développeur freelance ?" / "Vous recrutez ?"), ou (b) une page dédiée par audience.

**Discours A — Missions ponctuelles & suivi mensuel (freelance)**
Cible : TPE/PME, agences, sites WordPress existants.
> "Développeur WordPress disponible pour des missions ponctuelles (évolutions, corrections, intégrations) ou un suivi mensuel de votre site (ex. une demi-journée de dev par mois pour la maintenance, les mises à jour et les petites évolutions). Auto-entrepreneur, facturation simple, pas d'engagement long."
CTA : "Discutons de vos besoins" avec choix "mission ponctuelle" vs "suivi mensuel".

**Discours B — Recherche de poste (CDI)**
Cible : recruteurs, tech leads.
> "Développeur PHP/WordPress avec une pratique réelle de JavaScript/TypeScript, je recherche un poste où je peux m'investir pleinement dans une équipe technique. Mon parcours atypique m'a donné une autonomie et un sens des priorités que je mets aujourd'hui au service du code — j'ai notamment coordonné le lot technique d'une migration d'infrastructure, en lien direct avec une équipe DevOps."
CTA : "Disponible pour un poste de développeur — me contacter" + lien vers le CV PDF.

## Point de vigilance

Ne jamais faire apparaître sur le site : le volume "2 jours/semaine" du freelance, ni l'emploi non-dev à temps plein en parallèle. Chaque discours (freelance et CDI) doit donner l'impression d'un profil disponible et engagé sur son créneau.

## Données de référence

- `docs/cv_data.json` — toutes les données structurées du CV (identité, compétences, expériences, formation) à réutiliser telles quelles pour rester cohérent avec le PDF téléchargeable
- `public/assets/CV_Sebastien_Dru.pdf` — CV PDF à jour (déjà remplacé dans ce brief)
