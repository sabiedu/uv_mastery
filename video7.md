# M4V1: Developing a FastAPI Application with `uv`

## 1. Introduction

**(Talking Points)**

*   Welcome to our final module, `uv` in Practice. We've covered the theory, the commands, and the workflows. Now, let's put it all together to build a real-world application.
*   In this video, we'll build a complete web application using FastAPI, with `uv` managing our entire development workflow from start to finish.
*   This will demonstrate how seamlessly `uv` integrates into a modern web development stack, making the process faster and more efficient.

---

## 2. Scaffolding the FastAPI Project

**(Talking Points)**

*   Every great project starts with a solid foundation. We'll use `uv init` to create a project specifically for an application.

*   **Step 1: Create the project.**

    ```bash
    mkdir my-fastapi-project
    cd my-fastapi-project

    # Initialize an application project
    uv init --app
    ```

*   This command gives us a clean `pyproject.toml` and a virtual environment, the perfect starting point for our web app.

---

## 3. Adding Dependencies

**(Talking Points)**

*   A web application needs a few key dependencies: the framework itself (`fastapi`) and a server to run it (`uvicorn`).
*   We'll use `uv add` to manage them. We'll also install `uvicorn` with its `standard` extras for better performance.

    ```bash
    uv add fastapi "uvicorn[standard]"
    ```

*   As we saw in Module 2, this single command updates `pyproject.toml`, resolves the dependencies into `uv.lock`, and installs them into our `.venv`. Everything is in sync.

---

## 4. Creating the Application Code

**(Talking Points)**

*   Now for the fun part: writing the code. We'll create a simple API with a few endpoints.
*   For a good project structure, let's create our application code inside a dedicated directory.

*   **Step 1: Create the application directory and files.**

    ```bash
    mkdir app
    touch app/__init__.py
    touch app/main.py
    ```

*   **Step 2: Write the application logic in `app/main.py`.**

    ```python
    from fastapi import FastAPI

    app = FastAPI(title="My `uv` Project")

    @app.get("/")
    def read_root():
        """Returns a welcome message."""
        return {"message": "Welcome to the `uv`-powered FastAPI app!"}

    @app.get("/items/{item_id}")
    def read_item(item_id: int, q: str | None = None):
        """Returns an item by ID, with an optional query parameter."""
        return {"item_id": item_id, "q": q}
    ```

---

## 5. Running the Development Server

**(Talking Points)**

*   This is where `uv`'s workflow really shines. We don't need to activate the virtual environment. We can use `uv run` to execute commands directly within the project's managed environment.
*   The `--reload` flag is essential for development, as it tells `uvicorn` to automatically restart the server whenever we change our code.

    ```bash
    uv run uvicorn app.main:app --reload
    ```

*   Now, you can open your browser to `http://127.0.0.1:8000` to see your app live, and `http://127.0.0.1:8000/docs` to see the interactive API documentation that FastAPI generates.
*   The workflow is simple: make a code change, save the file, and the server reloads instantly. `uv` stays out of your way and lets you focus on building.

---

## 6. Conclusion

**(Talking Points)**

*   We've successfully built and run a complete web application using `uv` to manage the entire process.
*   We saw how `uv init` creates the perfect project structure and how `uv add` and `uv run` create a fast, seamless development loop.
*   This workflow demonstrates how `uv` isn't just for library authors—it's a powerful tool for application developers as well.
*   In our final video, we'll tackle another common, real-world scenario: migrating an existing project from a traditional `pip` and `requirements.txt` setup over to `uv`.
*   Thanks for watching!
