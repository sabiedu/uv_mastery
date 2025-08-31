# M3V2: Building and Publishing Packages

## 1. Introduction

**(Talking Points)**

*   Welcome back! In the last video, we used `uv init --lib --package` to scaffold a Python library that's ready to be built. Now, it's time to take that final step.
*   This video will show you how to turn your source code into a distributable package—a wheel—that others can install.
*   We'll cover the `uv build` command to create the package and the `uv publish` command to upload it to a package index like PyPI for the world to use.

---

## 2. Reviewing the Project Setup

**(Talking Points)**

*   Let's quickly revisit the project we created in the last video.

    ```bash
    # (Navigate to the 'my-package' directory)
    ls -R
    ```

*   We have our code in the `src/my_package` directory and a `pyproject.toml` file.
*   The key part that makes our project buildable is the `[build-system]` table in `pyproject.toml`.

    ```toml
    [build-system]
    requires = ["hatchling"]
    build-backend = "hatchling.build"
    ```

*   This tells `uv` (and other build tools) to use the `hatchling` backend to build the project. `uv` defaults to Hatch, but supports other backends like Setuptools, Flit, and PDM.

---

## 3. Building Your Package with `uv build`

**(Talking Points)**

*   The `uv build` command is a standards-compliant builder that takes your source code and packages it into two standard formats:
    *   **Source Distribution (`sdist`)**: A `.tar.gz` file containing your source code. It allows users to build the package on their own machine.
    *   **Wheel (`.whl`)**: A pre-built distribution. This is what `pip` and `uv` prefer to install because it's faster and doesn't require a build step on the user's machine.

*   Let's build our package. It's as simple as running one command from the project root.

    ```bash
    uv build
    ```

*   `uv` will create a `dist` directory. Let's look inside.

    ```bash
    ls dist
    ```

*   You'll see two files: `my_package-0.1.0.tar.gz` (the sdist) and `my_package-0.1.0-py3-none-any.whl` (the wheel). Your project is now officially packaged!

---

## 4. Publishing Your Package with `uv publish`

**(Talking Points)**

*   Building is great, but how do you share your package with others? You publish it to a package index. The most common one is the Python Package Index, or PyPI.
*   The `uv publish` command handles this for you.

*   **Important Prerequisite:** To publish to PyPI, you need an account and an API token. For this demo, we'll use **TestPyPI**, a separate index for testing. This is a critical best practice—never upload test packages to the real PyPI.

*   Once you have your TestPyPI token, you can set it as an environment variable.

    ```bash
    # On macOS/Linux
    export UV_TEST_PYPI_TOKEN="your-token-here"

    # On Windows
    $env:UV_TEST_PYPI_TOKEN="your-token-here"
    ```

*   Now, you can publish. The `--repository-url` flag tells `uv` to use TestPyPI instead of the real one.

    ```bash
    # Publish the wheel and sdist from the 'dist' directory
    uv publish --repository-url https://test.pypi.org/legacy/
    ```

*   And that's it! Your package is now live on TestPyPI and can be installed by anyone.

    ```bash
    # Example of how someone could install it
    uv pip install --index-url https://test.pypi.org/simple/ my-package
    ```

---

## 5. Conclusion

**(Talking Points)**

*   In this video, you learned how to complete the package lifecycle with `uv`.
*   You used `uv build` to create standard Python distributions and `uv publish` to share your work on a package index.
*   This completes our module on building projects. You now have the skills to both consume and produce Python packages using `uv`.
*   In our final module, we'll look at two practical, real-world scenarios: building a complete web application with FastAPI and migrating an existing `pip`-based project to `uv`.
*   Thanks for watching!
