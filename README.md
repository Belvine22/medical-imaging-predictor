# 🏥 Medical Imaging Disease Predictor

> Système d'aide au diagnostic médical par analyse d'images —
> développé dans le cadre d'une alternance chez Neyke (2024-2026)
> Code source confidentiel — vitrine technique publique

---

## 🎯 Résultats clés

| Métrique | Valeur |
|----------|--------|
| 🎯 Précision moyenne | **92%** |
| 🖼️ Images d'entraînement | **30 100** (via Kaggle) |
| 🏷️ Pathologies couvertes | **38 pathologies** |
| 📂 Catégories | **6 catégories** |
| ⚡ Temps de prédiction | **< 10 secondes** |
| 🧠 Modalités d'imagerie | IRM · Radiographie · Dermatologie |

---

## 🏗️ Architecture du système
```
            IMAGE MÉDICALE (input)
                     │
                     ▼
        ┌────────────────────────┐
        │        ROUTEUR         │
        │  (entraîné sur noms    │
        │   des 6 catégories)    │
        └────────────┬───────────┘
                     │
       ┌─────────────┼──────────────┬──────────────┬──────────────┐
       │             │              │              │              │
       ▼             ▼              ▼              ▼              ▼
┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
│Modèle 1  │  │Modèle 2  │  │Modèle 3  │  │Modèle 4  │  │Modèle N  │
│Neurologie│  │Pneumo.   │  │Oncologie │  │Orthopédie│  │  ...     │
│DenseNet  │  │EfficientN│  │DenseNet  │  │EfficientN│  │          │
└────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘
     │             │              │              │              │
     └─────────────┴──────────────┴──────────────┴──────────────┘
                                  │
                                  ▼
                   ┌──────────────────────────┐
                   │  MODULE DE DÉCISION       │
                   │  Application seuils de    │
                   │  confiance & validation   │
                   │  (OOD Detection)          │
                   └──────────────┬────────────┘
                                  │
                                  ▼
                   ┌──────────────────────────┐
                   │  MODULE DE RESTITUTION    │
                   │  Génération résultat      │
                   │  interprétable            │
                   └──────────────┬────────────┘
                                  │
                                  ▼
                   ┌──────────────────────────┐
                   │  RÉSULTAT SPÉCIALISTE     │
                   │  • Maladies probables     │
                   │  • Scores de confiance    │
                   │  • Temps : < 10 secondes  │
                   └──────────────┬────────────┘
                                  │
                                  ▼
                          API REST Django
                          Déploiement Plesk
```
---

## 🗂️ Catégories et pathologies couvertes

| Catégorie | Modalité | Exemples de pathologies |
|-----------|----------|------------------------|
| 🧠 Neurologie | IRM cérébrale | Alzheimer, tumeurs cérébrales, AVC |
| 🫁 Pneumologie | Radiographie thoracique | Pneumonie, cancer du poumon, COVID-19 |
| 🎗️ Oncologie mammaire | Mammographie | Cancer du sein, tumeurs bénignes |
| 🦴 Orthopédie | Radiographie osseuse | Fractures, arthrose, ostéoporose |
| 🔬 Dermatologie | Image clinique | Mélanome, carcinome, lésions cutanées |
| 👁️ Ophtalmologie | Fond d'œil | Rétinopathie diabétique, glaucome |

---

## 🛠️ Stack technique

**Deep Learning & ML**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat&logo=huggingface&logoColor=black)

**MLOps**

![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat&logo=mlflow&logoColor=white)
![GitLab](https://img.shields.io/badge/GitLab CI/CD-FC6D26?style=flat&logo=gitlab&logoColor=white)

**Déploiement**

![Django](https://img.shields.io/badge/Django REST-092E20?style=flat&logo=django&logoColor=white)
![Plesk](https://img.shields.io/badge/Plesk-52BBE6?style=flat&logo=plesk&logoColor=white)

---

## 🔄 Pipeline ML complet

Kaggle Datasets (30 100 images)
│
▼
┌───────────────────┐
│   PRÉTRAITEMENT   │  Resize · Normalisation ·
│                   │  Augmentation (rotation,
│                   │  flip, brightness...)
└────────┬──────────┘
│
▼
┌───────────────────┐
│   ENTRAÎNEMENT    │  DenseNet121 / EfficientNetB3
│                   │  Transfer Learning
│                   │  MLflow tracking
└────────┬──────────┘
│
▼
┌───────────────────┐
│   ÉVALUATION      │  Accuracy · F1-Score
│                   │  Matrice de confusion
│                   │  Courbes ROC
└────────┬──────────┘
│
▼
┌───────────────────┐
│   INFÉRENCE       │  < 10 secondes / image
│                   │  OOD Detection
│                   │  Score de confiance
└────────┬──────────┘
│
▼
┌───────────────────┐
│   API REST Django │  Endpoints sécurisés
│   + Plesk         │  Conformité RGPD
└───────────────────┘

---

## ⚠️ Note sur la confidentialité

Ce projet a été développé dans le cadre d'une **alternance chez Neyke (2024–2026)**. 
Le code source est la propriété de l'entreprise et reste **confidentiel**.

Ce repository est une **vitrine technique publique** décrivant l'architecture, 
les résultats et les choix technologiques du projet.

> Code source disponible sur demande auprès de l'entreprise.

---

## 👩‍💻 Auteure

**Belvine YEMDJO** — [@Belvine22](https://github.com/Belvine22)

Ingénieure Systèmes Numériques & IA — UTT 2026

