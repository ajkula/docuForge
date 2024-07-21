# docuForge
A tool to create/edit/export documents with image and charts integration of your own data from CSV/excel/JSON...

## User flow
graph TD
    A[Lancement de DocuForge] --> B[Écran principal]
    B --> C{Choix de l'action}
    C -->|Nouveau document| D[Création nouveau document]
    C -->|Ouvrir document| E[Sélection fichier existant]
    C -->|Documents récents| F[Liste documents récents]
    D --> G[Interface d'édition]
    E --> G
    F --> G
    G --> H{Actions d'édition}
    H -->|Structure hiérarchique| I[Gestion titres/chapitres]
    H -->|Mise en page| J[Création/ajustement rows]
    H -->|Intégration médias| K[Ajout images/graphiques]
    H -->|Création graphiques| L[Import et config données]
    I --> G
    J --> G
    K --> G
    L --> M[Sélection type graphique]
    M --> N[Configuration graphique]
    N --> G
    G --> O{Actions globales}
    O -->|Sauvegarder| P[Sauvegarde locale]
    O -->|Exporter HTML| Q[Génération fichier HTML]
    O -->|Fermer| B
    P --> G
    Q --> G
