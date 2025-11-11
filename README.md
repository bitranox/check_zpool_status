# check_zpool_status

<!-- Badges -->
[![CI](https://github.com/bitranox/check_zpool_status/actions/workflows/ci.yml/badge.svg)](https://github.com/bitranox/check_zpool_status/actions/workflows/ci.yml)
[![CodeQL](https://github.com/bitranox/check_zpool_status/actions/workflows/codeql.yml/badge.svg)](https://github.com/bitranox/check_zpool_status/actions/workflows/codeql.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Open in Codespaces](https://img.shields.io/badge/Codespaces-Open-blue?logo=github&logoColor=white&style=flat-square)](https://codespaces.new/bitranox/check_zpool_status?quickstart=1)
[![PyPI](https://img.shields.io/pypi/v/check_zpool_status.svg)](https://pypi.org/project/check_zpool_status/)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/check_zpool_status.svg)](https://pypi.org/project/check_zpool_status/)
[![Code Style: Ruff](https://img.shields.io/badge/Code%20Style-Ruff-46A3FF?logo=ruff&labelColor=000)](https://docs.astral.sh/ruff/)
[![codecov](https://codecov.io/gh/bitranox/check_zpool_status/graph/badge.svg?token=UFBaUDIgRk)](https://codecov.io/gh/bitranox/check_zpool_status)
[![Maintainability](https://qlty.sh/badges/041ba2c1-37d6-40bb-85a0-ec5a8a0aca0c/maintainability.svg)](https://qlty.sh/gh/bitranox/projects/check_zpool_status)
[![Known Vulnerabilities](https://snyk.io/test/github/bitranox/check_zpool_status/badge.svg)](https://snyk.io/test/github/bitranox/check_zpool_status)

`check_zpool_status` is a starter CLI for monitoring ZFS pools. It keeps the interface opinionated—rich-click drives ergonomics while lib_cli_exit_tools handles exits—so you can focus on wiring real `zpool status` calls.
- CLI entry point styled with rich-click (rich output + click ergonomics).
- Exit-code and messaging helpers powered by lib_cli_exit_tools.
- Metadata helpers ready for packaging, testing, and release automation.

## Install - recommended via UV
UV - the ultrafast installer - written in Rust (10–20× faster than pip/poetry)

```bash
# recommended Install via uv 
pip install --upgrade uv
# Create and activate a virtual environment (optional but recommended)
uv venv
# macOS/Linux
source .venv/bin/activate
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
# install via uv from PyPI
uv pip install check_zpool_status
```

For alternative install paths (pip, pipx, uv, uvx source builds, etc.), see
[INSTALL.md](INSTALL.md). All supported methods register both the
`check_zpool_status` and `check-zpool-status` commands on your PATH.

### Python 3.13+ Baseline

- The project targets **Python 3.13 and newer only**. 
- Runtime dependencies stay on the current stable releases (`rich-click>=1.9.3`
  and `lib_cli_exit_tools>=2.0.0`) and keeps pytest, ruff, pyright, bandit,
  build, twine, codecov-cli, pip-audit, textual, and import-linter pinned to
  their newest majors.
- CI workflows exercise GitHub's rolling runner images (`ubuntu-latest`,
  `macos-latest`, `windows-latest`) and cover CPython 3.13 alongside the latest
  available 3.x release provided by Actions.


## Usage

The CLI leverages [rich-click](https://github.com/ewels/rich-click) so help output, validation errors, and prompts render with Rich styling while keeping the familiar click ergonomics.
The scaffold keeps a CLI entry point so you can validate packaging flows, but it
currently exposes a single informational command while logging features are
developed:

```bash
check_zpool_status info
check_zpool_status hello
check_zpool_status fail
check_zpool_status --traceback fail
check-zpool-status info
python -m check_zpool_status info
uvx check_zpool_status info
```

For library use you can import the documented helpers directly:

```python
import check_zpool_status as btpc

btpc.emit_greeting()
try:
    btpc.raise_intentional_failure()
except RuntimeError as exc:
    print(f"caught expected failure: {exc}")

btpc.print_info()
```


## Further Documentation

- [Install Guide](INSTALL.md)
- [Development Handbook](DEVELOPMENT.md)
- [Contributor Guide](CONTRIBUTING.md)
- [Changelog](CHANGELOG.md)
- [Module Reference](docs/systemdesign/module_reference.md)
- [License](LICENSE)
