# 🚗 DZ-CarPool — Plateforme de Covoiturage en Algérie

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)]()
[![Django](https://img.shields.io/badge/Django-4.2-green)]()
[![Next.js](https://img.shields.io/badge/Next.js-14-black)]()
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue)]()
[![Docker](https://img.shields.io/badge/Docker-ready-2496ED)]()
[![License](https://img.shields.io/badge/licence-Académique-orange)]()

---

## 📋 Description du Projet

**DZ-CarPool** est une plateforme web de covoiturage dédiée aux déplacements inter-wilayas en Algérie. Elle met en relation des conducteurs proposant des trajets avec des passagers à la recherche de transport économique et fiable.

Le projet répond à un besoin réel en Algérie : réduire les coûts de transport, optimiser l'utilisation des véhicules privés, et offrir une alternative moderne aux transports en commun traditionnels.

---

## 🎯 Fonctionnalités Principales

### 👤 Gestion des Utilisateurs
- Inscription et authentification sécurisée (JWT)
- Profils distincts : **Conducteur** / **Passager**
- Photo de profil, biographie, historique des trajets
- Authentification via Google OAuth

### 🗺️ Gestion des Trajets
- Création, modification et suppression de trajets
- Recherche avancée par : ville de départ, ville d'arrivée, date, nombre de places
- Suggestion automatique de prix basée sur le prix du carburant par wilaya
- Suivi en temps réel des trajets disponibles

### 📦 Réservations
- Système de réservation avec approbation manuelle par le conducteur
- Notifications en temps réel (WebSocket)
- Historique complet des réservations

### 💬 Messagerie
- Messagerie intégrée entre conducteur et passager
- Notifications instantanées

### 💰 Tarification
- Commission plateforme : **15%**
- Option **Trajet Confort** : supplément de **30%**
- Prix suggéré automatiquement selon le carburant local

---

## 🛠️ Stack Technique

### Backend
| Technologie | Version | Rôle |
|---|---|---|
| Django | 4.2 | Framework principal |
| Django REST Framework | 3.14 | API RESTful |
| PostgreSQL | 15 | Base de données relationnelle |
| Redis | 7 | Cache et WebSocket |
| JWT (SimpleJWT) | latest | Authentification |
| OpenAPI/Swagger | drf-spectacular | Documentation API |
| Celery | latest | Tâches asynchrones |

### Frontend
| Technologie | Version | Rôle |
|---|---|---|
| Next.js | 14 | Framework React (App Router) |
| TypeScript | 5 | Typage statique |
| Tailwind CSS | 3 | Styles utilitaires |
| Axios | latest | Appels API |
| Zustand | latest | Gestion d'état |
| React Query | latest | Fetching et cache |

### DevOps & Qualité
| Outil | Rôle |
|---|---|
| Docker & Docker Compose | Containerisation |
| GitHub Actions | CI/CD Pipeline |
| Pytest | Tests backend |
| Jest & Playwright | Tests frontend et E2E |
| Flake8 | Qualité du code Python |

---

## 🚀 Démarrage Rapide

### Prérequis
- Docker Desktop installé
- Git installé
- 4 Go de RAM minimum recommandés

### Installation

**1. Cloner le projet**
```bash
git clone https://github.com/MHMD-SD1010/DZ-CarPool.git
cd DZ-CarPool
```

**2. Configurer les variables d'environnement**
```bash
cp .env.test .env
# Modifier les valeurs dans .env selon votre configuration
```

**3. Lancer les conteneurs**
```bash
docker-compose build
docker-compose up -d
```

**4. Initialiser la base de données**
```bash
docker-compose exec backend python manage.py migrate
docker-compose exec backend python manage.py createsuperuser
```

### Accès aux services
| Service | URL |
|---|---|
| Frontend | http://localhost:3000 |
| API REST | http://localhost:8000/api/ |
| Admin Django | http://localhost:8000/admin/ |
| Documentation API | http://localhost:8000/api/docs/ |

---

## 📁 Structure du Projet
DZ-CarPool/
├── .github/
│   └── workflows/          # Pipelines CI/CD GitHub Actions
├── Backend/                # API Django REST Framework
│   ├── config/             # Configuration Django (settings, urls)
│   ├── core/               # Logique métier commune
│   ├── apps/               # Applications Django modulaires
│   │   ├── users/          # Gestion des utilisateurs
│   │   ├── trips/          # Gestion des trajets
│   │   ├── bookings/       # Réservations
│   │   └── messaging/      # Messagerie
│   ├── tests/              # Tests unitaires et d'intégration
│   └── requirements.txt    # Dépendances Python
├── frontend/               # Application Next.js 14
│   ├── app/                # Pages et routing (App Router)
│   ├── components/         # Composants réutilisables
│   ├── hooks/              # Hooks personnalisés
│   ├── services/           # Appels API
│   ├── stores/             # Gestion d'état (Zustand)
│   └── tests/          # Tests Jest
├── BDD/                    # Scripts et schémas base de données
├── apps/                   # Configuration des applications
├── docker-compose.yml      # Orchestration des services
├── makefile                # Commandes utilitaires
└── README.md

---

## 🧪 Tests

### Backend
```bash
docker-compose exec backend pytest
docker-compose exec backend pytest --cov=. --cov-report=html
```

### Frontend
```bash
docker-compose exec frontend npm test
docker-compose exec frontend npm run test:coverage
```

### Tests End-to-End (Playwright)
```bash
npx playwright test
npx playwright test --ui
```

---

## 🔄 CI/CD Pipeline

Le projet utilise **GitHub Actions** avec les étapes suivantes à chaque push :

1. **Code Quality** — Vérification du style (Flake8, ESLint)
2. **Security Scan** — Analyse des vulnérabilités
3. **Tests Backend** — Pytest avec rapport de couverture
4. **Tests Frontend** — Jest sur Node.js 18.x et 20.x
5. **Build Docker Image** — Construction et validation de l'image

---

## 📐 Architecture

Le projet suit une architecture **client-serveur découplée** :

- Le **Backend** expose une API RESTful consommée par le Frontend
- Le **Frontend** est une SPA (Single Page Application) avec Next.js App Router
- **Redis** gère le cache et les communications WebSocket en temps réel
- **PostgreSQL** stocke toutes les données relationnelles
- **Docker** assure la portabilité et la reproductibilité de l'environnement

---

## 👥 Équipe de Développement

| Nom | Rôle |
|---|---|
| SAIDI Mahmoud | Full Stack Developer |
| OUDJANE Anies | Backend Developer |
| MELLIT Aroua | Frontend Developer |
| AOUF Abdel mounaim | Frontend Developer |
| HEBIB Kenza | UI/UX Designer |

---

## 📄 Informations Académiques

> Ce projet est réalisé dans le cadre du module **PP_2CP**.
> Il illustre les bonnes pratiques de développement logiciel :
> architecture en couches, intégration continue,
> containerisation et documentation technique.

---

*DZ-CarPool — Connecter les Algériens, un trajet à la fois.* 🇩🇿
