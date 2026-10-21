# EER Lab — Generalization & Specialization Visualizer

**Live Website:** https://eerdemo-lab.netlify.app/

An interactive, browser-based learning platform for the Enhanced Entity-Relationship (EER) model — covering superclass/subclass hierarchies, generalization, specialization, inheritance, and constraints such as disjoint/overlapping and total/partial participation.

At its core is a live diagram visualizer: build an EER diagram manually or import existing tables and SQL to identify structures, then see the relational schema and SQL generated automatically. The platform also includes a structured learning path, worked examples, a practice question bank, AI-generated quizzes, and progress tracking.

**No installation or account required to use the deployed website.** Open the live website directly in your browser.

---

## Features

### 1. EER Diagram Visualizer
- Create entities and attributes and mark primary keys.
- Perform generalization and specialization.
- Configure disjoint/overlapping and total/partial constraints using standard EER notation.
- Generate relational schemas and SQL automatically.
- Choose from four relational mapping strategies.
- Undo/redo, auto-layout, pan/zoom, and export diagrams as PNG or SVG and SQL.

### 2. Table / SQL Import Workbench
- Paste table data, upload CSV files, or import SQL `CREATE TABLE` statements.
- Analyze column names and patterns to suggest entities, relationships, and possible generalization groupings.
- Review and confirm suggestions before generating diagram structures.

### 3. Student Profile
- Manage student profile information, including profile photo, register number, department, semester, and course details.
- Track learning progress, question accuracy, competitive scores, and milestones.

### 4. Contributors Page
- Dynamically manage student contributors, faculty mentors, and other contributors.
- Add, edit, delete, and reorder contributor records.
- Include photos, names, roles, register numbers, departments, and contributions.
- Store contributor records and photos locally using IndexedDB.

### 5. Learning Path and Progress Tracking
- Explore 30 curriculum modules, from ER fundamentals to advanced EER mapping.
- View progress cards grouped by module.
- Track topic-wise accuracy and learning completion.
- Access curated YouTube video lectures with click-to-play support and direct-link fallbacks.

### 6. Competitive Questions
- Practice GATE CS-style and university-level questions across 12 EER and DBMS topics.
- Filter questions by difficulty.
- Practice questions with +2M and +4M marking schemes.
- Access detailed, step-by-step solutions.
- Attempt timed tests.

### 7. Personal Performance Leaderboard
- Review assessment attempts and personal rankings.
- Compare scores, accuracy, and completion times.
- Clearly distinguish locally stored rankings from shared, server-based leaderboards.

### 8. Admin and Content Manager
- Add, edit, preview, and delete competitive questions.
- Preview student-facing question cards and answer keys.
- Import questions from JSON.
- Curate YouTube lectures and manage diagram images.
- Back up and restore application data using JSON.

### 9. AI-Powered ER/EER Diagram Recognition
- Upload an ER/EER diagram image for recognition.
- Extract entities, attributes, primary keys, explicitly marked foreign keys, relationships, cardinalities, participation constraints, and specialization structures.
- Review uncertain items and verify the extracted structure against the original image.
- Confirm the results before generating the final diagram.

*AI-powered diagram recognition requires the separately configured Python server and a valid Anthropic API key. It will not work on a static Netlify deployment unless the recognition API is hosted and configured separately.*

---

## Live Demo

Visit **https://eerdemo-lab.netlify.app/** to explore the application.

The deployed website provides the browser-based learning and visualization experience. Features that depend on a local Python server, external API credentials, or server-side processing require their corresponding services to be configured.

### Running Locally

The application can also be run locally using Python 3.

For the bundled server:

```bash
python3 server.py
```

Then open:

http://127.0.0.1:8000

For AI-powered diagram recognition, configure your Anthropic API key in a `.env` file alongside `server.py`, following `.env.example`.

Alternatively, serve the static application:

```bash
python3 -m http.server 8000
```

Then open:

http://127.0.0.1:8000

The static server supports browser-based features but does not provide the custom diagram-recognition API.

**Security note:** Never commit API keys or other secrets to GitHub. Keep `.env` private and use `.env.example` only as a template.

---

## Reading an ER/EER Diagram from an Image

1. Open **Table / SQL Import → ER diagram image**.
2. Upload an ER/EER diagram.
3. Allow the configured recognition service to analyze the image.
4. Review the extracted entities, attributes, keys, relationships, constraints, and uncertain items.
5. Compare the results against the original diagram.
6. Confirm the reviewed structure and generate the diagram.

The recognition server validates uploaded images, applies upload-size and rate limits, calls the configured vision model, and returns structured JSON. The API key remains on the server rather than being sent to the browser.

Recognition requires a running and correctly configured backend.

---

## Technology Stack

- **Frontend:** HTML, CSS, JavaScript
- **Data storage:** Browser IndexedDB and local storage
- **Data import:** CSV and SQL
- **Visualization:** Interactive EER diagrams and relational schema generation
- **AI integration:** Anthropic vision API through a Python server
- **Local server:** Python 3
- **Deployment:** Netlify

---

## Project Structure

```text
├── index.html                  # Bundled application
├── build.py                    # Build and concatenation script
├── server.py                   # Static server and recognition API
├── .env.example                # API key configuration template
├── README.md                   # Project documentation
├── 01_style.css                # Styling and design system
├── 02_core.js                  # Utilities, storage, and icons
├── 03_eer.js                   # EER visualizer and relational mapping
├── 04_import.js                # SQL/CSV import workbench
├── 04b_vision.js               # Image validation and recognition client
├── 05a_content.js              # Examples, questions, and video resources
├── 05b_topics.js               # Curriculum modules, part 1
├── 05c_topics.js               # Curriculum modules, part 2
├── 06_views1.js                # Dashboard and core navigation
├── 07_views2.js                # Visualizer, import, and learning views
├── 08_views3.js                # Profile, contributors, progress, admin
└── assets/
    └── contributors/            # Placeholder contributor images
```

---

## Rebuilding the Application

If you edit the modular source files, regenerate `index.html` by running:

```bash
python3 build.py
```

Commit and push the updated files to the connected GitHub repository to trigger a Netlify deployment, provided automatic deployments are enabled and your Netlify plan permits production deployments.

---

## Data Storage and Privacy

- Student profile information, progress, and contributor records may be stored locally in the browser.
- Local data is not automatically synchronized across different devices or browsers.
- A shared, multi-user leaderboard requires an appropriate server-side implementation.
- AI diagram recognition sends uploaded diagram images to the configured backend and external vision service for processing.

---

## Project Goal

EER Lab aims to make database design concepts easier to understand through interactive visualization, hands-on practice, automatic schema generation, and structured learning resources.

It bridges theoretical EER concepts with practical database design and SQL mapping, helping students learn by building, experimenting, and evaluating their understanding.

---

## License

Add your chosen license here if you intend to distribute the project for reuse. Until a license is specified, the repository's reuse permissions depend on applicable copyright law.

---

**Live Demo:** https://eerdemo-lab.netlify.app/  
**Repository:** https://github.com/shreedevi-s-28/dbms-project-works
