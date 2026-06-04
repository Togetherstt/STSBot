# STSBot v0.1.0

First standalone open-source release of `STSBot`.

## Highlights

- Extracted the `Slay the Spire 2` card-guess bot from a larger private bot project.
- Included the standalone `NoneBot2` plugin implementation.
- Included built-in card JSON data for local gameplay.
- Added unit tests and a local interactive test script.
- Added independent project scaffolding and open-source repository metadata.

## Included

- `src/plugins/sts_card_guess/`
- `data/sts_card_guess/cards/`
- `tests/test_sts_card_guess.py`
- `scripts/test_sts_card_guess_local.py`

## Verification

- `python -m unittest tests.test_sts_card_guess`
