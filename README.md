# Create TFMG + Immersive Engineering Creosote Fix

KubeJS fix for a recipe conflict between:

- Create
- Create: The Factory Must Grow (TFMG)
- Immersive Engineering

on Minecraft `1.21.1 NeoForge`.

---

# Problem

When using the Create Spout with Creosote Oil, the game incorrectly crafts:

```txt
immersiveengineering:treated_wood_horizontal
```

instead of:

```txt
tfmg:hardened_planks
```

This happens because Immersive Engineering registers a conflicting `create:filling` recipe that overrides the intended TFMG recipe.

As a result, Hardened Planks become impossible to craft using the Create Spout.

---

# What this fix does

This script removes the Immersive Engineering treated wood recipe from the Create Spout.

Specifically, it removes the `create:filling` recipe that outputs:

```txt
immersiveengineering:treated_wood_horizontal
```

This means you will no longer be able to craft Immersive Engineering Treated Wood using the Create Spout.

However, this allows the original TFMG Hardened Planks recipe to work correctly again.

---

# Tested Versions

## Minecraft

- Minecraft `1.21.1`
- NeoForge

## Dependencies

- Rhino `2101.2.7-build.81`
- KubeJS `2101.7.2-build.368`
- KubeJS Create `2101.3.1-build.18`

Other versions may work, but these are the confirmed working versions.

---

# Installation

## 1. Install dependencies

Install:

- Rhino
- KubeJS
- KubeJS Create

and place the `.jar` files inside:

```txt
.minecraft/mods
```

---

## 2. Launch Minecraft once

Start the game and enter a world once.

This will generate the `kubejs` folder automatically.

Then close the game.

---

## 3. Create the script

Go to:

```txt
.minecraft/kubejs/server_scripts/
```

Create a file called:

```txt
creosote_fix.js
```

---

## 4. Paste this script

```js
ServerEvents.recipes(event => {

  event.remove({
    type: 'create:filling',
    output: 'immersiveengineering:treated_wood_horizontal'
  })

})
```

---

## 5. Reload KubeJS

Open your world and run:

```txt
/reload
```

If everything worked correctly, the chat should display:

```txt
Reloaded with no KubeJS errors!
```

---

# Result

The Create Spout should now correctly craft:

```txt
tfmg:hardened_planks
```

instead of Immersive Engineering treated wood.

---

# Important

This fix does NOT remove Immersive Engineering Treated Wood from the game.

It only removes its Create Spout recipe.

You can still craft Immersive Engineering Treated Wood using Immersive Engineering's intended crafting methods.

This fix also does NOT add a new Hardened Planks recipe.

The original TFMG recipe already exists and starts working again automatically after the conflicting recipe is removed.

---

# Repository Structure

```txt
create-tfmg-immersive-creosote-fix/
├── README.md
└── kubejs/
    └── server_scripts/
        └── creosote_fix.js
```

---

# Credits

Created after troubleshooting a Create + TFMG + Immersive Engineering compatibility issue on NeoForge 1.21.1.
Fix discovered and documented by DasTropi.
