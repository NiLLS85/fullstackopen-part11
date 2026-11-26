Let's pick Python for a team of six people building a web API that is about to be released.

Linting: the usual choice today is Ruff, a very fast linter and formatter that replaces Flake8, isort and much of Pylint. Black is still common for formatting, and mypy or Pyright add static type checking, which catches many bugs before the code even runs.

Testing: pytest is the de facto standard, together with pytest-cov for coverage reports. Playwright also has Python bindings for end-to-end tests, and tox or nox can run the suite against several Python versions.

Building: Python is not compiled, so "building" usually means packaging. Tools such as uv, Poetry or the standard build module create wheels, and lock files make the dependencies reproducible. For deployment, the build step often produces a Docker image that is pushed to a registry.

Alternatives to Jenkins and GitHub Actions: GitLab CI/CD, CircleCI, Azure Pipelines, Bitbucket Pipelines, Travis CI, TeamCity, Buildkite, and lighter self-hosted options like Drone or Woodpecker CI.

Self-hosted or cloud? For a team of six I would start with a cloud-based service. There is no server to install, patch or back up, the free or cheap tiers are usually enough, and the team can focus on the product instead of the CI machine. Self-hosting starts to make sense when builds need special hardware such as GPUs, when builds are so long and frequent that cloud minutes become expensive, or when the code or data cannot leave the company network for legal reasons.

To decide, I would want to know the budget, how many builds per day we expect and how long they take, the security and compliance requirements, and whether someone in the team has time to maintain a CI server.
