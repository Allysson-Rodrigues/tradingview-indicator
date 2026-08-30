# Contributing to ICT + FVG + RSI

Thank you for your interest in contributing to this indicator!

## Development Workflow
1. **Local Development**: Code modifications are made locally in the `src/` directory.
2. **Version Bumping**: Always bump the version in the `*.pine` file header and in `CHANGELOG.md` when making functional changes.
3. **Manual Validation**: Because Pine Script requires the TradingView environment to run, you must copy the `.pine` contents into the TradingView Pine Editor and manually validate the chart against the scenarios listed in the technical analysis document.
4. **Pull Requests**: Submit your changes via a Pull Request to the `main` branch. Ensure the commit messages follow the repository's standard (e.g. `Refactor: ...`, `Fix: ...`, `Docs: ...`).

## Code Style
- Use `snake_case` for variables and `camelCase` or `PascalCase` only for UDTs and specific settings objects.
- Keep the code modular. Avoid duplicating logic for multiple timeframes.
- Document user-facing `input`s clearly with tooltips.

## Reporting Issues
Please open an issue describing the bug, including the timeframe and asset you were testing, and a screenshot of the unexpected behavior.
