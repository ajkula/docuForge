# docuForge
A tool to create/edit/export documents with image and charts integration of your own data from CSV/excel/JSON...

## Application home page
```mermaid
graph TD
    A[User opens DocuForge] --> B[Home Page]
    B --> C{User's choice}
    C -->|New document| D[Click 'New Document']
    C -->|Select existing document| E[Click on document in scrollable list]
    C -->|Search| F[Use search bar]
    C -->|Import external resource| G[Click 'Import External Resource']
    D --> H[New Document window]
    H --> I[Enter document name]
    I --> J[Choose template or start from scratch]
    J --> K[Click 'Create']
    K --> L[Open editing interface]
    E --> L
    F --> M[Filter document list]
    M --> N{Document found?}
    N -->|Yes| E
    N -->|No| O[Display 'No results found']
    G --> P[External Resource Import window]
    P --> Q[Select resource type]
    Q --> R[Choose file from file system]
    R --> S[Confirm import]
    S --> T[Resource added to DocuForge]
    L --> U[Main document interface]
```

## Document edition flow
```mermaid
graph TD
    A[Starting DocuForge] --> B[Main screen]
    B --> C{Select action}
    C -->|New document| D[Create new document]
    C -->|Open document| E[Select existing file]
    C -->|Recent documents| F[Recent documentslist]
    D --> G[Edition interface]
    E --> G
    F --> G
    G --> H{Edition actions}
    H -->|Hierarchical structure| I[titles/chapters Management]
    H -->|Layout creation| J[Rows creation/ajustement]
    H -->|Medias integration| K[Add images/charts]
    H -->|Chart integration| L[Data importation & config]
    I --> G
    J --> G
    K --> G
    L --> M[Chart type selection]
    M --> N[Charts configuration]
    N --> G
    G --> O{Global actions}
    O -->|Save| P[Local save]
    O -->|HTML Export| Q[HTML File generation]
    O -->|Exit| B
    P --> G
    Q --> G
```

## Chapters management flow
```mermaid
graph TD
    A[User accesses Document Structure] --> B[View Chapter List]
    B --> C{User Action}
    
    C -->|Add Chapter| D[Click '+ Add Chapter']
    D --> E[Enter Chapter Title]
    E --> F[Confirm]
    F --> B

    C -->|Add Subchapter| G[Click 'Add Subchapter']
    G --> H[Select Parent Chapter]
    H --> I[Enter Subchapter Title]
    I --> J[Confirm]
    J --> B

    C -->|Rename Chapter| K[Click 'Rename Chapter']
    K --> L[Select Chapter]
    L --> M[Enter New Title]
    M --> N[Confirm]
    N --> B

    C -->|Reorder Chapters| O[Click 'Reorder Chapters']
    O --> P[Drag and Drop Chapters]
    P --> Q[Confirm New Order]
    Q --> B

    C -->|Delete Chapter| R[Click Chapter Menu '⋮']
    R --> S[Select 'Delete']
    S --> T[Confirm Deletion]
    T --> B

    C -->|Edit Chapter Content| U[Click on Chapter]
    U --> V[Open Chapter Editor]

    B --> W[Return to Main Document]
```

## Chart insertion and configuration
```mermaid
graph TD
    A[Click 'Insert Chart'] --> B[Select Chart Type]
    B --> C[Upload Data Source]
    C --> D[Analyze Data Format]
    D --> E{Valid Format?}
    E -->|No| F[Error Message]
    F --> C
    E -->|Yes| G[Display Mapping Interface]
    G --> H[Map Data Attributes to Chart Properties]
    H --> I[Preview Chart]
    I --> J{Satisfied?}
    J -->|No| K[Make Adjustments]
    K --> H
    J -->|Yes| L[Confirm and Insert into Document]
    L --> M[Return to Document Editing]
```

**This flow outlines the step-by-step process a user follows when inserting a chart :**
- Initiate chart insertion
- Choose chart type
- Upload data
- Validate data format
- Map data to chart properties
- Preview and adjust as needed
- Confirm and insert into document

This intuitive process ensures users can easily create data visualizations that adhere to Edward Tufte's principles, enhancing the overall quality of their documents.

## Image insertion user flow

```mermaid
graph TD
    A[User clicks 'Insert Image' button] --> B{Choose upload method}
    B -->|Drag and Drop| C[User drags image into upload area]
    B -->|File Selection| D[User clicks to open file explorer]
    D --> E[User selects image file]
    C --> F[Image uploaded]
    E --> F
    F --> G[Image preview displayed]
    G --> H[User adjusts container width]
    H --> I[User selects image fit option]
    I --> J[User enters alt text]
    J --> K{User satisfied?}
    K -->|No| L[User makes adjustments]
    L --> H
    K -->|Yes| M[User clicks 'Insert' button]
    M --> N[Image inserted into document]
    N --> O[User returns to main document view]
```

## Components diagram
```mermaid
graph TD
    subgraph "Frontend (React + TypeScript)"
        A[UI Components]
        B[State Management]
        C[Chart Rendering D3.js/Recharts]
    end

    subgraph "Wails v2 Bridge"
        D[API Bindings]
    end

    subgraph "Backend (Go)"
        E[Business Logic]
        F[File System Operations]
        G[Data Processing]
        H[HTML Export]
    end

    subgraph "Data Storage"
        I[SQLite]
    end

    A <--> B
    B <--> C
    A <--> D
    B <--> D
    D <--> E
    E <--> F
    E <--> G
    E <--> H
    E <--> I
    G <--> I
```
**Components description**
1. Frontend (React + TypeScript)
  - UI Components: React components for the user interface
  - State Management: Handles local state with React Hooks and global state with Context API
  - Chart Rendering: Uses D3.js or Recharts for data visualization
2. Wails v2 Bridge
  - API Bindings: Facilitates communication between the frontend and backend
3. Backend (Go)
  - Business Logic: Handles core application logic
  - File System Operations: Manages reading and writing of files
  - Data Processing: Processes data for charts and document structure
  - HTML Export: Generates HTML output for documents
4. Data Storage
  - SQLite: Stores document data and application state

**Key interactions**
- The frontend communicates with the backend through the Wails v2 API bindings
- The backend handles all data processing and storage operations
- Chart rendering in the frontend uses processed data from the backend
- Document export is managed by the backend with input from the frontend

This architecture ensures a clear separation of concerns, with the frontend handling user interactions and presentation, while the backend manages data processing, storage, and core business logic.


## DocuForge UI Wireframe

**Home screen**
![DocuForge home screen](repo/docuforge-home-page-wireframe.svg)

**Document screen**
![DocuForge document screen Wireframe](repo/docuforge-main-wireframe.svg)

**Chapters management**
![DocuForge Chapters Management Interface](repo/chapter-management-wireframe.svg)

**Dataset to charts link view**
![DocuForge Chart Creation Interface](repo/docuforge-chart-creation-wireframe.svg)

**Document export view**
![DocuForge Export Wireframe](repo/docuforge-export-wireframe.svg)

**Image insertion view**
![DocuForge Image Insert Wireframe (Refined)](repo/docuforge-image-insert-wireframe.svg)