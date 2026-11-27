# Password Generator

A secure password generator with customizable rules.

## Development

This tool has no build dependencies. The source file can be edited directly.

## Output

Production files are in the `dist/` folder:
- `dist/index.html` - Main application

## URL parameters

Settings can be set through readable query parameters, e.g.
`https://passwordgenerator.wbtl.app/?length=64` or
`https://passwordgenerator.wbtl.app/?mode=passphrase&words=8&separator=.`

Order of precedence: **defaults < saved local settings < URL**. Only the parameters given in the
URL are overridden; everything else comes from local settings (or defaults). Opening a URL does not
change saved settings; changing a setting afterwards saves it as usual.

When any setting is changed, the URL is updated to contain the full set of parameters for the
current mode, so it can be copied and shared to reproduce exactly that setup.

Parameter names are case-insensitive. Booleans accept `true`/`false` (also `1`/`0`, `yes`/`no`, `on`/`off`).

| Mode | Parameter | Meaning |
|------|-----------|---------|
| all | `mode` | `password` (default), `passphrase` or `pronounceable` |
| all | `count` | Number of passwords to generate (1-100) |
| password | `length` | Password length (2-1000) |
| password | `upper`, `lower`, `numbers`, `symbols` | Include character type |
| password | `upperMin`, `upperMax`, `lowerMin`, `lowerMax`, `numbersMin`, `numbersMax`, `symbolsMin`, `symbolsMax` | Min/max count per type (empty or `none` = no max) |
| password | `excludeAmbiguous` | Exclude `0O1lI` |
| password | `symbolSet` | Custom symbol set (empty = default set) |
| password | `exclude` | Characters to exclude |
| passphrase | `words` | Number of words (3-50) |
| passphrase | `separator` | Word separator (max 3 characters) |
| passphrase | `capitalize` | Capitalize words |
| passphrase | `number` | Include a number |
| pronounceable | `length` | Length (2-100) |
| pronounceable | `upper` | Include capitals |
| pronounceable | `numbers` | Include numbers |

Parameters are interpreted for the selected mode, so `length` means the pronounceable length when
`mode=pronounceable`. Legacy `#passphrase` / `#pronounceable` links still work and are converted.
