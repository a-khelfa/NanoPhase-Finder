# NanoPhase-Finder
# Analyse de Données EELS-SPIM par Machine Learning

Ce projet présente un pipeline complet en Python pour le traitement et l'analyse de données de spectroscopie de perte d'énergie d'électrons (EELS) acquises en mode image-spectre (SPIM). Le flux de travail utilise des techniques de machine learning non supervisé pour extraire, visualiser et segmenter les différentes phases ou états chimiques présents dans les données.

Le notebook Jupyter (`spim_t8_6026-6226_processing_github.ipynb`) guide l'utilisateur à travers chaque étape, du prétraitement des données brutes à la visualisation finale des clusters et de leurs spectres caractéristiques.

---

## 🔬 Flux de Travail de l'Analyse

Le processus d'analyse est divisé en plusieurs étapes clés :

1.  **Prétraitement des Données**
    * Chargement des données au format `.dm4`.
    * Correction des artefacts instrumentaux, notamment les "spikes" aux jonctions des détecteurs TIMEPIX, en réduisant l'intensité sur les canaux concernés.

2.  **Analyse en Composantes Principales (PCA)**
    * Application de la PCA pour réduire le bruit et la dimensionnalité des données.
    * Visualisation du *scree plot* pour déterminer le nombre optimal de composantes à conserver.
    * Reconstruction des données en utilisant uniquement les composantes les plus significatives.

3.  **Déconvolution de Richardson-Lucy (RLC)**
    * Amélioration de la résolution énergétique des spectres par déconvolution avec un spectre de pic de non-perte d'énergie (ZLP) de référence.

4.  **Réduction de Dimensionnalité avec UMAP**
    * Normalisation des spectres pour corriger les variations d'épaisseur de l'échantillon.
    * Application de l'algorithme UMAP (Uniform Manifold Approximation and Projection) pour projeter les données de haute dimension dans un espace 2D, facilitant ainsi la visualisation des regroupements de spectres similaires.

5.  **Clustering et Analyse des Spectres**
    * Segmentation des points dans l'espace UMAP à l'aide de l'algorithme **K-Means**.
    * (Optionnel) Raffinement des frontières des clusters à l'aide d'un classificateur **SVM (Support Vector Machine)**.
    * Visualisation des résultats sous forme de :
        * Projection UMAP colorée par cluster.
        * Carte spatiale montrant la distribution des clusters dans l'image.
        * Spectres moyens normalisés pour chaque cluster, permettant une interprétation physique.

---

## 🚀 Comment Utiliser

1.  **Cloner le dépôt :**
    ```bash
    git clone [https://votre-lien-vers-le-depot.git](https://votre-lien-vers-le-depot.git)
    cd nom-du-dossier
    ```

2.  **Installer les dépendances :**
    Assurez-vous d'avoir un environnement Python (par exemple, via Anaconda/Miniconda). Installez les bibliothèques nécessaires :
    ```bash
    pip install hyperspy numpy matplotlib scikit-learn umap-learn tqdm
    ```

3.  **Configurer le Notebook :**
    * Ouvrez le fichier `.ipynb` dans Jupyter Lab ou Jupyter Notebook.
    * Placez vos fichiers de données (`.dm4`) dans le même répertoire ou mettez à jour les chemins dans la cellule **"Paramètres de l'analyse"**.
    * Ajustez les paramètres (nombre de composantes PCA, nombre de clusters, etc.) selon les besoins de votre analyse.

4.  **Exécuter les cellules :**
    Exécutez les cellules du notebook dans l'ordre pour effectuer l'analyse complète.

---

## 📦 Dépendances Principales

* [HyperSpy](https://hyperspy.org/)
* [NumPy](https://numpy.org/)
* [Scikit-learn](https://scikit-learn.org/)
* [UMAP](https://umap-learn.readthedocs.io/)
* [Matplotlib](https://matplotlib.org/)
* [Tqdm](https://tqdm.github.io/)
