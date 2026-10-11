# Contributing

Thank you for helping. mini-AlbertCode SWE Agent is a proprietary product, but what makes it easy to
install and use lives here in the open, and contributions to it are welcome.

## What you can contribute

| Area | Examples |
|---|---|
| Documentation | Fixing an error, a clearer explanation, a missing step, a translation |
| Installer | Support for another distribution, a clearer message, a fix ([installer/](installer/README.md)) |
| Tutorials | A walkthrough of a real task, start to finish |

The application itself isn't in this repository. To change how mini-AlbertCode plans, verifies or
reviews work, open a [feature request](https://github.com/huynvic/mini-albertcode-swe-agent/issues/new/choose)
describing the behaviour you want.

## Before you start

- **Small fixes** (typos, broken links, one-line clarifications): open a pull request directly.
- **Anything larger**: open an issue first, so we can agree on the approach before you spend time on it.

## Pull requests

1. Fork the repository and create a branch from `main`.
2. Make your change. Keep each pull request to one subject.
3. Run the checks that apply:

   ```bash
   sh installer/tests/test_install_sh.sh     # installer changes
   python3 scripts/release_gate.py           # every change: scans for secrets and private material
   ```

4. Open the pull request and fill in its template. Say what you changed, why, and how you checked it.

The same checks run automatically on every pull request.

## Writing style

- Write for a developer who has never seen mini-AlbertCode, and give them the command they need.
- Use concrete language. Say what mini-AlbertCode does, and leave out adjectives about it.
- Never claim a feature or a compatibility that you haven't checked.

## Never include

- API keys, tokens, passwords or other credentials, even expired ones;
- private source code, internal URLs, or anything from a private repository;
- personal information about anyone else.

If you commit one by mistake, tell us in the pull request. Deleting the file isn't enough, because
it stays in Git history.

## Licence of contributions

Code in this repository is Apache-2.0 and documentation is CC BY 4.0 ([LICENSING.md](LICENSING.md)).
Sign off each commit (`git commit -s`) to certify the
[Developer Certificate of Origin](https://developercertificate.org/): that you wrote the change, or
have the right to submit it under those terms.

## Conduct

Everyone taking part is expected to follow the [code of conduct](CODE_OF_CONDUCT.md).
