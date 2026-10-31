# GD Save Keeper

Optional add-on for Geometry Dash. After you quit, it saves a readable copy of your save data. Before every launch, it puts that copy back.

> **Warning:** it overwrites the game's save files on every launch, and the readable files can contain account info. Back up your saves first, and don't share the folder.

## Install on Linux

1. Back up your saves:
   ```bash
   cp -r ~/.steam/debian-installation/steamapps/compatdata/322170/pfx/drive_c/users/steamuser/AppData/Local/GeometryDash ~/GD_manual_backup
   ```
2. Download the file and unzip it.
Download the GDKeeper.zip and unzip it, then put it inside your Geometry Dash folder.

3. Copy the files in:
   ```bash
   mkdir -p ~/GDKeeper
   cp gd_wrapper.sh gd_saves.py ~/GDKeeper/
   chmod +x ~/GDKeeper/gd_wrapper.sh
   ```
4. In Steam, set GD's Launch Options to:
   ```
   ~/GDKeeper/gd_wrapper.sh %command%
   ```
   With the Stat Editor mod, use:
   ```
   WINEDLLOVERRIDES="xinput1_4=n,b" ~/GDKeeper/gd_wrapper.sh %command%
   ```
5. Launch the game, play, and quit. It works from the next launch on.

Your data is kept in `~/GDSaveStore/`.

## Install on Windows

> Untested. Start the game with the shortcut below, not Steam's Play button.

1. Back up your saves: press `Win + R`, run `%localappdata%\GeometryDash`, and copy the `CCGameManager*.dat` files somewhere safe.
2. Save `gd_keeper.ps1` into `C:\Users\<you>\GDKeeper\`.
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
- **Windows:** delete the `readable` folder, and just use Steam's Play button again.

Not affiliated with RobTop Games.
