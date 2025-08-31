# M3V1: Scaffolding Projects with `uv init`

## 1. Introduction

**(Talking Points)**

*   Welcome to Module 3! So far, we've focused on how `uv` helps you manage dependencies for existing projects. Now, we're shifting gears to see how `uv` can help you create projects from scratch.
*   In this video, we'll do a deep dive into the `uv init` command. This powerful command is your starting point for any new Python project, whether it's a simple script, a web application, or a reusable library you intend to publish.
*   We'll explore the different project templates `uv` offers and learn how to scaffold a robust project structure in seconds.

---

## 2. A Deep Dive into `uv init`

**(Talking Points)**

*   The `uv init` command bootstraps a new Python project. At its simplest, it creates a `pyproject.toml` and a virtual environment, but it can do much more.
*   It uses a series of flags to configure the project template. Let's look at the most important ones.

*   **`--app`**: Creates a project for an application. This is a good default for most projects that aren't meant to be imported by others, like a web app or a data analysis script.

*   **`--lib`**: Creates a project for a library. This sets up a `src` layout, which is the standard for modern Python packages.

*   **`--package`**: Can be used with `--lib` or `--app` to configure a build backend, making the project ready to be built into a wheel.

*   Let's see these in action.

---

## 3. Creating a Simple Application (`--app`)

**(Talking Points)**

*   Let's start with the most common use case: a standalone application. We'll create a simple script that uses the `requests` library.

    ```bash
    # Create and navigate to a new directory
    mkdir my-app
    cd my-app

    # Initialize an application project
    uv init --app
    ```

*   This gives us a `pyproject.toml` and a `.venv`. The structure is flat, which is perfect for an application.
*   We can add dependencies and a `main.py` file, and we're ready to go.

    ```bash
    uv add requests
    ```

    *Create `main.py`:*
    ```python
    import requests

    def main():
        response = requests.get("https://www.astral.sh")
        print(f"Request to astral.sh returned status: {response.status_code}")

    if __name__ == "__main__":
        main()
    ```

    *Run it:*
    ```bash
    uv run python main.py
    ```

---

## 4. Creating a Reusable Library (`--lib`)

**(Talking Points)**

*   Now, let's create a project that's meant to be imported by other projects—a library.

    ```bash
    # Go back to the parent directory
    cd ..

    # Create and navigate to a new directory
    mkdir my-lib
    cd my-lib

    # Initialize a library project
    uv init --lib
    ```

*   Notice the difference in the file structure. `uv` has created a `src` directory. Inside `src`, there's another directory named `my_lib`. This is where your library's code lives.
*   This `src` layout is a best practice that prevents many common import-related issues.

---

## 5. Setting Up a Project for Packaging (`--package`)

**(Talking Points)**

*   Our library is structured correctly, but it's not yet ready to be built into a distributable package (a wheel). We need to configure a build backend.
*   The `--package` flag, used with `uv init`, does this for us. It adds the necessary `[build-system]` table to `pyproject.toml`.

    ```bash
    # Let's create another library, this time ready for packaging
    cd ..
    mkdir my-package
    cd my-package

    # Initialize a library that is also a package
    uv init --lib --package
    ```

*   If you inspect the `pyproject.toml`, you'll see a new section:

    ```toml
    [build-system]
    requires = ["hatchling"]
    build-backend = "hatchling.build"
    ```

*   By default, `uv` uses Hatchling, but you can specify others like Setuptools or Flit. This project is now ready for the `uv build` command, which we'll cover in the next video.

---

## 6. Conclusion

**(Talking Points)**

*   You now know how to use `uv init` to scaffold different types of Python projects, from simple applications to build-ready libraries.
*   Using these templates from the start ensures your project follows modern best practices and saves you significant setup time.
*   In the next video, we'll take the package we just created and learn how to build it into a wheel and publish it for the world to use with `uv build` and `uv publish`.
*   Thanks for watching!
