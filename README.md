# bambu-nfc

This repository contains tools for working with Bambu Lab filament spool NFC tags, building on information from the [Bambu Research Group RFID Tag Guide](https://github.com/Bambu-Research-Group/RFID-Tag-Guide).

## Contents

- **`/nfc`** — Bambu NFC tag data read using a Flipper Zero (e.g., `/nfc/PLA`)
- **`/src`** — Python scripts for key generation and tag decoding
- **`/decoded`** — Sample human-readable JSON files generated from the NFC data

## Usage

All scripts should be run from the `src/` directory:

### `gen_key.py`

Generates the A-Keys for a Bambu NFC tag.

```sh
cd src
python3 ./gen_key.py -u 6AA42B72 -f ../nfc/ABS/ABS-GF_ORANGE_1.json
```

See `python3 ./gen_key.py -h` for all options.

### `decode.py`

Decodes Bambu NFC tag data into a human-readable JSON file.

```sh
python3 ./decode.py -n ../nfc/PLA/PLA_BASIC_GREEN_1.nfc -f ../decoded/PLA_Basic.json
```

See `python3 ./decode.py -h` for all options.

**Example output:**

```json
{
    "file": "../nfc/PLA/PLA_BASIC_GREEN_1.nfc",
    "filament": {
        "type": "PLA",
        "detailed type": "PLA Basic",
        "color": "#00AE42FF",
        "diameter [mm]": 1.75,
        "length [m]": 82,
        "drying temperature [C]": 55,
        "drying time [H]": 8
    },
    "spool": {
        "weight [g]": 250,
        "width [mm]": 66.25
    },
    "print": {
        "bed temperature [C]": 0,
        "min hotend temperature [C]": 190,
        "max hotend temperature [C]": 230
    },
    "production datetime": "2024-04-30 13:44:00"
}
```
