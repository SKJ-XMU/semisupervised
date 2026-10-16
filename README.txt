README

Project overview
----------------
These notebooks implement a benchmark-guided clustering workflow for screening candidate phosphor host materials. The workflow is designed to organize a large candidate space, identify regions enriched with reference phosphors, and progressively reduce the number of candidates for further evaluation.

Main functions
--------------
1. Data preprocessing and dimensionality reduction
   - Material descriptors are preprocessed and transformed using principal component analysis (PCA).
   - Different retained-variance settings are used to construct feature spaces with different levels of retained information.

2. Unsupervised clustering
   - Multiple clustering algorithms are tested, including:
     K-means, Gaussian Mixture Model (GMM), DBSCAN, BIRCH, Ward hierarchical clustering, Mean Shift, and Spectral Clustering.
   - The distributions of 15 benchmark phosphors are used to identify target-enriched clusters and guide candidate screening.

3. Narrow-band and Debye-temperature screening
   - Separate clustering analyses are used to assist screening toward narrow-band emission and relatively high Debye temperature.
   - The benchmark materials provide property-guided reference information for selecting relevant clustering regions.
   - The clustering models are used for candidate screening and prioritization rather than direct numerical prediction of FWHM or Debye temperature.

4. Benchmark pairwise-distance analysis
   - Euclidean distances among the 15 benchmark materials are calculated in the corresponding PCA representation space.
   - A total of 105 unique benchmark pairs are generated.
   - The normalized feature-space distances can be compared with pairwise differences in FWHM or Debye temperature to examine whether materials with similar properties tend to occupy nearby regions of the feature space.

5. Random-Forest surrogate and SHAP analysis
   - A Random Forest classifier is trained as a surrogate model to reproduce clustering-derived labels.
   - Stratified cross-validation is used to evaluate the fidelity of the surrogate classifier using metrics such as accuracy, macro-F1 score, and balanced accuracy.
   - SHAP is then used to analyze feature contributions associated with the surrogate-model assignment to clustering-derived regions.
   - This analysis explains the surrogate classification behavior and should not be interpreted as direct prediction of physical properties or proof of intrinsic physical mechanisms.

Typical outputs
---------------
The notebooks may generate:
- Cluster labels and screened candidate lists
- PCA representations and loading matrices
- Cluster statistics
- Benchmark pairwise Euclidean-distance tables
- Normalized distance matrices
- FWHM or Debye-temperature pairwise-difference tables
- Random-Forest surrogate fidelity metrics
- SHAP summary and force plots
- Excel files and figures used for subsequent analysis

Notes
-----
- Input file paths may need to be updated before running the notebooks.
- Run notebook cells in order unless otherwise specified.
- Some notebooks correspond to different clustering algorithms or different screening stages.
- The 15 benchmark phosphors are used as reference materials to guide the screening process; they are not treated as interchangeable supervised-learning positive samples.
- Exact software/package versions should be recorded in the accompanying requirements.txt or environment file for reproducibility.
