# Documentation Proper
***
# Text Global

> `kompanion://edit/global`

###### Parameters
1. `name`— A unique name for your text global. You'll be using this in order to fetch its value. Refrain from using special characters.
2. `text`*[OPTIONAL]* — The initial value inside the text box. Default value is nothing so the textbox will be empty.

###### Extra Info

The `Text Global` feature allows you to enter values in a textbox without going inside KLWP. 

###### Fetching

1. `global_[name]`— Getting the value inside the textbox: 

***

# Image Global

> `kompanion://edit/image`

###### Parameters

1. `name`— A unique name for your image global. You'll be using this in order to fetch its wallpaper link. Refrain from using special characters. If it's a wallpaper, please use `wallpaper` for the name for inter-theme compatibility.
2. `generatepalette`*[OPTIONAL]* — Input `true` if you want to generate a color palette from the image you sent. Defaults to `false`.
3. `maxcolors`*[OPTIONAL]* — Limits the amount of colors when generating a palette. Defaults to `6`. Cannot be zero otherwise it will throw an error. The palette you generate will not always yield this amount of colors. 
4. `delimiter`*[OPTIONAL]* — When opting in for a palette, it returns a value that looks like this with the default delimiter of `~~`: `#FFFFFF~~#FFFFFF~~#FFFFFF`. The delimiter allows you to customize the default delimiter `~~` if want to. Use with `tc(split, palette, index)` in order to split the palette and get a specific color using an index.

###### Extra Info

The `Image Global` feature allows you to apply an image without going inside Kustom apps. If you choose want to, you could also generate a palette from the image you gave.

###### Fetching

1. `image_[name]`— Getting the link of the image you applied. Use inside the `Bitmap` formula.
2. `wallpaper`— Getting the link of the image with the `name` set to `wallpaper`. Use inside the `Bitmap` formula. **Please only use this for wallpapers.**
3. `image_[name]_palettesize`— The amount of colors that the palette generator got. Will not exceed the `maxcolors` parameter. Its value can be lower than `maxcolors`. Please plan ahead. 
4. `image_[name]_palette`— Returns the entire palette, separated with the value indicated in the `delimiter` parameter. *(See Image Global Parameter: delimiter)*

***

# App Global

#### Opening an app

>kompanion://open/app

#### Editing an app

>kompanion://edit/app

###### Parameters

1.`index` — The index of the app youre trying to edit/open. Use with `si(mindex)` for scalability. Indexes start at `0` 

###### Extra Info

The `App Global` allows you to edit and open apps. It takes care of touch actions, changing the app icon and applying an icon pack for you automatically. 

When opening an App Global with an index that is not linked to any app, a window will pop up allowing you to set one up. An App Global with an index that is linked to an app that was uninstalled with also pop up a window that will allow you to reconfigure it.

###### Fetching

1. `app[index]_name` — The name of the app you set it to.
2. `app[index]_appIcon` — The app icon of the app you set it to. If there is an icon pack, it will use that instead of the default icon pack.
3. `app[index]_packageName` — The package name of the app you set it to.

***

# Hex Color Global

> kompanion://edit/hex

###### Parameters

1. `name` — The unique name of your hex global. You'll be using this in order to fetch its hex color. Refrain from using special characters.
2. `color`*[OPTIONAL]* — The initial value of the hex picker. Defaults to `black`. Remove the `#` of the color using `tc(reg, color, "#", "")` because it breaks it.

###### Extra Info

The `Hex Color Global` feature allows you to set hex color without going inside Kustom apps.

###### Fetching

1. `hex_[global]` — Getting the hex color that you set it to.

***

# Icon Pack Global

> kompanion://edit/iconpack

###### Parameters

None

###### Extra Info

The `Icon Pack Global` feature allows the `App Global` feature to use icon packs instead of its default icons. You can set a primary and a secondary icon pack. When the primary doesnt support an app, the secondary icon will try to take its place. If the primary and secondary doesn't support it, the default icon is used instead.

###### Fetching

None

***

# Cutout and Notch Sizing

> kompanion://edit/sizes

###### Parameters

None

###### Extra Info

The `Cutout and Notch Sizing` feature can help themers create custom status bars and navigation bars. This is a fairly automatic process for phones without notches, but its very simple to set up.

###### Fetching

1. `sbSize` — The statusbar size in Kustom Units. No need to convert it.
2. `hasCutout` — Returns `1` if the phone has a cutout, otherwise `0`.
3. `sbCutoutPos` — Returns `Center`, `Left`, or `Right`, depending on the cutout position. When setting the cutout type as Notch, the cutout position is automatically set to `Center`
4. `sbCutoutSize` — the width of the cutout in Kustom Units.
5. `nbSize` — The height of the navigation bar in Kustom Units.

***

# Tracking

> kompanion://edit/tracker

###### Parameters

1. `name` — The name of what you are tracking. Keep it as simple as possible like `coffee`, `pushups`, `water`. 
1. `target` — The target amount of what you are tracking.
3. `append` — The amount you are adding to the tracker. Can accept negative values to subtract.
2. `anim`*[OPTIONAL]* — Will return `1` when you reach your, target allowing you to show some sort of accomplishment screen. Default to nothing.

###### Extra Info

The `Tracking` feature allows you to keep track on stuff like the glasses of water you drank today.

###### Fetching

>Note: Use `df(YYYY.mm.dd)` Kustom formula for ease. 

1. `track_[name]_YYYY.MM.DD` — Get the last amount it was set to for a specific date.
2. `track_[name]_YYYY.MM.DD_anim` — Returns `1` or `0` depending if you reached that days' goal. 
3. `track_[name]_timestamp` — Returns a Kustom-compatible timestamp `(y****M**d**h**m**s**)`. Use with `tf()` in order to show the time you last time you updated your tracker.
