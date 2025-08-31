# M1V2: Installation and Core Commands

## 1. Introduction

**(Talking Points)**

*   Welcome back! In the last video, we saw how `uv` can streamline your development workflow. Now, it's time to get it running on your machine and learn the fundamental commands.
*   This video will walk you through the installation process on Windows, macOS, and Linux.
*   Then, we'll cover the essential commands you'll use every day: creating virtual environments and managing packages with the `uv pip` interface.

---

## 2. Installing `uv`

**(Talking Points)**

*   `uv` is distributed as a single binary, which makes installation incredibly simple.

*   **On macOS and Linux:** The recommended way is to use the standalone installer. Just run this command in your terminal.

    ```bash
    curl -LsSf https://astral.sh/uv/install.sh | sh
    ```

*   **On Windows:** You can use PowerShell.

    ```powershell
    irm https://astral.sh/uv/install.ps1 | iex
    ```

*   **Alternative Methods:** You can also install `uv` using package managers like `pipx` or Homebrew.

    ```bash
    # Using pipx
    pipx install uv

    # Using Homebrew
    brew install uv
    ```

*   To verify the installation, open a new terminal and run:

    ```bash
    uv --version
    ```

---

## 3. Creating Virtual Environments with `uv venv`

**(Talking Points)**

*   The first step in any Python project is creating an isolated environment. With `uv`, this is handled by the `uv venv` command.
*   It's a direct, high-speed replacement for `python -m venv`.

*   **Usage:**

    ```bash
    # Create a virtual environment named .venv
    uv venv

    # You can also specify a name
    uv venv my-env
    ```

*   `uv` can also create an environment with a specific Python version if you have it installed.

    ```bash
    # Use a specific Python interpreter
    uv venv -p python3.11
    ```

*   After creating the environment, you can activate it just like you normally would.

    ```bash
    # On macOS/Linux
    source .venv/bin/activate

    # On Windows
    .venv\Scripts\activate
    ```

---

## 4. The `uv pip` Interface

**(Talking Points)**

*   `uv` provides a `pip` command that acts as a super-fast, drop-in replacement for the `pip` you already know.
*   Let's explore the most common subcommands.

*   **`uv pip install`:** Install packages into your environment.

    ```bash
    # Install a single package
    uv pip install requests

    # Install multiple packages
    uv pip install "fastapi[all]" httpx

    # Install from a requirements.txt file
    uv pip install -r requirements.txt
    ```

*   **`uv pip list`:** See what's installed in your environment.

    ```bash
    uv pip list
    ```

*   **`uv pip freeze`:** Generate a `requirements.txt` file from the current environment.

    ```bash
    uv pip freeze > requirements.txt
    ```

*   **`uv pip uninstall`:** Remove packages.

    ```bash
    uv pip uninstall requests
    ```

---

## 5. Conclusion

**(Talking Points)**

*   You now have `uv` installed and are equipped with the core commands for managing virtual environments and packages.
*   You can already replace your `venv` and `pip` workflows with `uv venv` and `uv pip` for a significant speed boost.
*   In the next module, we'll go beyond the `pip` interface and explore `uv`'s powerful project management features, centered around `pyproject.toml`.
*   Thanks for watching!
