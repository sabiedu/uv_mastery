# M2V2: Advanced Dependency Management

## 1. Introduction

**(Talking Points)**

*   Welcome back! Now that you've mastered the basic project workflow, it's time to explore some of `uv`'s more advanced features for handling complex dependency scenarios.
*   In this video, we'll cover three key topics: how to manage different groups of dependencies for things like testing and documentation, how to set up editable installs for local package development, and how to manage `uv`'s global cache.

---

## 2. Managing Dependency Groups

**(Talking Points)**

*   Most projects have more than just production dependencies. You have tools for testing, building documentation, or linting. `uv` allows you to manage these in separate groups within your `pyproject.toml`.
*   The most common group is `dev`. You can add a dependency to this group using the `--dev` flag.

    ```bash
    # Add pytest to the [tool.uv.dev-dependencies] group
    uv add pytest --dev
    ```

*   You can also create your own custom groups with the `--group` flag.

    ```bash
    # Add Sphinx to a 'docs' group
    uv add sphinx --group docs
    ```

*   When you run `uv sync` or `uv pip install`, by default, it only installs the main dependencies. To include optional groups, you use the `--with` flag.

    ```bash
    # Install main and dev dependencies
    uv sync --with dev

    # Install main, dev, and docs dependencies
    uv sync --with dev,docs
    ```

*   This system allows you to keep your production environment lean while easily pulling in the tools you need for development.

---

## 3. Editable Installs

**(Talking Points)**

*   What if you're developing a package and want to test it in another project without having to publish it first? This is where editable installs come in.
*   An editable install creates a link to your package's source code, so any changes you make are immediately reflected in the environment.
*   You can add a local package in editable mode using the `-e` flag, similar to `pip`.

    ```bash
    # Assuming you have a local package in a 'my-local-package' directory
    uv add -e ./my-local-package
    ```

*   This is incredibly useful for monorepo setups or when you're working on a library and an application that uses it simultaneously.

---

## 4. Understanding and Managing the `uv` Cache

**(Talking Points)**

*   One of the secrets to `uv`'s incredible speed is its intelligent global cache.
*   Whenever `uv` downloads a package wheel or builds a distribution, it stores the result in a central cache directory. The next time any project on your system needs that same package, `uv` can grab it from the cache instantly instead of re-downloading or re-building it.
*   You can locate the cache directory by running:

    ```bash
    uv cache dir
    ```

*   While you usually don't need to touch the cache, `uv` provides commands to manage it.
*   `uv cache clean` will remove all cached data.

    ```bash
    # Clear the entire cache
    uv cache clean
    ```

*   `uv cache prune` is a safer command that removes only old, likely unused packages, helping you reclaim disk space without slowing down your active projects.

    ```bash
    uv cache prune
    ```

---

## 5. Conclusion

**(Talking Points)**

*   You're now equipped with some of `uv`'s most powerful features for managing complex projects.
*   You can organize your dependencies into logical groups, work seamlessly with local packages, and understand how `uv` uses its cache to deliver amazing performance.
*   In the next module, we'll shift our focus from consuming packages to creating them. We'll dive deep into `uv init`, `uv build`, and `uv publish` to scaffold, build, and distribute your own Python packages.
*   Thanks for watching!
