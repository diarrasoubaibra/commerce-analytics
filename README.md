# Ecommerce Analytics Project

![Python](https://img.shields.io/badge/Python-3.11-blue)
![Pandas](https://img.shields.io/badge/Pandas-Yes-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📖 Description

Ce projet permet de collecter, nettoyer, enrichir et agréger les données d’un site e-commerce et de magasins physiques pour produire des indicateurs quotidiens et mensuels.  

**Workflow :**  
1. Extraction depuis Google Drive et une base SQLite.  
2. Nettoyage des données pour supprimer doublons et valeurs manquantes.  
3. Enrichissement des commandes (calcul du chiffre d’affaires).  
4. Agrégation pour générer des KPI quotidiens et mensuels.  

---
```bash
## 🗂️ Structure du projet
ecommerce-analytics/
├── data/
│ ├── raw_data/ # Données brutes
│ ├── cleaned_data/ # Données nettoyées
│ ├── enriched_data/ # Données enrichies
│ └── aggregated_data/ # Données agrégées
├── dags/
│ └── common/
│ ├── extract.py
│ ├── transform.py
│ ├── enrich.py
│ └── aggregate.py
├── requirements.txt
└── README.md
```


---

## ⚙️ Installation rapide

1. Cloner le projet :

```bash
git clone <URL_DU_PROJET>
cd ecommerce-analytics
```
2. Créer un environnement virtuel et activer :
```
python -m venv dahvenv
source dahvenv/bin/activate  # Linux/Mac
dahvenv\Scripts\activate     # Windows
```
3. Installer les dépendances
```
pip install -r requirements.txt
```
4. Ajouter le fichier Google Service Account JSON dans dags/common :
```
****************.json
```
🚀 Exécution rapide

1️⃣ Extraction des données :
```
cd dags/common
python extract.py
```
2️⃣ Nettoyage des données :
```
python transform.py
```
3️⃣ Enrichissement des commandes :
```
python enrich.py
```
4️⃣ Agrégation des KPI :
```
python aggregate.py
```
📊 KPI générés
| Type               | Source                 | Indicateur                | Périodicité |
| ------------------ | ---------------------- | ------------------------- | ----------- |
| Clients            | cleaned\_data/clients  | Nombre de clients uniques | Quotidien   |
| Stock              | cleaned\_data/products | Stock total disponible    | Quotidien   |
| Chiffre d’affaires | enriched\_data/orders  | Somme des `revenue`       | Mensuel     |

🛠️ Dépendances

Python 3.11

pandas

google-api-python-client

google-auth

sqlite3 (standard)

pathlib (standard)

```
pip install pandas google-api-python-client google-auth
```

🔑 Bonnes pratiques

Conserver la structure année/mois/jour pour tous les fichiers.

Vérifier que le fichier Service Account JSON est présent avant l’exécution.

Lancer les scripts dans l’ordre : extract.py → transform.py → enrich.py → aggregate.py.
