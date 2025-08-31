# YouTube Course: Mastering Python Development with `uv`

## Course Description
A comprehensive YouTube series designed to get Python developers up and running with `uv`. This course covers everything from basic dependency management to building and publishing your own packages, and integrating `uv` into modern web development workflows with frameworks like FastAPI.

---

## Module 1: Introduction to `uv`

*   **Video 1: What is `uv` and Why Should You Use It?**
    *   **Goal:** Introduce `uv` and its value proposition.
    *   **Topics:**
        *   Common pain points in Python development (`pip`, `venv`, `pip-tools`).
        *   Introducing `uv` as a single, high-performance tool for managing and building projects.
        *   Core features: speed, dependency resolution, and project management.
        *   Quick demo: `uv run` with a FastAPI application.

*   **Video 2: Installation and Core Commands**
    *   **Goal:** Install `uv` and learn the essential commands for daily use.
    *   **Topics:**
        *   Installation on macOS, Linux, and Windows.
        *   Creating virtual environments with `uv venv`.
        *   A tour of the `uv pip` interface: `install`, `list`, `freeze`, `uninstall`.

---

## Module 2: Managing Dependencies

*   **Video 1: The `uv` Project Model**
    *   **Goal:** Understand how `uv` manages project dependencies through `pyproject.toml`.
    *   **Topics:**
        *   Adding and removing dependencies with `uv add` and `uv remove`.
        *   Locking and syncing your environment with `uv lock` and `uv sync`.
        *   Visualizing dependencies with `uv tree`.
        *   Exporting lockfiles with `uv export`.

*   **Video 2: Advanced Dependency Management**
    *   **Goal:** Explore advanced features for handling complex dependency scenarios.
    *   **Topics:**
        *   Managing dependency groups (e.g., `dev`, `docs`).
        *   Editable installs for local development (`uv add -e .`).
        *   Understanding and managing the `uv` cache (`uv cache clean`, `uv cache prune`).

---

## Module 3: Building Projects with `uv`

*   **Video 1: Scaffolding Projects with `uv init`**
    *   **Goal:** Learn to create different types of projects from scratch.
    *   **Topics:**
        *   A deep dive into `uv init`.
        *   Creating a simple application (`--app`).
        *   Creating a reusable library (`--lib`).
        *   Setting up a project for packaging (`--package`).

*   **Video 2: Building and Publishing Packages**
    *   **Goal:** Build a Python package and publish it to an index.
    *   **Topics:**
        *   Configuring the build backend in `pyproject.toml`.
        *   Building source distributions and wheels with `uv build`.
        *   Publishing your package with `uv publish`.

---

## Module 4: `uv` in Practice

*   **Video 1: Developing a FastAPI Application with `uv`**
    *   **Goal:** Build a complete web application using `uv` for project and dependency management.
    *   **Topics:**
        *   Setting up a FastAPI project from scratch with `uv init --app`.
        *   Managing dependencies like `fastapi` and `uvicorn`.
        *   Using `uv run` to serve the application.
        *   Structuring a web application for production.

*   **Video 2: Migrating from `pip` to `uv`**
    *   **Goal:** Learn to migrate an existing project from a `pip` and `requirements.txt` workflow.
    *   **Topics:**
        *   Importing dependencies from `requirements.in`.
        *   Preserving locked versions from `requirements.txt` using constraints.
        *   Handling development and optional dependency groups during migration.
