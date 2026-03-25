# Color Transfer with Optimal Transport (OT)

## Objectif
Comparer plusieurs méthodes de **transfert de couleurs** entre images, avec un focus sur le **Transport Optimal**, en travaillant dans un espace perceptuel adapté (**Lab**).



## Espace de représentation : Lab

Les images sont converties de RGB → **Lab** :

- **L** : luminosité  
- **a / b** : composantes chromatiques  

=> Plus proche de la perception humaine  
=> Distances euclidiennes plus pertinentes pour la couleur  


## Transport Optimal (OT)

Le transport optimal vise à transformer une distribution source en une distribution cible en minimisant un coût de transport :

- Basé sur la **distance de Wasserstein (Earth Mover’s Distance)**
- Permet de capturer la structure globale des distributions de couleurs



## ⚙️ Algorithmes testés

1. **OT exact (EMD)**  
   - Transport optimal classique  
   - Précis mais coûteux

2. **OT régularisé (Sinkhorn)**  
   - Version accélérée avec entropie  
   - Bon compromis vitesse / qualité

3. **Mapping barycentrique OT linéaire et gaussien**  
   - Applique le plan de transport aux pixels  
   - Permet une transformation directe des couleurs



## Métriques utilisées

- **Distance de Wasserstein (W2)**  
  → mesure principale du transport entre distributions de couleurs  

- **Divergence de Jensen-Shannon (JS)**  
  → similarité probabiliste entre histogrammes  

- **Statistiques globales (Lab)**  
  → **moyenne** (couleur dominante)  
  → **covariance** (dispersion / structure des couleurs)  

- **Évaluation qualitative (visuelle)**  
  → cohérence perceptuelle  
  → naturel du rendu  


## Résultats 

- Le modèle **gaussien (moyenne + covariance en Lab)** offre le meilleur compromis :
  - rapide
  - stable
  - visuellement satisfaisant

- Les méthodes **OT (EMD / Sinkhorn)** sont plus fidèles théoriquement,
  mais plus coûteuses et parfois moins stables.

---

  Projet réalisé dans le cadre de l'UE COMPUTATIONAL IMAGING @ IMT ATLANTIQUE

