# Password Generator

A static password generator page. Passwords are created in the browser with `crypto.getRandomValues`; nothing is sent to a server.

## URL parameters

Upper- and lowercase letters and digits are always used. Look-alike characters `I O Q l o 0 1` are always excluded.

| Parameter | Values | Default |
|---|---|---|
| `len` | 4–128 | 25 |
| `special` | `on` / `off` — special characters `!#%+@:=?*` | `off` |

When special characters are enabled, the `!#%+@:=?*` set itself becomes editable: characters can be added or removed. The edited set is not stored in the URL.

Example: `?len=16&special=on`

## Strength indicator

The password card border colour shifts smoothly from red through orange to green. The score is the lower of two values:

- **Length** — based on NIST SP 800-63B-4 (minimum 15 characters for a password without MFA) and CISA (16 characters or more): up to 8 — red, 15–16 — turning green, 25 — maximum.
- **Entropy** — `length × log2(alphabet size)`: 40 bits — weak, 80 — strong, 128 and above — very strong.

The score does not change beyond 25 characters.
