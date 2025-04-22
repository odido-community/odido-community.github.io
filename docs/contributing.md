# Contributing

## How to Contribute

We welcome your contributions! To get started, please follow these steps:

1. Fork the Repository
    - Click on the `Fork` button at the top-right of the repository page to create your own copy.

2. Create a New Branch
    - Once you have your fork, create a new branch to work on. Name it something descriptive of the changes you're making.

For example:

```bash
git checkout -b fix/typo-in-readme
```

3. Make Your Changes
Make changes to the documentation. Use mkdocs serve to preview the site locally.

4. Commit Your Changes
After making your changes, commit them with a clear message explaining what you did.
```bash
git add .
git commit -m "Fix typo in README"
```

5. Push Your Changes
Push your changes to your forked repository:
```bash
git push origin fix/typo-in-readme
```
6. Open a Pull Request
- Go to your fork on GitHub.
- Click the `Compare & Pull Request` button.
- Add a description of what changes you made and why they are needed.
- Select the main branch of the original repository as the base branch.
- Click `Create Pull Request`.

## PR Guidelines

- Ensure your changes are well-documented and well-tested (if applicable).
- Write clear, descriptive commit messages.
- If you're adding new features, explain why they are useful.
- If you're fixing a bug, provide a clear explanation of the problem and how you solved it.
- If you’re making significant changes, include relevant screenshots or demos in your PR description.

## Dev Container
This project supports [Dev Containers](https://containers.dev/) for a smooth and consistent development experience across environments. Whether you're using **GitHub Codespaces** or **VS Code with the Dev Containers extension**, you're good to go.



## Getting Started

### Open in Dev Container

- **GitHub Codespaces:** Click the **"Code" → "Create codespace on main"** button.
- **VS Code Dev Containers Extension:**
    - Clone the repo locally
    - Open the folder in VS Code
    - Run: `Dev Containers: Reopen in Container` from the Command Palette

### Start the Local Server

Once inside the Dev Container, run:

```bash
mkdocs serve -a 0.0.0.0:8000
```

