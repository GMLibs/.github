
# GMLibs
### Game Library & Source Network

GMLibs is a centralized collection of browser games, game assets, covers, and supporting resources. It brings multiple game repositories together into one accessible library for developers to use in their own projects.

GMLibs provides access through **CDN delivery, direct file fetching, and existing JSON catalogs**. Developers can use these sources to build game libraries, launchers, websites, browsers, and other applications.

## Getting Started

Most GMLibs repositories can be accessed through [jsDelivr](https://www.jsdelivr.com/), allowing files hosted on GitHub to be delivered through a CDN.

### CDN Format

```text
https://cdn.jsdelivr.net/gh/GMLibs/REPOSITORY@BRANCH/FILE_PATH
```

Example:

```text
https://cdn.jsdelivr.net/gh/GMLibs/NebulaCDN@main/games.json
```

Replace `REPOSITORY`, `BRANCH`, and `FILE_PATH` with the appropriate values for the repository.

### Fetching Files

Static files can be requested directly:

```js
const url = "https://cdn.jsdelivr.net/gh/GMLibs/NebulaCDN@main/games.json";

const response = await fetch(url);
const data = await response.json();

console.log(data);
```

No API key or authentication is required for public repositories.

---

# Sources & Repositories

GMLibs contains multiple independent sources. Some provide JSON catalogs, while others offer directly accessible files or complete game directories.

## Game Libraries

### NebulaCDN
[Repository](https://github.com/GMLibs/NebulaCDN)

A collection of browser games with a dedicated JSON catalog.

| Resource | Description |
|---|---|
| `games.json` | Game catalog |
| `games/` | Individual game files |

**CDN Base:**
```js
const NEBULA = "https://cdn.jsdelivr.net/gh/GMLibs/NebulaCDN@main";
```

**Fetch the catalog:**
```js
const games = await fetch(`${NEBULA}/games.json`)
  .then(r => r.json());
```

**Load a game:**
```js
const game = games.games.find(g => g.slug === "doom");

if (game) {
  iframe.src = `${NEBULA}/${game.file}`;
}
```

Nebula uses the `file` property for its game paths. These paths are relative to the repository's root.

---

### GN Math
Three separate repositories provide games, assets, and covers.

| Repository | Purpose |
|---|---|
| [GN-Math-Games-](https://github.com/GMLibs/GN-Math-Games-) | Game HTML files |
| [GN-Math-Assets-](https://github.com/GMLibs/GN-Math-Assets-) | Supporting assets |
| [GN-Math-Covers-](https://github.com/GMLibs/GN-Math-Covers-) | Game covers |

**CDN Bases:**
```js
const GN_GAMES = "https://cdn.jsdelivr.net/gh/GMLibs/GN-Math-Games-@main";
const GN_ASSETS = "https://cdn.jsdelivr.net/gh/GMLibs/GN-Math-Assets-@main";
const GN_COVERS = "https://cdn.jsdelivr.net/gh/GMLibs/GN-Math-Covers-@main";
```

GN Math uses direct file access rather than a unified JSON game catalog.

**Example game:**
```html
<iframe src="https://cdn.jsdelivr.net/gh/GMLibs/GN-Math-Games-@main/0-fix2.html"></iframe>
```

**Example cover:**
```html
<img src="https://cdn.jsdelivr.net/gh/GMLibs/GN-Math-Covers-@main/1.png">
```

Use the actual filenames and directory paths when requesting files. Some games use additional assets from the separate assets repository.

---

### Seraph
[Repository](https://github.com/GMLibs/Seraph)

A browser-game collection with a JSON catalog and separate game directories.

**Important resources:**
- `seraph.json` — Game catalog
- `seraph/` — Game files
- `covers/` — Cover resources
- `storage/` — Supporting resources

**CDN Base:**
```js
const SERAPH = "https://cdn.jsdelivr.net/gh/GMLibs/Seraph@main";
```

**Fetch games:**
```js
const games = await fetch(`${SERAPH}/seraph.json`)
  .then(r => r.json());
```

**Load a game:**
```js
const game = games.find(g => g.name === "Slope");

if (game) {
  iframe.src = SERAPH + game.url;
}
```

Seraph uses the `url` property for game locations. Its catalog also contains image information.

---

### Truffled
[Repository](https://github.com/GMLibs/Truffled)

A game source with its own JSON catalog and organized game directories.

**Important resources:**
- `truffled.json` — Game catalog
- `truffled/` — Game files
- `covers/` — Cover resources

**CDN Base:**
```js
const TRUFFLED = "https://cdn.jsdelivr.net/gh/GMLibs/Truffled@main";
```

**Fetch games:**
```js
const games = await fetch(`${TRUFFLED}/truffled.json`)
  .then(r => r.json());
```

**Load a game:**
```js
const game = games.find(g => g.name === "2048");

if (game) {
  iframe.src = TRUFFLED + game.url;
}
```

Truffled uses `url` and `img` properties in its catalog. Preserve the original directory structure when loading games.

---

### UGS
[Repository](https://github.com/GMLibs/UGS)

A packaged game collection with its own loading system and supporting files.

Unlike the other catalog-based sources, UGS uses JavaScript and HTML resources to organize and load its games.

**Important resources:**
- `AASINGLEFILE.html`
- `UGS-Files/`
- `offline/`
- `games.js`
- `game.js`
- `esm.js`

**CDN Base:**
```js
const UGS = "https://cdn.jsdelivr.net/gh/GMLibs/UGS@main";
```

UGS should generally be accessed through its existing launcher and loading system rather than treating its game identifiers as direct HTML filenames.

Preserve the supporting files and directory structure when integrating it.

---

### CKV
[Repository](https://github.com/GMLibs/CKV)

A game collection with a JSON catalog and separate game and cover directories.

**Important resources:**
- `ckv.json` — Game catalog
- `ckv/` — Game files
- `covers/` — Cover resources

**CDN Base:**
```js
const CKV = "https://cdn.jsdelivr.net/gh/GMLibs/CKV@main";
```

**Fetch games:**
```js
const data = await fetch(`${CKV}/ckv.json`)
  .then(r => r.json());

const games = data.games;
```

**Load a game:**
```js
const game = games.find(g => g.name === "2048game");

if (game) {
  iframe.src = CKV + game.url;

  const cover = CKV + game.img;
}
```

CKV stores its game entries inside the `games` property. Its `url` and `img` values contain repository-relative paths.

---

### DominumUBG
DominumUBG is divided into three repositories.

| Repository | Purpose |
|---|---|
| [DominumUBG-Games-](https://github.com/GMLibs/DominumUBG-Games-) | Game HTML files |
| [DominumUBG-Assets-](https://github.com/GMLibs/DominumUBG-Assets-) | Game catalog and supporting assets |
| [DominumUBG-Covers-](https://github.com/GMLibs/DominumUBG-Covers-) | Game covers |

**CDN Bases:**
```js
const DOM_GAMES = "https://cdn.jsdelivr.net/gh/GMLibs/DominumUBG-Games-@main";
const DOM_ASSETS = "https://cdn.jsdelivr.net/gh/GMLibs/DominumUBG-Assets-@main";
const DOM_COVERS = "https://cdn.jsdelivr.net/gh/GMLibs/DominumUBG-Covers-@main";
```

**Fetch the catalog:**
```js
const games = await fetch(`${DOM_ASSETS}/games.json`)
  .then(r => r.json());
```

DominumUBG uses URL placeholders in its catalog:

- `{HTML_URL}` — Game repository.
- `{COVER_URL}` — Cover repository.

These placeholders must be replaced before using the URLs.

**Example:**
```js
const game = games.find(g => g.name === "OvO");

if (game) {
  const gameURL = game.url.replace("{HTML_URL}", DOM_GAMES);
  const coverURL = game.cover.replace("{COVER_URL}", DOM_COVERS);

  iframe.src = gameURL;
}
```

This allows the game catalog to reference files hosted in separate repositories.

---

### Selenite
[Repository](https://github.com/GMLibs/Selenite)

A browser-game source with a JSON catalog and individually organized game directories.

**Important resource:**
- `data/games.json` — Game catalog

**CDN Base:**
```js
const SELENITE = "https://cdn.jsdelivr.net/gh/GMLibs/Selenite@main";
```

**Fetch the catalog:**
```js
const games = await fetch(`${SELENITE}/data/games.json`)
  .then(r => r.json());
```

Selenite uses its own game directory and image references. Use the catalog's `directory` and `image` fields rather than assuming every game follows a standard HTML filename.

Preserve the original loader and asset paths when integrating its games.

---

## Additional Sources

### Noah's Tutoring Hub (NTH)
[Repository](https://github.com/GMLibs/Noah-s-Tutoring-Hub-NTH-)

A complete website project containing game-related resources and supporting files.

The repository includes its own website structure and game directories. It is best accessed through its existing entry points or individual files.

**CDN Base:**
```js
const NTH = "https://cdn.jsdelivr.net/gh/GMLibs/Noah-s-Tutoring-Hub-NTH-@master";
```

Use the actual paths from the repository when requesting individual files.

### Duck With Goose Skin (DWGS)
[Repository](https://github.com/GMLibs/Duck-With-Goose-Skin-DWGS-)

A complete browser-game website source with its own game directories and supporting resources.

**CDN Base:**
```js
const DWGS = "https://cdn.jsdelivr.net/gh/GMLibs/Duck-With-Goose-Skin-DWGS-@main";
```

The repository can be accessed through its website entry point or by directly requesting individual game files.

Preserve the original directory structure and dependencies when integrating games.

---

## Supporting Libraries

### Lumin
[Repository](https://github.com/GMLibs/Lumin)

A collection of JavaScript resources and supporting libraries.

**CDN Base:**
```js
const LUMIN = "https://cdn.jsdelivr.net/gh/GMLibs/Lumin@main";
```

JavaScript files can be included directly in a project:

```html
<script src="https://cdn.jsdelivr.net/gh/GMLibs/Lumin@main/lumin.min.js"></script>
<script src="https://cdn.jsdelivr.net/gh/GMLibs/Lumin@main/fonts.min.js"></script>
```

---

# Fetching Methods

Different repositories use different systems. The following table summarizes how each source should generally be accessed.

| Source | Fetching Method | Catalog / Entry Point |
|---|---|---|
| NebulaCDN | JSON + CDN | `games.json` |
| GN Math | Direct CDN | Individual files |
| Seraph | JSON + CDN | `seraph.json` |
| Truffled | JSON + CDN | `truffled.json` |
| UGS | Existing loader | `AASINGLEFILE.html` |
| CKV | JSON + CDN | `ckv.json` |
| DominumUBG | JSON + multiple CDNs | Assets `games.json` |
| Selenite | JSON + CDN | `data/games.json` |
| Noah's Tutoring Hub | Direct CDN | Existing website files |
| DWGS | Direct CDN | Existing website files |
| Lumin | Direct CDN | JavaScript files |

## CDN File Paths

When working with JSON catalogs, pay attention to how each source stores its paths.

Some catalogs use paths relative to the repository root:

```js
const gameURL = BASE + "/" + game.file;
```

Others use paths beginning with `/`:

```js
const gameURL = BASE + game.url;
```

Some sources use placeholders that must be replaced before a URL can be used:

```js
const gameURL = game.url.replace("{HTML_URL}", GAME_BASE);
```

Do not assume every repository uses the same catalog format or path structure.

---

# Integration Example

A basic game launcher can use a CDN-hosted game file inside an iframe.

```html
<iframe
  id="game-frame"
  allowfullscreen
  style="width:100%;height:600px;border:0;">
</iframe>

<script>
  const BASE =
    "https://cdn.jsdelivr.net/gh/GMLibs/NebulaCDN@main";

  async function loadGame(slug) {
    const response = await fetch(`${BASE}/games.json`);

    if (!response.ok) {
      throw new Error("Could not fetch game catalog.");
    }

    const catalog = await response.json();

    const game = catalog.games.find(
      item => item.slug === slug
    );

    if (!game) {
      throw new Error("Game not found.");
    }

    document.getElementById("game-frame").src =
      `${BASE}/${game.file}`;
  }

  loadGame("doom").catch(console.error);
</script>
```

---

# Important Notes

- **CDN availability:** Public repositories can be accessed through jsDelivr without an API key.
- **File paths:** Always use the actual repository paths and filenames.
- **Dependencies:** Some games require additional JavaScript, images, audio, or other resources.
- **Directory structure:** Do not move or rename files without updating their references.
- **Branch names:** Check the repository's default branch before constructing CDN URLs.
- **Large files:** CDN providers have file-size and delivery restrictions.
- **Compatibility:** Some games may require specific browser features or iframe permissions.
- **Licensing:** Public availability does not automatically grant redistribution rights. Respect original licenses and attribution requirements.

---

# Credits

GMLibs brings together resources from multiple independent projects and repositories.

Original developers, creators, and maintainers deserve credit for their work. Please respect their licenses, attribution requirements, and removal requests.

---

<p align="center">
  <strong>GMLibs</strong><br>
  One library. Multiple sources. Easier integration.
</p>
