# GD Save Keeper

Optional add-on for Geometry Dash. It keeps readable XML copies of your save data. Before a launch, it applies those copies; after the game closes, it refreshes them.

> **Warning:** Applying a readable copy replaces the matching game save. Readable files may contain account information. Back up your saves first and never share your `GDSaveStore` folder.

Save files handled:
- `CCGameManager.dat`
- `CCGameManager2.dat`
- `CCLocalLevels.dat`
- `CCLocalLevels2.dat`

## Linux (Steam + Proton)

1. Close Geometry Dash.
2. Back up your save folder. The usual Steam location is:

   ```text
   ~/.steam/steam/steamapps/compatdata/322170/pfx/drive_c/users/steamuser/AppData/Local/GeometryDash
   ```

   Example backup command:

   ```bash
   cp -a "$HOME/.steam/steam/steamapps/compatdata/322170/pfx/drive_c/users/steamuser/AppData/Local/GeometryDash" "$HOME/GD_manual_backup"
   ```

3. Extract the ZIP directly into `~/GDKeeper`:

   ```bash
   mkdir -p "$HOME/GDKeeper"
   unzip -o "$HOME/Downloads/GDKeeper.zip" -d "$HOME/GDKeeper"
   chmod +x "$HOME/GDKeeper/gd_wrapper.sh"
   ```

   The four project files should be directly inside `~/GDKeeper/`.

4. In Steam, open Geometry Dash → Properties → General → Launch Options. Use:

   ```text
   ~/GDKeeper/gd_wrapper.sh %command%
   ```

   If you use the GD Stat Editor mod, use:

   ```text
   WINEDLLOVERRIDES="xinput1_4=n,b" ~/GDKeeper/gd_wrapper.sh %command%
   ```

5. Launch Geometry Dash from Steam, play, then quit normally. The first run creates readable copies after the game closes. Edits to those XML files are applied on the next launch.

If Steam is installed in an unusual location, set `GD_SAVE_DIR` to the full Geometry Dash save-folder path.

## Windows (Steam)

The Windows script is provided, but should be tested on your Windows setup before relying on it as your only backup.

1. Close Geometry Dash.
2. Press `Win + R`, enter `%localappdata%\GeometryDash`, and copy the folder somewhere safe.
3. Extract `GDKeeper.zip` into `%USERPROFILE%\GDKeeper\`. Make sure `gd_keeper.ps1` is directly inside that folder.
4. Create a Desktop shortcut with this target:

   ```text
   powershell.exe -NoProfile -ExecutionPolicy Bypass -File "%USERPROFILE%\GDKeeper\gd_keeper.ps1"
   ```

5. Start Geometry Dash using that shortcut, not Steam's Play button. Play and quit normally.

## Data and logs

Linux:
- `~/GDSaveStore/readable/` — readable XML copies; edit only while Geometry Dash is closed.
- `~/GDSaveStore/history/` — up to 10 recent backups per save file.
- `~/GDSaveStore/keeper.log` — actions and errors.

Windows:
- `%USERPROFILE%\GDSaveStore\readable\`
- `%USERPROFILE%\GDSaveStore\history\`
- `%USERPROFILE%\GDSaveStore\keeper.log`

## Stop using GD Save Keeper

- **Linux:** remove the Steam launch option.
- **Windows:** use Steam's Play button instead of the GD Save Keeper shortcut.

To reset readable copies, delete only the `readable` folder inside `GDSaveStore`. Keep `history` if you want to retain backups.

Main mod: https://github.com/BananaLordYT/GD-Stat-Editor

Not affiliated with RobTop Games.
