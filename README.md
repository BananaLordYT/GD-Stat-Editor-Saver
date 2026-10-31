# GD Save Keeper

Optional add-on for GD Stat Editor. After you quit Geometry Dash, it saves a readable copy of your save data. Before every launch, it puts that copy back.

> **Warning:** it overwrites the game's save files on every launch, and the readable files can contain account info. Back up your saves first, and don't share the folder.

First, download this repo: click **Code → Download ZIP** on this page and unzip it.

## Install on Linux

1. Back up your saves:
   ```bash
   cp -r ~/.steam/steam/steamapps/compatdata/322170/pfx/drive_c/users/steamuser/AppData/Local/GeometryDash ~/GD_manual_backup
   ```
2. Copy the files in (this assumes the ZIP is in your Downloads folder):
   ```bash
   unzip -o ~/Downloads/GD-Stat-Editor-Saver-main.zip -d /tmp/gdkeeper
   mkdir -p ~/GDKeeper
   cp /tmp/gdkeeper/*/gd_wrapper.sh /tmp/gdkeeper/*/gd_saves.py ~/GDKeeper/
   chmod +x ~/GDKeeper/gd_wrapper.sh
   ```
3. In Steam, set GD's Launch Options to:
   ```
   WINEDLLOVERRIDES="xinput1_4=n,b" ~/GDKeeper/gd_wrapper.sh %command%
   ```
   (Without the Stat Editor mod, you can use just `~/GDKeeper/gd_wrapper.sh %command%`.)
4. Launch the game, play, and quit. It works from the next launch on.

Your data is kept in `~/GDSaveStore/`.

## Install on Windows

> Untested. Start the game with the shortcut below, not Steam's Play button.

1. Back up your saves: press `Win + R`, run `%localappdata%\GeometryDash`, and copy the `CCGameManager*.dat` files somewhere safe.
2. Copy `gd_keeper.ps1` from the unzipped repo into `%USERPROFILE%\GDKeeper\`.
3. Make a shortcut (right-click Desktop → New → Shortcut) with this target:
   ```
   powershell -ExecutionPolicy Bypass -File "%USERPROFILE%\GDKeeper\gd_keeper.ps1"
   ```
4. Launch GD from that shortcut, play, and quit. It works from the next launch on.

Your data is kept in `%USERPROFILE%\GDSaveStore\`.

## Where things go

- `readable/`: readable XML copies. You can edit them while the game is closed.
- `history/`: your 10 most recent old saves.
- `keeper.log`: what happened, and any errors.

## Stop or reset

- **Linux:** `rm -r ~/GDSaveStore/readable`, and remove the launch option.
- **Windows:** delete the `readable` folder, and use Steam's Play button again.

Main mod: https://github.com/BananaLordYT/GD-Stat-Editor

Not affiliated with RobTop Games.
