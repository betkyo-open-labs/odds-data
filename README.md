# Betkyo odds data

![What a keno risk level actually changes](docs/cover.webp)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22725012.svg)](https://doi.org/10.5281/zenodo.22725012) [![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/) [![Hugging Face](https://img.shields.io/badge/Hugging_Face-Betkyo%2Fodds--data-yellow)](https://huggingface.co/datasets/Betkyo/odds-data) [![Kaggle](https://img.shields.io/badge/Kaggle-dataset-20BEFF)](https://www.kaggle.com/datasets/betkyo/betkyo-odds-data-casino-paytables-from-source)

Machine-readable tables behind the [Betkyo Journal](https://betkyo.com/en/blog/), exported from the game engine source rather than typed by hand. Each file names the engine module it was read from and the article that derives the figures. Canonical copies: `https://betkyo.com/data/<name>.json` and `.csv`; `https://betkyo.com/data/index.json` lists them.

| File | What it is | Derivation |
|---|---|---|
| `keno-paytables` | All forty keno payout tables (level × picks × hits), total-return multipliers | [What a keno risk level actually changes](https://betkyo.com/en/blog/what-a-keno-risk-level-changes/) |
| `plinko-multipliers` | Plinko bucket multipliers for every risk level and row count | [Plinko, priced](https://betkyo.com/en/blog/plinko-priced-the-binomial-behind-every-board/) |
| `roulette-bets` | Bet kinds, pockets covered, multiplier, expected return; wheel order and red pockets | [A roulette bet is a string](https://betkyo.com/en/blog/a-roulette-bet-is-a-string-self-describing-keys-and-the-36-table/) |
| `blackjack-dealer-outcomes` | Dealer final-total distribution by upcard, infinite shoe, dealer stands on all 17s | [Dealer bust odds by upcard](https://betkyo.com/en/blog/dealer-bust-odds-by-upcard-on-an-infinite-shoe/) |
| `koban-ladder` | Koban Flip cumulative multiplier after n straight calls, floored to cents | [Designing Koban Flip](https://betkyo.com/en/blog/designing-koban-flip-every-face-is-fixed-when-you-buy-the-coin/) |
| `fukubukuro-bags` | Item weights (millionths) and payout multiples for both lucky bags | [Designing Fukubukuro](https://betkyo.com/en/blog/designing-fukubukuro-the-lucky-bag-that-always-pays-something/) |

## Using the files

Every JSON file carries its own provenance (`source` names the engine module, `article` the derivation, `generated` the export date) and a `data` object; the CSV next to it is the same table flattened. `data/index.json` lists them all.

```bash
# dealer bust chance with a 6 showing, straight from the table
node -e "const t=require('./data/blackjack-dealer-outcomes.json').data.table; console.log(t.find(r=>r.upcard==='6').bust)"
# 0.4231...

# the 16-row HIGH Plinko board
node -e "console.log(require('./data/plinko-multipliers.json').data.HIGH['16'].join(' '))"
# 1000 130 26 9 4 2 0.2 0.2 0.2 0.2 0.2 2 4 9 26 130 1000
```

```python
import pandas as pd
keno = pd.read_csv("https://raw.githubusercontent.com/betkyo-open-labs/odds-data/main/data/keno-paytables.csv")
```

The procedure behind every figure, including the times it found bugs in the games themselves: [How the Journal verifies a number](https://betkyo.com/en/blog/how-the-journal-verifies-a-number-methodology/). The scripts that turn these tables into the returns quoted in the articles live in [odds-derivations](https://github.com/betkyo-open-labs/odds-derivations); the round verifier in [provably-fair-verifier](https://github.com/betkyo-open-labs/provably-fair-verifier).

## Citing

Archived, versioned copy with a DOI on Zenodo: [10.5281/zenodo.22725012](https://doi.org/10.5281/zenodo.22725012) (concept DOI for all versions: 10.5281/zenodo.22725011). A `CITATION.cff` is included; GitHub's "Cite this repository" button reads it.

> Betkyo Research (2026). *Betkyo odds data: casino paytables and outcome distributions exported from game engine source* (1.0.0) [Data set]. Betkyo Journal. https://doi.org/10.5281/zenodo.22725012

Also mirrored on [Hugging Face](https://huggingface.co/datasets/Betkyo/odds-data) and [Kaggle](https://www.kaggle.com/datasets/betkyo/betkyo-odds-data-casino-paytables-from-source).

Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribute as "Betkyo Journal, betkyo.com/data". Corrections: dev@betkyo.com.

Betkyo is a crypto casino with provably fair original games. 18+. These tables describe games of chance with a house edge; nothing here is betting advice.
