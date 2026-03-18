# ✍️ Writing Documentation

To maintain a consistent and professional look across all **CodeHive** projects, please adhere to the following directory structure and formatting standards.

## 🏗️ Project Directory Structure
Each project must reside in its own folder under `docs/projects/`. Follow this exact layout:

```text
docs/projects/[project-name]/
├── assets/             # All images, diagrams, and screenshots
├── pages/              # Deep-dive documentation pages
│   └── [page-name].md
├── index.md            # Project Intro & Getting Started
└── setup.md            # Environment & Infrastructure (Optional)
```

### **File Descriptions**
1.  **`index.md`**: The landing page for the project. Should include the project's purpose, the lead members, and a "Quick Start" guide.
2.  **`setup.md`**: Technical details regarding the environment (e.g., Docker configs, M4 Mac Mini specs, required Python version via `uv`).
3.  **`pages/`**: Any documentation that doesn't fit in the index or setup goes here (e.g., `alu-logic.md`, `api-endpoints.md`).
4.  **`assets/`**: Always store project-specific images here. Link them using:
    `![Alt Text](../../assets/[project-name]/image.png)`

## 📖 Formatting Standards
We use **Material for MkDocs**. Refer to the [Official Reference](https://squidfunk.github.io/mkdocs-material/reference/) for advanced components like tabs, buttons, or math.

### **1. Code Blocks**
Always specify the language for syntax highlighting.
- **Example:**

    ```yaml
    services:
      mc-server:
        image: itzg/minecraft-server
    ```

### **2. Admonitions**
Use these for callouts, tips, or warnings:
```markdown
!!! info "Pro Tip"
    When building with Redstone, use `Carpet Mod` to freeze the tick rate for frame-perfect debugging.
```

## 🚀 Navigation & mkdocs.yml
When you add a new file or project, you **must** update the `nav` section in the root `mkdocs.yml`. Use capitalized titles for the navigation labels.

**Standard Navigation Template:**
```yaml
nav:
  - Projects:
      - [Project Name]:
          - Overview: projects/[project-name]/index.md
          - Setup: projects/[project-name]/setup.md
          - [Specific Page Name]: projects/[project-name]/pages/[file].md
```
