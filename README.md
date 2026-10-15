# Gun Mod for MCPE - content server

Static files the app (`com.QuillbyteStudios.GunModForMCPE`) downloads at runtime.

| Path | What |
|---|---|
| `catalog.json` | Item + skin list. The app swaps it in when `version` is higher than its own. |
| `files/` | Packs: `.mcaddon`, `.mcworld`, `.mctemplate`, `.mcpack` |
| `img/` | Images for items added after the app release (`banner`, `image`, skin `texture` / `front`) |
| `worlds/<id>/` | PLAY WORLD kits (used when an item's `world.kit` is a relative path) |

App URLs (tried in order):

- https://cdn.jsdelivr.net/gh/mainsabun/gunmod-mcpe-content@main/
- https://raw.githubusercontent.com/mainsabun/gunmod-mcpe-content/main/

## Add content without an app update

1. Put the pack in `files/` and its images in `img/`.
2. Add an item to `catalog.json` with relative paths, e.g.
   `"url": "files/new_gun.mcaddon", "file_name": "New Gun.mcaddon", "size": <bytes>,
   "banner": "img/new_gun_banner.jpg", "image": "img/new_gun.png"`.
   `size` must be the exact byte size (truncated downloads are rejected).
3. Raise `version`, commit, push.
4. Refresh the CDN copy of the catalog:
   https://purge.jsdelivr.net/gh/mainsabun/gunmod-mcpe-content@main/catalog.json
