# godot-blue-zinc-pelican

## 1. Description

[Godot Blue Zinc Pelican](https://github.com/fernandolv33/lowpoly-chmaker) is a low poly character generator and editor for Godot. It allows you to generate random characters at runtime, or edit and save specific characters for later use in your game.

The package includes:

- The character editor `res://character_maker/scenes/npc_editor.tscn`
- Nodes to deploy the characters into your own scenes:
  - `res://character_maker/nodes/npc_game.tscn`
  - `res://character_maker/nodes/npc_random.tscn`
- A blender file containing the source assets used by the character generator.
- Additional nodes, scripts and bitmaps.

## 2. Compatibility

- Compatible with Godot 4.2 pre-release

## 3. Installation

To install, copy the folder `character_maker` and all its contents into your Godot project. Add the file `res://character_maker/scripts/npc_maker.gd` as auto-load into your project settings.

To create a custom character, run the scene `res://character_maker/scenes/npc_editor.tscn`. Press male and female buttons to generate random characters. Use the scene controls to customize the character. Give a name and press "Save" to save the character. Characters are stored into the folder `res://character_maker/data`. NPC files have the extension `.npc`

> **Note:** Avoid using spaces, special characters, or extended characters in the NPC file name. You may use any combination of lowercase letters, numbers, hyphens and underscores.

## 4. Using the characters in your game

### 4.1 Adding a random NPC

Add an instance of the node `res://character_maker/nodes/npc_random.tscn` into your scene. Use the node parameters to define the specific characteristics of the NPC you want to generate.

### 4.2 Adding a specific NPC

Generate a NPC file using the character maker editor. Run the scene `res://character_maker/scenes/npc_editor.tscn`. Add an instance of the node `res://character_maker/nodes/npc_game.tscn` into your scene. Use the field NPC_file to select the NPC. Ensure that the npc file is located in the `res://character_make/data` folder. You may use the randomize_npc option to generate a random character that uses the same clothes combination as a saved npc.

> **Note:** Remember to add the npc data files into your project build!

## 5. Customization

The Low Poly Character Maker for Godot can be customized to fit your project needs.

### 5.1 Adding new npc colours

You can add new skin, eyes, mouth and hair colours. The new colours will be automatically used by the random npc generator, in the editor and in the game.

- Edit the file `res:/character_maker/scripts/npc_maker.gd` and add the new colours in the constant PERSONA data structure.

### 5.2 Adding new clothes palettes

To ensure that randomly generated characters use acceptable color combinations, different palettes of valid color combinations have been defined. NPC clothing generates slight variations on the predefined palettes.
To add a new colour palette:

- Edit the file `res:/character_maker/scripts/npc_maker.gd` and add the new colour palette in the constant STYLE data structure. Then add the palette name in the constant STYLES data structure.
- Edit the file `res:/character_maker/scripts/npc_random.gd` and add the new colour palette as export var bool and inside the \_ready() function.

### 5.3 Adding new clothes, complements and animations to the actual base meshes

- Edit the Blender file `res://character_maker/blender/ch_maker.blend` to add new clothes, complements and/or animations.
- Export the male and female characters as binary gltf. Use the names chmaker_female.glb and chmaker_male.glb
- Copy and replace the files chmaker_female.glb and chmaker_male.glb into the folder `res:/character_maker/meshes`
- Edit the file `res:/character_maker/scripts/npc_maker.gd` and add the new clothes, complements and animations into the directory BODY_PARTS.

### 5.4 Replacing the base models

- Look at the structure of the Blender file `res://character_maker/blender/ch_maker.blend`. You have to replicate the mesh structure of the male and female models you want to use.
- Generate new glb files.
- Generate new inherited nodes from the glb files. Replicate the structure of the nodes chmaker_male.tscn or chmaker_male.tscn.
- Edit the nodes chmaker_game.tscn and chmaker_random.tscn to generate instances of your new nodes.

## 6. License

See LICENSE
