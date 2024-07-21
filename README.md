# docuForge
A tool to create/edit/export documents with image and charts integration of your own data from CSV/excel/JSON...

## User flow
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

## Chart Insertion and Configuration
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

## Component Diagram
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
**Component Description**
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

**Key Interactions**
- The frontend communicates with the backend through the Wails v2 API bindings
- The backend handles all data processing and storage operations
- Chart rendering in the frontend uses processed data from the backend
- Document export is managed by the backend with input from the frontend

This architecture ensures a clear separation of concerns, with the frontend handling user interactions and presentation, while the backend manages data processing, storage, and core business logic.


## DocuForge UI Wireframe

**Main screen**
![DocuForge Main screen Wireframe](repo/docuforge-main-wireframe.svg)

**Dataset to charts link settings**
![DocuForge Optimized Chart Creation Interface](repo/docuforge-optimized-chart-creation-wireframe.svg)