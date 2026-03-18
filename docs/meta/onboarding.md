# 📥 Onboarding & Contribution

Welcome to **CodeHive**. To maintain a high standard of technical documentation, we use a tiered contribution system based on your role and experience level.

## 🛠️ Environment Setup
All members contributing to the documentation must use [`uv`](https://docs.astral.sh/uv/) for fast, reliable Python dependency management.

1.  **Install uv:** Follow the [official installation guide](https://docs.astral.sh/uv/getting-started/installation/).
2.  **Clone the Repo:** ```bash
    git clone [https://github.com/codehive/project-docs.git](https://github.com/codehive/project-docs.git)
    ```
3.  **Sync Environment:** Navigate to the project folder and run:
    ```bash
    uv sync
    ```
    *This will automatically create a `.venv` and install MkDocs with all required plugins based on the `uv.lock` file.*

---

## 🛰️ How to Contribute

### **Level 1: Novice (General Members)**
If you are new to Git or documentation, you can still contribute content:
* **The Workflow:** Draft your project updates, technical specs, or logs in Markdown format.
* **Submission:** Send your `.md` files or raw text to the **Documentation Moderators** via the designated Discord channel. They will review, format, and upload the content for you.

### **Level 2: Advanced (Moderators)**
For members comfortable with version control, use the **Pull Method**:
1.  **Sync:** Ensure your local environment is up to date with `uv sync`.
2.  **Preview:** Run `uv run mkdocs serve` to see changes in real-time at `http://localhost:8000`.
3.  **Branch:** Create a new feature branch for your edits.
4.  **PR:** Submit a **Pull Request** on GitHub. A Lead Moderator will review and merge your changes.

### **Level 3: Privileged (Leads/Admin)**
Members of the **CodeHive GitHub Organization** with write access can use the **Push Method**:
* **The Workflow:** Direct push to the `main` branch is permitted for minor updates, configuration changes, or urgent documentation fixes.
* **Requirement:** Ensure `uv run mkdocs serve` passes without errors before pushing.

---