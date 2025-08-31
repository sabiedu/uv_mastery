# M2V1: The `uv` Project Model

## 1. Introduction

**(Talking Points)**

*   Welcome to Module 2! In the last module, we treated `uv` as a fast replacement for `pip` and `venv`. Now, we're going to unlock its true potential as a complete project and dependency manager.
*   This is where `uv` moves beyond being just a tool and becomes the backbone of your development workflow.
*   We'll focus on the `pyproject.toml` file and the commands that interact with it: `add`, `remove`, `lock`, `sync`, `tree`, and `export`.

---

## 2. From `pip` to Project

**(Talking Points)**

*   While `uv pip` is great, it's an imperative approach—you tell it what to do, and it does it. A project-based workflow is declarative—you declare what you need, and `uv` makes it happen.
*   The center of this workflow is the `pyproject.toml` file. Let's initialize a project to see it in action.

    ```bash
    # Create a new project directory
    mkdir my-uv-project
    cd my-uv-project

    # Initialize the project
    uv init
    ```

*   This creates a `pyproject.toml` and a `.venv`. The `pyproject.toml` is now the single source of truth for your project's dependencies.

---

## 3. Adding and Removing Dependencies

**(Talking Points)**

*   The `uv add` command is the primary way to add a new dependency. It's much more than just an install command.

    ```bash
    uv add "requests<3"
    ```

*   When you run `uv add`, three things happen automatically:
    1.  The `dependencies` list in `pyproject.toml` is updated.
    2.  The dependency tree is resolved, and `uv.lock` is created or updated.
    3.  The package is installed into your virtual environment.

*   Removing a package is just as easy with `uv remove`.

    ```bash
    uv remove requests
    ```

*   This automatically removes the package from your environment, `uv.lock`, and `pyproject.toml`.

---

## 4. Locking and Syncing

**(Talking Points)**

*   The `uv.lock` file is the key to reproducible builds. It contains the exact versions of every package in your dependency tree.
*   While `uv add` and `uv remove` update the lockfile automatically, you can also manage it manually.
*   If you edit `pyproject.toml` directly, you can run `uv lock` to regenerate the lockfile.

    ```bash
    # (After manually adding a dependency to pyproject.toml)
    uv lock
    ```

*   The `uv sync` command ensures your virtual environment exactly matches the `uv.lock` file. It will add missing packages and remove any that don't belong. This is the command you'd use in CI/CD or when a new developer joins the project.

    ```bash
    # Sync the environment with the lockfile
    uv sync
    ```

---

## 5. Visualizing and Exporting

**(Talking Points)**

*   As your project grows, understanding your dependency tree becomes crucial. `uv tree` gives you a clear visualization.

    ```bash
    uv tree
    ```

*   If you need to share your locked dependencies with someone who isn't using `uv`, you can export your lockfile to a `requirements.txt` format.

    ```bash
    uv export > requirements.txt
    ```

---

## 6. Conclusion

**(Talking Points)**

*   You've now learned the core of `uv`'s project management workflow. By using `add`, `remove`, `lock`, and `sync`, you can maintain a clean, reproducible, and declarative project setup.
*   In the next video, we'll dive into advanced dependency management, including how to handle different groups of dependencies for testing and documentation, and how to work with local, editable packages.
*   Thanks for watching!
