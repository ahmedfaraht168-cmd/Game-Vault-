# ◈ GAME VAULT — Inventory Manager



---

## Requirements

- Python 3.7 or higher
- No third-party packages needed — uses only the Python standard library (`tkinter` is included with Python)

---

## How to Run

```bash
python game_inventory.py
```

That's it. The app creates `inventory.txt` automatically in the same folder on first launch.

---

## File Structure

```
game_inventory.py   ← main application (run this)
inventory.txt       ← auto-created; stores all game records
README.md           ← this file
```

---

## Data Format

Each game is stored as one line in `inventory.txt`:

```
name:God of War | price:60 | quantity:5
```

---

## Features

### Add a Game
Fill in the three fields in the sidebar (name, price, quantity) and click **Add to Vault**.

- Price and quantity must be whole numbers
- Duplicate names are allowed (each entry is a separate line)

### Sell a Game
Type a game name in the **Sell** field and click **Sell One Copy** — this decreases the quantity by 1.

- **Tip:** Click any row in the table to auto-fill the sell field with that game's name, avoiding typos
- Returns an error if the game is not found or is out of stock
- Name matching is case-insensitive (`god of war` matches `God of War`)

### Delete a Game
Type a game name in the **Delete** field and click **Remove from Vault**.

- A confirmation dialog appears before anything is deleted
- Permanently removes the game from `inventory.txt`

### Inventory Table
The table shows all games with color-coded quantity indicators:

| Color | Meaning |
|-------|---------|
| 🟢 Green | Healthy stock (5 or more copies) |
| ⚪ White | Low stock (1–4 copies) |
| 🔴 Red | Out of stock (0 copies) |

The **Portfolio Value** in the top bar shows the total monetary value of all stock (`price × quantity` summed across all games), and updates automatically after every operation.

### Status Bar
The bar at the bottom of the window shows real-time feedback for every action (success in green, errors in red).

---

## Keyboard Tips

| Action | How |
|--------|-----|
| Move between fields | `Tab` |
| Click a row | Auto-fills the Sell field |
| Confirm delete | Click Yes in the dialog |

---

## Troubleshooting

**App won't start on Linux/macOS**
Tkinter may not be installed by default. Fix with:
```bash
# Ubuntu / Debian
sudo apt-get install python3-tk

# macOS (via Homebrew)
brew install python-tk
```

**Inventory not saving**
Make sure `game_inventory.py` and `inventory.txt` are in a folder where you have write permissions.

**Wrong quantity after manual edit of `inventory.txt`**
Make sure every line follows the exact format: `name:X | price:Y | quantity:Z` (spaces around the `|` are required).
