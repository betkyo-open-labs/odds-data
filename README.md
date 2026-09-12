# Betkyo odds data

Machine-readable tables behind the [Betkyo Journal](https://betkyo.com/en/blog/), exported from the game engine source rather than typed by hand. Each file names the engine module it was read from and the article that derives the figures. Canonical copies: `https://betkyo.com/data/<name>.json` and `.csv`; `https://betkyo.com/data/index.json` lists them.

| File | What it is | Derivation |
|---|---|---|
| `keno-paytables` | All forty keno payout tables (level × picks × hits), total-return multipliers | [What a keno risk level actually changes](https://betkyo.com/en/blog/what-a-keno-risk-level-changes/) |
| `plinko-multipliers` | Plinko bucket multipliers for every risk level and row count | [Plinko, priced](https://betkyo.com/en/blog/plinko-priced-the-binomial-behind-every-board/) |
| `roulette-bets` | Bet kinds, pockets covered, multiplier, expected return; wheel order and red pockets | [A roulette bet is a string](https://betkyo.com/en/blog/a-roulette-bet-is-a-string-self-describing-keys-and-the-36-table/) |
| `blackjack-dealer-outcomes` | Dealer final-total distribution by upcard, infinite shoe, dealer stands on all 17s | [Dealer bust odds by upcard](https://betkyo.com/en/blog/dealer-bust-odds-by-upcard-on-an-infinite-shoe/) |
| `koban-ladder` | Koban Flip cumulative multiplier after n straight calls, floored to cents | [Designing Koban Flip](https://betkyo.com/en/blog/designing-koban-flip-every-face-is-fixed-when-you-buy-the-coin/) |
| `fukubukuro-bags` | Item weights (millionths) and payout multiples for both lucky bags | [Designing Fukubukuro](https://betkyo.com/en/blog/designing-fukubukuro-the-lucky-bag-that-always-pays-something/) |

The procedure behind every figure, including the times it found bugs in the games themselves: [How the Journal verifies a number](https://betkyo.com/en/blog/how-the-journal-verifies-a-number-methodology/). The scripts that turn these tables into the returns quoted in the articles live in the `odds-derivations` repository; the round verifier in `provably-fair-verifier`.

Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribute as "Betkyo Journal, betkyo.com/data". Corrections: dev@betkyo.com.

Betkyo is a crypto casino with provably fair original games. 18+. These tables describe games of chance with a house edge; nothing here is betting advice.
