

# 🛠️ ox_doorlock - Native QBCore Inventory Fork by Chelo

🌍 **[English Version](#english-version)** | 🇩🇪 **[Deutsche Version](#deutsche-version)**

---

## <a name="english-version"></a> 🌍 English Version

### What is this fork?
This fork modifies the standard `ox_doorlock` to fully support **native QBCore inventories** (such as `qb-inventory`, `lj-inventory`, or `ps-inventory`). 

Even when configured for QBCore, the original script attempts to check for required items (like keycards or lockpicks) using the `ox_inventory:Search()` export. If you don't use `ox_inventory`, this results in the following console error:
`SCRIPT ERROR: @ox_doorlock/server/main.lua: No such export Search in resource ox_inventory`

✅ **Tested and Proven:** This fix is 100% functional and is currently actively used on the **[ParadoX-RP.com](https://paradox-rp.com) Roleplay Server**.

### What was changed?
- Replaced `ox_inventory:Search()` with the native `Player.Functions.GetItemByName()` for all door item checks.
- Replaced `ox_inventory:RemoveItem()` with the native `Player.Functions.RemoveItem()` (e.g., when a lockpick breaks).
- Fixed the internal `GetPlayer` overwrite issue that caused `attempt to index a nil value (field 'Functions')` errors during item validation.

### Installation
1. Delete your existing `ox_doorlock` folder.
2. Download this forked version and drop it into your resources folder.
3. **IMPORTANT - UI BUILD:** Because this is a code fork, it does not include the compiled UI. You **must** download the latest official release from [overextended/ox_doorlock/releases](https://github.com/overextended/ox_doorlock/releases/latest), copy the `web` folder from that zip file, and paste it into this resource.
4. Rename the folder to exactly `ox_doorlock` (otherwise it will cause errors).
5. Configure your doors as usual.
6. **Important:** Restart your entire server. Do not use `ensure ox_doorlock` while the server is running, as it will cause `ox_lib` callback errors.

---
### Original Documentation & API
*This script requires `oxmysql`, `ox_lib` (v2.3.0+), and a target system (`ox_target` preferred).*

**Usage:**
Use the `/doorlock` command to open the UI and enter the settings for your new door. Once confirmed, activate your targeting resource (typically LALT) to select the entity (or entities) to use.

**Client API:**
```lua
exports.ox_doorlock:useClosestDoor()
exports.ox_doorlock:pickClosestDoor()

```

**Server API:**

```lua
local mrpd_locker_rooms = exports.ox_doorlock:getDoor(1)
local mrpd_locker_rooms = exports.ox_doorlock:getDoorFromName('mrpd locker rooms')

-- Set door state (0: unlocked, 1: locked)
TriggerEvent('ox_doorlock:setState', mrpd_locker_rooms.id, state)

```

---

---

## <a name="deutsche-version"></a> 🇩🇪 Deutsche Version

### Was ist dieser Fork?

Dieser Fork modifiziert das Standard `ox_doorlock` Skript, um **native QBCore Inventare** (wie `qb-inventory`, `lj-inventory` oder `ps-inventory`) vollständig zu unterstützen.

Selbst wenn das originale Skript auf QBCore eingestellt ist, versucht es, benötigte Items (wie Keycards oder Dietriche) über den `ox_inventory:Search()` Export abzufragen. Wenn man kein `ox_inventory` nutzt, führt das zu folgendem Fehler:
`SCRIPT ERROR: @ox_doorlock/server/main.lua: No such export Search in resource ox_inventory`

✅ **Getestet und Bewährt:** Dieser Fix funktioniert zu 100 % und wird aktuell aktiv auf dem **[ParadoX-RP.com](https://paradox-rp.com) Roleplay Server** eingesetzt.

### Was wurde geändert?

* `ox_inventory:Search()` wurde durch die native Funktion `Player.Functions.GetItemByName()` für alle Item-Checks ersetzt.
* `ox_inventory:RemoveItem()` wurde durch `Player.Functions.RemoveItem()` ersetzt (z.B., wenn ein Dietrich abbricht).
* Ein Überschreibungsproblem mit `GetPlayer` wurde behoben, welches bei der Item-Validierung den Fehler `attempt to index a nil value (field 'Functions')` auslöste.

### Installation

1. Lösche deinen aktuellen `ox_doorlock` Ordner vom Server.
2. Lade diesen Fork herunter und ziehe ihn in deinen Ressourcen-Ordner.
3. **WICHTIG - UI BUILD:** Da dies ein Code-Fork ist, fehlt die fertig gerenderte Benutzeroberfläche. Du **musst** das offizielle Release von [overextended/ox_doorlock/releases](https://www.google.com/url?sa=E&source=gmail&q=https://github.com/overextended/ox_doorlock/releases/latest) herunterladen, den Ordner namens `web` aus der Zip-Datei kopieren und in diese Ressource einfügen.
4. Benenne den Hauptordner exakt in `ox_doorlock` um (sonst gibt es Skript-Fehler).
5. Richte deine Türen wie gewohnt ein.
6. **Wichtig:** Starte deinen kompletten Server neu. Nutze **niemals** den Befehl `ensure ox_doorlock` im laufenden Betrieb, da dies zu `ox_lib` Callback-Fehlern führt.

---

### Original Dokumentation & API

*Dieses Skript benötigt `oxmysql`, `ox_lib` (v2.3.0+) und ein Target-System (bevorzugt `ox_target`).*

**Nutzung:**
Nutze den Befehl `/doorlock`, um das UI zu öffnen und die Einstellungen für deine Tür vorzunehmen. Danach nutzt du dein Target-System (meistens LALT), um die Tür(en) auszuwählen.

**Client API:**

```lua
exports.ox_doorlock:useClosestDoor()
exports.ox_doorlock:pickClosestDoor()

```

**Server API:**

```lua
local mrpd_locker_rooms = exports.ox_doorlock:getDoor(1)
local mrpd_locker_rooms = exports.ox_doorlock:getDoorFromName('mrpd locker rooms')

-- Tür-Status setzen (0: auf, 1: zu)
TriggerEvent('ox_doorlock:setState', mrpd_locker_rooms.id, state)

```

```
