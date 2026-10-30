# Spicetify Throwback

**Throwback** is a fun and nostalgic theme for the Spotify Desktop client that is inspired by the original UI design of the Spotify client and early 2010's-era web design.

*Long live skeuomorphism!*

![Screenshot](./static/screenshot-01.png)
![Screenshot](./static/screenshot-02.png)

## WARNING - ALPHA VERSION

This theme is **alpha quality software** and various things may break! Please only install this theme at your own risk! I may or may not have time to address all issues in the future!

## requirements

- spotify desktop (win or linux)
- spicetify v2.46.4 or newer

**note:** originally built & tested on spotify win. linux support added after, css targets spotify web ui (same on both) but linux not tested thoroughly. report issues.

## installation (linux)

### 1. install spicetify & make spotify writable

follow the official guide at [spicetify.app](https://spicetify.app/docs/getting-started). spicetify must modify the spotify install, which depends on how you installed it:

| spotify install | what to do |
| --- | --- |
| **apt / deb** | `sudo chmod a+wr /usr/share/spotify` then `sudo chmod a+wr /usr/share/spotify/Apps -R` |
| **aur** (`spotify`) | `sudo chmod a+wr /opt/spotify` then `sudo chmod a+wr /opt/spotify/Apps -R` |
| **spotify-launcher** | `spicetify config spotify_path /home/<you>/.local/share/spotify-launcher/install/usr/share/spotify` (full abs path, no `~` or `$HOME`) |
| **flatpak** | set `spotify_path` & `prefs_path` to full abs paths (see spicetify docs), e.g. `/home/<you>/.var/app/com.spotify.Client/config/spotify/prefs`. apply the `chmod` steps to the flatpak install dir & its `Apps` subfolder. |
| **snap** | not supported, snap installs are read-only. switch to apt or aur first. |

wait ~1 min after a fresh spotify install, logged in, before running spicetify.

### 2. install the theme

spicetify keeps themes in `~/.config/spicetify/Themes/` by default. copy the `Throwback` folder there:

```bash
mkdir -p ~/.config/spicetify/Themes
cp -r Throwback ~/.config/spicetify/Themes/
```

or symlink it so repo edits show up right away (handy with `npm run watch`):

```bash
ln -s "$PWD/Throwback" ~/.config/spicetify/Themes/Throwback
```

### 3. enable the theme

```bash
spicetify config current_theme Throwback
spicetify apply
```

### after a spotify update

updates overwrite the patched files. re-apply:

```bash
spicetify restore
spicetify apply
```

## development

needs node.js.

```bash
npm install      # install sass stylelint prettier
npm run build    # compile src/scss/*.scss into Throwback/user.css
npm run watch    # rebuild on save
```

edit the scss in `src/scss/` & rebuild, don't edit `Throwback/user.css` directly. `Throwback/nowPlaying.css` is hand-written.
