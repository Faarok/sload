<span style="color: #d63e36;">S.L.O.A.D - Skyrim Logical Outfitting and Armament Diversification</span>
==================================================================

# <span style="color: #E4B60A;">Summary</span>
* [1. What is it ?](#intro)
* [2. How does it works ?](#work)
* [3. How to use it ?](#use)
    * [3.1 Tools](#use-tools)
    * [3.2 Example](#use-example)
* [4. Appendix](#appendix)
    * [4.1 List of edits](#edits)
        * [Global](#edits-global)
        * [Stormcloaks](#edits-stormcloak)
        * [Wanderer Encounter](#edits-wanderer-encounter)
    * [4.2 List of LLs](#lls)
        * [Breton stuff](#lls-breton-stuff)
        * [Stormcloaks](#lls-stormcloak)
        * [Redoran](#lls-redoran)
        * [Wanderer Encounter](#lls-wanderer-encounter)
    * [4.3 List of outfits](#outfits)
        * [Stormcloaks](#outfits-stormcloak)
        * [Redoran](#outfits-redoran)
        * [Bandits](#outfits-bandits)
        * [Wanderer Encounter](#outfits-wanderer-encounter)


# <span style="color: #E4B60A;" id="intro">1. What is it ?</span>
**S.L.O.A.D** is a mod based on a plugin and SkyPatcher, designed to completely simplify the management of NPC equipment.

The idea came to me when I wanted to change the outfit of Ravenrock's guards. If I wanted to combine two mods, I had to make a patch. Which is a bit silly, since that's what SkyPatcher is for. But since the guards weren't using a leveled list, but a "hard coded" outfit, I needed a solution.

So I decided to modify part of this system in Skyrim.

The idea is simple:
* An outfit
* A levelled list, which will manage all sublists
* Sublists of sublists... etc.

Like this:

<span id="example">
<img src="https://i.ibb.co/S7chr50/image.png" alt="Screenshot">

However, after a while, I noticed a few things I didn't like about the game, notably the lack of diversity in the distribution of weapons and outfits, as well as the way certain distributions were carried out. Not to mention the fact that, in my humble opinion, certain distributions make no sense at all.
So **S.L.O.A.D** brings its share of fixes. Of course, if some of them don't suit you, you're free to "deactivate" them by commenting / deleting the linked line in the SkyPatch `.ini' files. That's how practical **S.L.O.A.D** is.


# <span style="color: #E4B60A;" id="work">2. How does it works ?</span>
All you have to do is create your line in a SkyPatcher `.ini`, in order to add items to an existing list, or to add a new, leveled list to the outfit.
Using the previous image as an example, let's take an NPC who uses the OTFT `outfit`.
This `outfit` includes a `MainLL` leveled list.
The NPC itself can have one or more leveled lists (`MainSubLL`, `CustomSubLL1`, etc.).

It's now much easier to inject a mod's outfit or weapons without having to say good-bye to vanilla outfits, since leveled lists serve directly as outfits.
The advantage of these leveled sub-lists is also that you can mix and match elements from the vanilla game and one or more mods.
This also offers the possibility of integrating your own leveled lists.


# <span style="color: #E4B60A;" id="use">3. How to use it ?</span>
## <span style="color:teal;" id="use-tools">3.1 Tools</span>
First of all, I would **_heavily_** recommend you to use a code editor such as [Visual Studio Code](https://code.visualstudio.com/), [Sublime Text](https://www.sublimetext.com/), or **at least** [Notepad++](https://notepad-plus-plus.org/downloads/) to edit files. <br>
Why? Simply better than bloc-note.

You'll probably need [xEdit](#https://www.nexusmods.com/skyrimspecialedition/mods/164) to get further information about the plugin.

## <span style="color:teal;" id="use-example">3.2 Example</span>
For this example, I'll be using the [Stormcloak Einherjar Armor](https://www.nexusmods.com/skyrimspecialedition/mods/100787) mod from [PrincessAries](https://next.nexusmods.com/profile/PrincessAries/about-me?gameId=1704).

This mod adds three weapons:
* Warhammer
* Battleaxe
* Waraxe

As well as a set of armor, of which the cape and helmet have two variants each.

I've grouped the boots, armor, gauntlets and the two leveled lists for helmet and cape in one patch (personal choice of 50% chance distribution).

Now, I'd like Stormcloaks commanders to have the **possibility** of equipping themselves with them, which means I don't want to make the vanilla armor they wear disappear, nor the vanilla weapons.

To this end, I'm going to create a `.ini` file, which will contain the following lines:

```ini
; LOutfitStormcloakOfficer [LVLI:FE080800]
; LItemsEinherjarArmor [LVLI:FE082800]
filterByLLs=Skyrim_Logical_Outfit_and_Armament_Diversification.esp|800:addToLLs=EinherjarArmors - Distribution.esp|800~18~1
```

> *<u>Note</u>: More details and explanations can be found in the [SkyPatcher](https://www.nexusmods.com/skyrimspecialedition/mods/106659?tab=articles) documentation by [Zzyxzz](https://next.nexusmods.com/profile/Zzyxzz/about-me?gameId=1704)*.

Let's break this down a little:
* `LOutfitStormcloakOfficer [LVLI:FE080800]` is the leveled list represented by `MainLL` in our [example image](#example)
* `LItemsEinherjarArmor [LVLI:FE082800]` is the leveled list containing the armor of the **Stormcloak Einherjar Armor** mod we saw above. It is the equivalent of `CustomSubLL1`.
* We add this last levelled list to our main levelled list, so that we find the structure `MainLL` → `MainSubLL`, `CustomSubLL1`.

From now on, Stormcloaks commanders will have, randomly, the vanilla outfit or the armor added by **Stormcloak Einherjar Armor**.

> *<u>Note</u>: The concept is exactly the same with weapons.*


# <span style="color: #E4B60A;" id="appendix">4. Appendix</span>
## <span style="color: teal;" id="edits">4.1 Edits</span>
> *<u>Note</u>: Feel free to explore SkyPatches with this data, where it is also repeated for easier navigation. CC Content may be added to LLs. Don't worry if you don't have them, you won't have any issue since they're SkyPatched, and not rough edited in the plugin.*

<details>
<summary id="edits-global" style="color: #3BA5EA;">Global</summary>

*   <details>
    <summary>Thomas now know the spell "Fireball" as stated in his note :</summary>

    ```ini
    ; dunBleakFallsCorpseBretonThomas "Thomas" [NPC_:000C3B25]
    ; ADD SPELL ↓
    ; Fireball "Fireball" [SPEL:0001C789]
    ```
    </details>
*   <details>
    <summary>Pelagius the Suspicious now wear plated steel armor, instead of a dwemer one</summary>

    ```ini
    ; dunBluePalacePelagiusSuspicious "Pélagius le Méfiant" [NPC_:0009B287]
    ; REPLACE OUTFIT BY ↓
    ; ArmorSteelPlateNoHelmetOutfit [OTFT:000579A3]
    ```
    </details>
*   <details>
    <summary>Lisette now use Breton equipment</summary>

    ```ini
    ; Lisette "Lisette" [NPC_:00013297]
    ; LItemsBretonDagger [LVLI:FE04384E]
    ; OutfitWESpellswordBretonNoHelmet [OTFT:FE04384D]
    ```
    </details>
*   <details>
    <summary>Eola now use Breton equipment</summary>

    ```ini
    ; Eola "Eola" [NPC_:0001990F]
    ; SublistBretonWeapons1HSword [LVLI:FE04383E]
    ; LItemsBretonMarksmann [LVLI:FE043875]
    ; OutfitWESpellswordBretonNoHelmet [OTFT:FE04384D]
    ```
    </details>
*   <details>
    <summary>Erwan now use Breton bandit equipment</summary>

    ```ini
    ; ccBGSSSE051_Erwan "Erwan" [NPC_:FE03281C] (ccbgssse051-ba_daedricmail.esl)
    ; REPLACE OUTFIT BY ↓
    ; OutfitBanditBreton [OTFT:FE043850]
    ```
    </details>
</details>

<details>
    <summary id="edits-stormcloak" style="color: #3BA5EA;">Stormcloaks</summary>

*   <details>
    <summary>Stormcloaks now use :</summary>

    *   <details>
        <summary>Long bow, Hunting bow, and Iron and Steel arrows :</summary>

        * `LItemsStormcloakBow [LVLI:FE080813]`
        </details>
    *   <details>
        <summary>Iron and steel shields (+ Stormcloak shield for guards) and weapons (1H and 2H) :</summary>

        * `SubListStormcloak2H [LVLI:FE00080B]`
        * `SubListStormcloak1H [LVLI:FE00080A]`
        * `SubListStormcloakShield [LVLI:FE080809]`
        * `SubListStormcloakGuardShield [LVLI:FE000825]` *(a special one for guards)*
        </details>
    *   <details>
        <summary>See :</summary>

        * `CWSoldierSonsGearNoTorch [LVLI:0010AA4E]`
        * `CWSoldierSonsGear [LVLI:000A6E7A]`
        </details>
    </details>
*   <details>
    <summary>Stormcloak guards now use their own outfit and own items :</summary>

    * `OutfitStormcloakGuard [OTFT:FE080826]`
    * `LItemsStormcloakGuardGear [LVLI:FE080827]`
    </details>
*   <details>
    <summary>Stormcloak soldiers and guards now use iron, steel, leather, hide, fur (stormcloak version) and scaled boots / gauntlets</summary>

    * `LItemsStormcloakSoldier [LVLI:FE080818]`
    </details>
*   <details>
    <summary>Stormcloak soldiers now use iron, steel, leather, hide and scaled helmet</summary>

    * `LItemsStormcloakGuard [LVLI:FE08081E]`
    </details>
</details>

<details>
    <summary id="edits-wanderer-encounter" style="color: #3BA5EA;">Wanderer Encounter</summary>

*   <details>
    <summary>Breton spellsword and Breton aggressive Adventurer now use :</summary>

    *   <details>
        <summary>A custom outfit :</summary>

        * `OutfitWESpellswordBreton [OTFT:FE043828]`
        * With it, Breton spellsword / aggressive Adventurer use circlet **or** hood, with heavy boots and gauntlets, and mage robe **or** heavy armor.
        * CC content is integrated in a lore-friendly way.
        </details>
    * Only iron, steel, steel plate and ebony stuff, including weapons (no Marksmann stuff)
    * Enchanted rings and neckless (25% chance, vanilla LLs)
    </details>
*   <details>
    <summary>Taron Breton mercenary now use :</summary>

    *   <details>
        <summary>A custom outfit :</summary>

        * `OutfitWESpellswordBreton [OTFT:FE043828]`
        * With it, Breton Taron Breton mercenary use circlet **or** hood, with heavy boots and gauntlets, and mage robe **or** heavy armor.
        * CC content is integrated in a lore-friendly way.
        </details>
    * Only iron, steel, steel plate and ebony stuff
    * Iron, steel, and ebony Marksmann stuff, two handed weapon and dagger
    * Enchanted rings and neckless (25% chance, vanilla LLs)
    </details>
</details>


## <span style="color: teal;" id="lls">4.2 List of LLs</span>
> *<u>Note</u>: Feel free to use this data in xEdit or to explore SkyPatches, where it is also repeated for easier navigation.*<br>
>**Legend** :<br>
>* <span style="color: #00a822;">FormID</span> → Vanilla content<br>
>* <span style="color: orange;">FormID</span> → CC / AE content, added with SkyPatcher<br>

<details>
<summary id="lls-breton-stuff" style="color: #3BA5EA;">Breton stuff</summary>

*   <details>
    <summary>SublistBretonMageRobes [LVLI:FE043832]</summary>

    * <span style="color: #00a822;">LItemRobesCollegeMagickaRegen [LVLI:00016E22]</span>
    * <span style="color: #00a822;">LItemRobesConjuration [LVLI:0010F9B0]</span>
    * <span style="color: #00a822;">LItemRobesDestruction [LVLI:0010F9B1]</span>
    </details>
*   <details>
    <summary>SublistBretonCuirassHeavy [LVLI:FE04382D]</summary>

    *   <details>
        <summary>SublistEnchBretonCuirassHeavy [LVLI:FE042841] <b>*3</b></summary>

        * <span style="color: #00a822;">SublistEnchArmorIronCuirass01 [LVLI:0007A82F]</span>
        * <span style="color: #00a822;">SublistEnchArmorIronCuirass02 [LVLI:000B5088]</span>
        * <span style="color: #00a822;">SublistEnchArmorIronCuirass03 [LVLI:000B5089]</span>
        * <span style="color: #00a822;">SublistEnchArmorBandedIronCuirass01 [LVLI:000B5094]</span>
        * <span style="color: #00a822;">SublistEnchArmorBandedIronCuirass02 [LVLI:000B5095]</span>
        * <span style="color: #00a822;">SublistEnchArmorBandedIronCuirass03 [LVLI:000B5096]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelCuirass01 [LVLI:000B50FB]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelCuirass02 [LVLI:000B50FC]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelCuirass03 [LVLI:000B50FD]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelPlateCuirass02 [LVLI:00092A0C]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelPlateCuirass03 [LVLI:00092A0D]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelPlateCuirass04 [LVLI:00092A0E]</span>
        * <span style="color: #00a822;">SublistEnchArmorEbonyCuirass03 [LVLI:000FD99F]</span>
        * <span style="color: #00a822;">SublistEnchArmorEbonyCuirass04 [LVLI:000FD9A0]</span>
        * <span style="color: #00a822;">SublistEnchArmorEbonyCuirass05 [LVLI:000FD9A1]</span>
        </details>
    * <span style="color: #00a822;">ArmorIronCuirass "Armure de fer" [ARMO:00012E49]</span> \*4
    * <span style="color: #00a822;">ArmorIronBandedCuirass "Armure de fer renforcée" [ARMO:00013948]</span> \*2
    * <span style="color: #00a822;">ArmorSteelCuirassA "Armure d'acier" [ARMO:00013952]</span> \*4
    * <span style="color: #00a822;">ArmorSteelPlateCuirass "Armure de plates" [ARMO:0001395C]</span> \*3
    * <span style="color: #00a822;">ArmorEbonyCuirass "Armure d'ébonite" [ARMO:00013961]</span> \*2
    * <span style="color: orange;">ccBGSSSE052_ArmorBladesCuirass "Armure de plates de fer" [ARMO:FE023801]</span>
    * <span style="color: orange;">ccBGSSSE058_ArmorBladesCuirass "Armure d'acier de soldat" [ARMO:FE025801]</span>
    * <span style="color: orange;">ccBGSSSE063_ArmorBladesCuirass "Armure de plates d'ébonite" [ARMO:FE02C801]</span>
    * <span style="color: orange;">ccEDHSSE002_ArmorSplKntIronCuirass "Armure de fer de chevalier-sorcier" [ARMO:FE02AD78]</span>
    * <span style="color: orange;">ccEDHSSE002_ArmorSplKntSteelCuirass "Armure d'acier de chevalier-sorcier" [ARMO:FE02AD74]</span>
    * <span style="color: orange;">ccEDHSSE002_ArmorSplKntEliteCuirass "Armure d'ébonite de chevalier-sorcier" [ARMO:FE02AD7C]</span>
    * <span style="color: orange;">ccBGSSSE056_ArmorBladesCuirass "Armure d'argent" [ARMO:FE02F801]</span>
    </details>
*   <details>
    <summary>SublistBretonGauntletsHeavy [LVLI:FE04382E]</summary>

    *   <details>
        <summary>SublistEnchBretonGauntletsHeavy [LVLI:FE042842] <b>*3</b></summary>

        * <span style="color: #00a822;">SublistEnchArmorIronGauntlets01 [LVLI:0007A82D]</span>
        * <span style="color: #00a822;">SublistEnchArmorIronGauntlets02 [LVLI:000B508A]</span>
        * <span style="color: #00a822;">SublistEnchArmorIronGauntlets03 [LVLI:000B508B]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelPlateGauntlets02 [LVLI:00092A0F]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelPlateGauntlets03 [LVLI:00092A10]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelPlateGauntlets04 [LVLI:00092A11]</span>
        * <span style="color: #00a822;">SublistEnchArmorEbonyGauntlets03 [LVLI:000FD9A8]</span>
        * <span style="color: #00a822;">SublistEnchArmorEbonyGauntlets04 [LVLI:000FD9A9]</span>
        * <span style="color: #00a822;">SublistEnchArmorEbonyGauntlets05 [LVLI:000FD9AA]</span>
        </details>
    * <span style="color: #00a822;">ArmorIronGauntlets "Gantelets de fer" [ARMO:00012E46]</span> \*4
    * <span style="color: #00a822;">ArmorSteelGauntletsB "Brassards d'acier impériaux" [ARMO:000F6F23]</span> \*4
    * <span style="color: #00a822;">ArmorSteelPlateGauntlets "Gantelets de plates" [ARMO:0001395D]</span> \*3
    * <span style="color: #00a822;">ArmorEbonyGauntlets "Gantelets d'ébonite" [ARMO:00013962]</span> \*2
    * <span style="color: orange;">ccBGSSSE052_ArmorBladesGauntlets "Gantelets de plates de fer" [ARMO:FE023802]</span>
    * <span style="color: orange;">ccBGSSSE058_ArmorBladesGauntlets "Gantelets d'acier de soldat" [ARMO:FE025802]</span>
    * <span style="color: orange;">ccBGSSSE063_ArmorBladesGauntlets "Gantelets de plates d'ébonite" [ARMO:FE02C802]</span>
    * <span style="color: orange;">ccEDHSSE002_ArmorSplKntIronGauntlets "Gantelets de fer de chevalier-sorcier" [ARMO:FE02AD79]</span>
    * <span style="color: orange;">ccEDHSSE002_ArmorSplKntSteelGauntlets "Gantelets d'acier de chevalier-sorcier" [ARMO:FE02AD75]</span>
    * <span style="color: orange;">ccEDHSSE002_ArmorSplKntEliteGauntlets "Gantelets d'ébonite de chevalier-sorcier" [ARMO:FE02AD7D]</span>
    * <span style="color: orange;">ccBGSSSE056_ArmorBladesGauntlets "Gantelets d'argent" [ARMO:FE02F802]</span>
    </details>
*   <details>
    <summary>SublistBretonBootsHeavy [LVLI:FE04382F]</summary>

    *   <details>
        <summary>SublistEnchBretonBootsHeavy [LVLI:FE042843] <b>*3</b></summary>

        * <span style="color: #00a822;">SublistEnchArmorIronBoots01 [LVLI:0007A82C]</span>
        * <span style="color: #00a822;">SublistEnchArmorIronBoots02 [LVLI:000B5086]</span>
        * <span style="color: #00a822;">SublistEnchArmorIronBoots03 [LVLI:000B5087]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelPlateBoots02 [LVLI:00092A09]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelPlateBoots03 [LVLI:00092A0A]</span>
        * <span style="color: #00a822;">SublistEnchArmorSteelPlateBoots04 [LVLI:00092A0B]</span>
        * <span style="color: #00a822;">SublistEnchArmorEbonyBoots03 [LVLI:000FD9A5]</span>
        * <span style="color: #00a822;">SublistEnchArmorEbonyBoots04 [LVLI:000FD9A6]</span>
        * <span style="color: #00a822;">SublistEnchArmorEbonyBoots05 [LVLI:000FD9A7]</span>
        </details>
    * <span style="color: #00a822;">ArmorIronBoots "Bottes de fer" [ARMO:00012E4B]</span> \*4
    * <span style="color: #00a822;">ArmorSteelBootsB "Jambières d'acier" [ARMO:000F6F21]</span> \*4
    * <span style="color: #00a822;">ArmorSteelPlateBoots "Bottes de plates" [ARMO:0001395B]</span> \*3
    * <span style="color: #00a822;">ArmorEbonyBoots "Bottes d'ébonite" [ARMO:00013960]</span> \*2
    * <span style="color: orange;">ccBGSSSE052_ArmorBladesBoots "Bottes de plates de fer" [ARMO:FE023800]</span>
    * <span style="color: orange;">ccBGSSSE058_ArmorBladesBoots "Bottes d'acier de soldat" [ARMO:FE025800]</span>
    * <span style="color: orange;">ccBGSSSE063_ArmorBladesBoots "Bottes de plates d'ébonite" [ARMO:FE02C800]</span>
    * <span style="color: orange;">ccEDHSSE002_ArmorSplKntIronBoots "Bottes de fer de chevalier-sorcier" [ARMO:FE02AD77]</span>
    * <span style="color: orange;">ccEDHSSE002_ArmorSplKntSteelBoots "Bottes d'acier de chevalier-sorcier" [ARMO:FE02AD73]</span>
    * <span style="color: orange;">ccEDHSSE002_ArmorSplKntEliteBoots "Bottes d'ébonite de chevalier-sorcier" [ARMO:FE02AD7B]</span>
    * <span style="color: orange;">ccBGSSSE056_ArmorBladesBoots "Bottes d'argent" [ARMO:FE02F800]</span>
    </details>
*   <details>
    <summary>LItemsBretonWeapons1H [LVLI:FE042838]</summary>

    *   <details>
        <summary>SublistBretonWeapons1HSword [LVLI:FE04283E]</summary>

        *   <details>
            <summary>SublistEnchBretonWeapons1HSword [LVLI:FE042847] <b>*3</b></summary>

            * <span style="color: #00a822;">LItemEnchIronSword [LVLI:0004B580]</span>
            * <span style="color: #00a822;">LItemEnchSteelSword [LVLI:0004B583]</span>
            * <span style="color: #00a822;">LItemEnchEbonySword [LVLI:000CB3CB]</span>
            </details>
        * <span style="color: #00a822;">IronSword "Épée de fer" [WEAP:00012EB7]</span> \*4
        * <span style="color: #00a822;">SteelSword "Épée d'acier" [WEAP:00013989]</span> \*3
        * <span style="color: #00a822;">EbonySword "Épée d'ébonite" [WEAP:000139B1]</span> \*2
        * <span style="color: orange;">ccASVSSE001_EbonyScimitar "Cimeterre d'ébonite" [WEAP:05000E38]</span>
        </details>
    *   <details>
        <summary>SublistBretonWeapons1HMace [LVLI:FE042840]</summary>

        *   <details>
            <summary>SublistEnchBretonWeapons1HMace [LVLI:FE042849] <b>*3</b></summary>

            * <span style="color: #00a822;">LItemEnchIronMace [LVLI:0004B57F]</span>
            * <span style="color: #00a822;">LItemEnchSteelMace [LVLI:0004B582]</span>
            * <span style="color: #00a822;">LItemEnchEbonyMace [LVLI:000CB3CA]</span>
            * <span style="color: orange;">ccASVSSE001_EbonyMace "Masse d'ébonite" [WEAP:05000E37]</span>
            </details>
        * <span style="color: #00a822;">IronMace "Masse de fer" [WEAP:00013982]</span> \*4
        * <span style="color: #00a822;">SteelMace "Masse d'acier" [WEAP:00013988]</span> \*3
        * <span style="color: #00a822;">EbonyMace "Masse d'ébonite" [WEAP:000139B0]</span> \*2
        * <span style="color: orange;">ccASVSSE001_EbonyMace "Masse d'ébonite" [WEAP:05000E37]</span>
        </details>
*   <details>
    <summary>LItemsBretonWeapons2H [LVLI:FE042830]</summary>

    *   <details>
        <summary>SublistBretonWeapons2HGreatsword [LVLI:FE04283B]</summary>

        *   <details>
            <summary>SublistEnchBretonWeapons2HGreatsword [LVLI:FE042844] <b>*3</b></summary>

            * <span style="color: #00a822;">LItemEnchIronGreatsword [LVLI:0008992D]</span>
            * <span style="color: #00a822;">LItemEnchSteelGreatsword [LVLI:000A6A21]</span>
            * <span style="color: #00a822;">LItemEnchEbonyGreatsword [LVLI:000CB3C9]</span>
            </details>
        * <span style="color: #00a822;">IronGreatsword "Espadon de fer" [WEAP:0001359D]</span> \*4
        * <span style="color: #00a822;">SteelGreatsword "Espadon d'acier" [WEAP:00013987]</span> \*3
        * <span style="color: #00a822;">EbonyGreatsword "Espadon d'ébonite" [WEAP:000139AF]</span> \*2
        </details>
    *   <details>
        <summary>SublistBretonWeapons2HWarhammer [LVLI:FE04283D]</summary>

        *   <details>
            <summary>SublistEnchBretonWeapons2HWarhammer [LVLI:FE042846] <b>*3</b></summary>

            * <span style="color: #00a822;">LItemEnchIronWarhammer [LVLI:0008992A]</span>
            * <span style="color: #00a822;">LItemEnchSteelWarhammer [LVLI:000A6A28]</span>
            * <span style="color: #00a822;">LItemEnchEbonyWarhammer [LVLI:000CB3CD]</span>
            </details>
        * <span style="color: #00a822;">IronWarhammer "Marteau de fer" [WEAP:00013981]</span> \*4
        * <span style="color: #00a822;">SteelWarhammer "Marteau d'acier" [WEAP:0001398A]</span> \*3
        * <span style="color: #00a822;">EbonyWarhammer "Marteau d'ébonite" [WEAP:000139B2]</span> \*2
        </details>
    </details>
*   <details>
    <summary>LItemsBretonRanged [LVLI:FE0008A1]</summary>

    *   <details>
        <summary>LItemsBretonMarksmann [LVLI:FE000875]</summary>

        *   <details>
            <summary>SublistBretonBow [LVLI:FE000876]</summary>

            * <span style="color: #00a822;">LongBow "Arc long" [WEAP:0003B562]</span> x3
            * <span style="color: #00a822;">HuntingBow "Arc de chasse" [WEAP:00013985]</span> x2
            * <span style="color: #00a822;">ImperialBow "Arc impérial" [WEAP:00013841]</span> x3
            * <span style="color: #00a822;">EbonyBow "Arc d'ébonite" [WEAP:000139AD]</span> x2
            * SublistEnchBretonBow [LVLI:FE000877] x3
                * <span style="color: #00a822;">LItemEnchHuntingBow [LVLI:000AE745]</span>
                * <span style="color: #00a822;">LItemEnchImperialBow [LVLI:000AE746]</span>
                * <span style="color: #00a822;">LItemEnchEbonyBow [LVLI:000CB3C7]</span>
            </details>
        *   <details>
            <summary>SublistBretonArrow [LVLI:FE000878]</summary>

            * <span style="color: #00a822;">IronArrow "Flèche de fer" [AMMO:0001397D]</span>
            * <span style="color: #00a822;">SteelArrow "Flèche d'acier" [AMMO:0001397F]</span>
            * <span style="color: #00a822;">EbonyArrow "Flèche d'ébonite" [AMMO:000139BF]</span>
            </details>
        <details>
    *   <details>
        <summary>LItemsBretonCrossbowman [LVLI:FE00089D]</summary>

        *   <details>
            <summary>SublistBretonCrossbow [LVLI:FE00089E]</summary>

            * <span style="color: #00a822;">DLC1CrossBow "Arbalète" [WEAP:02000801]</span> x2
            * <span style="color: orange;">ccFFBSSE002_ImperialCrossbow "Arbalète impériale" [WEAP:FE00280B]</span>
            * <span style="color: orange;">ccFFBSSE002_SilverCrossbow "Arbalète d'argent" [WEAP:FE00280E]</span>
            * <span style="color: orange;">ccBGSSSE043_EbonyCrossbow "Arbalète d'ébonite" [WEAP:FE0018A6]</span>
            </details>
        *   <details>
            <summary>SublistBretonBolt [LVLI:FE0008A0]</summary>

            * <span style="color: #00a822;">DLC1BoltSteel "Carreau d'acier" [AMMO:02000BB3]</span> x3
            * <span style="color: #00a822;">DLC1LItemAmmoSteelBoltEnhancedGated [LVLI:0200F1AE]</span>
            * <span style="color: orange;">ccBGSSSE037_IronBolt "Carreau de fer" [AMMO:FE00083A]</span>
            * <span style="color: orange;">ccBGSSSE037_SilverBolt "Carreau d'argent" [AMMO:FE00083F]</span>
            </details>
        </details>
    </details>
</details>

<details>
    <summary id="lls-stormcloak" style="color: #3BA5EA;">Stormcloaks</summary>

*   <details>
    <summary>LOutfitStormcloakOfficer [LVLI:FE080800]</summary>

    *   <details>
        <summary>LItemsStormcloakOfficer [LVLI:FE080801]</summary>

        * SubListStormcloakOfficerCuirass [LVLI:FE080802]
        * SubListStormcloakOfficerGauntlets [LVLI:FE080803]
        * SubListStormcloakOfficerBoots [LVLI:FE080804]
        * SubListStormcloakOfficerHelmet [LVLI:FE080805]
        </details>
    </details>
*   <details>
    <summary>LOutfitStormcloakOfficerNoHelmet [LVLI:FE080806]</summary>

    *   <details>
        <summary>LItemsStormcloakOfficerNoHelmet [LVLI:FE080807]</summary>

        * ***Same w/o helmet***
        </details>
    </details>
*   <details>
    <summary>LItemsStormcloakWeapons [LVLI:FE080808]</summary>

    *   <details>
        <summary>SubListStormcloak2H [LVLI:FE08080B]</summary>

        * SubListStormcloak2HGreatsword [LVLI:FE080810]
        * SubListStormcloak2HBattleaxe [LVLI:FE080811]
        * SubListStormcloak2HWarhammer [LVLI:FE080812]
        </details>
    *   <details>
        <summary>SubListStormcloakShield1H [LVLI:FE08080C]</summary>

        * SubListStormcloakShield [LVLI:FE080809]
        *   <details>
            <summary>SubListStormcloak1H [LVLI:FE08080A]</summary>

            * SubListStormcloak1HSword [LVLI:FE08080D]
            * SubListStormcloak1HWaraxe [LVLI:FE08080E]
            * SubListStormcloak1HMace [LVLI:FE08080F]
            </details>
        </details>
    </details>
*   <details>
    <summary>LItemsStormcloakMarksmann [LVLI:FE080815]</summary>

    * LItemsStormcloakBow [LVLI:FE080813]
    * LItemsStormcloakArrow [LVLI:FE080814]
    </details>
* SubListStormcloakDagger [LVLI:FE080816]
*   <details>
    <summary>LOutfitStormcloakSoldier [LVLI:FE000817]</summary>

    *   <details>
        <summary>LItemsStormcloakSoldier [LVLI:FE000818]</summary>

        * SubListStormcloakSoldierCuirass [LVLI:FE000819]
        * SubListStormcloakSoldierGauntlets [LVLI:FE00081A]
        * SubListStormcloakSoldierBoots [LVLI:FE00081B]
        * SubListStormcloakSoldierHelmet [LVLI:FE00081C]
        </details>
    </details>
*   <details>
    <summary>LOutfitStormcloakGuard [LVLI:FE00081D]</summary>

    *   <details>
        <summary>LItemsStormcloakGuard [LVLI:FE00081E]</summary>

        * SubListStormcloakGuardCuirass [LVLI:FE00081F]
        * SubListStormcloakGuardGauntlets [LVLI:FE000820]
        * SubListStormcloakGuardBoots [LVLI:FE000821]
        * SubListStormcloakGuardHelmet [LVLI:FE000822]
        </details>
    </details>
*   <details>
    <summary>LItemsStormcloakGuardWeapons [LVLI:FE000823]</summary>

    * SubListStormcloak2H [LVLI:FE00080B]
    *   <details>
        <summary>SubListStormcloakGuardShield1H [LVLI:FE000824]</summary>

        * SubListStormcloak1H [LVLI:FE00080A]
        * SubListStormcloakGuardShield [LVLI:FE000825]
        </details>
    </details>
*   <details>
    <summary>LItemsStormcloakGuardGear [LVLI:FE000827]</summary>

    * ***Same as original but with S.E.X.E LLs***
    </details>
</details>

<details>
<summary style="color: #3BA5EA;" id="lls-redoran">Redoran</summary>

*   <details>
    <summary>LOutfitRedoranGuardExterior [LVLI:FE000835]</summary>

    *   <details>
        <summary>LItemsRedoranGuard [LVLI:FE000880]</summary>

        *   <details>
            <summary>SublistRedoranGuardCuirass [LVLI:FE000881]</summary>

            * <span style="color: #00a822;">DLC2ArmorBonemoldCuirassVariant02 "Armure d'ostalium" [ARMO:0401CD93]</span> x2
            * <span style="color: #00a822;">DLC2ArmorBonemoldCuirassVariant01 "Spalière d'ostalium" [ARMO:04037563]</span> x2
            * <span style="color: #00a822;">DLC2ArmorBonemoldCuirassGuard "Armure de garde d'ostalium" [ARMO:04037564]</span> x2
            *  SublistEnchRedoranGuardCuirass [LVLI:FE000885] x2
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldCuirass01 [LVLI:0402BA49]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldCuirass02 [LVLI:0402BA4B]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldCuirass03 [LVLI:0402BA4D]</span>
            </details>
        *   <details>
            <summary>SublistRedoranGuardBoots [LVLI:FE000882]</summary>

            * <span style="color: #00a822;">DLC2ArmorBonemoldBoots "Bottes d'ostalium" [ARMO:0401CD92]</span> x2
            * SublistEnchRedoranGuardBoots [LVLI:FE000886]
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldBoots01 [LVLI:0402BA43]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldBoots02 [LVLI:0402BA45]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldBoots03 [LVLI:0402BA47]</span>
            </details>
        *   <details>
            <summary>SublistRedoranGuardHelmet [LVLI:FE000883]</summary>

            * <span style="color: #00a822;">DLC2ArmorBonemoldHelmet "Casque d'ostalium" [ARMO:0401CD95]</span> x2
            * SublistEnchRedoranGuardHelmet [LVLI:FE000887]
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldHelmet01 [LVLI:0402BA55]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldHelmet02 [LVLI:0402BA57]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldHelmet03 [LVLI:0402BA59]</span>
            </details>
        *   <details>
            <summary>SublistRedoranGuardGauntlets [LVLI:FE000884]</summary>

            * <span style="color: #00a822;">DLC2ArmorBonemoldGauntlets "Gantelets d'ostalium" [ARMO:0401CD94]</span> x2
            * SublistEnchRedoranGuardGauntlets [LVLI:FE000888]
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldGauntlets01 [LVLI:0402BA4F]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldGauntlets02 [LVLI:0402BA51]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldGauntlets03 [LVLI:0402BA53]</span>
            </details>
        </details>
    </details>
*   <details>
    <summary>LOutfitRedoranGuardBulwark [LVLI:FE00088A]</summary>

    *   <details>
        <summary>LItemsRedoranGuard [LVLI:FE000880]</summary>

        *   <details>
            <summary>SublistRedoranGuardCuirass [LVLI:FE000881]</summary>

            * <span style="color: #00a822;">DLC2ArmorBonemoldCuirassVariant02 "Armure d'ostalium" [ARMO:0401CD93]</span> x2
            * <span style="color: #00a822;">DLC2ArmorBonemoldCuirassVariant01 "Spalière d'ostalium" [ARMO:04037563]</span> x2
            * <span style="color: #00a822;">DLC2ArmorBonemoldCuirassGuard "Armure de garde d'ostalium" [ARMO:04037564]</span> x2
            *  SublistEnchRedoranGuardCuirass [LVLI:FE000885] x2
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldCuirass01 [LVLI:0402BA49]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldCuirass02 [LVLI:0402BA4B]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldCuirass03 [LVLI:0402BA4D]</span>
            </details>
        *   <details>
            <summary>SublistRedoranGuardBoots [LVLI:FE000882]</summary>

            * <span style="color: #00a822;">DLC2ArmorBonemoldBoots "Bottes d'ostalium" [ARMO:0401CD92]</span> x2
            * SublistEnchRedoranGuardBoots [LVLI:FE000886]
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldBoots01 [LVLI:0402BA43]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldBoots02 [LVLI:0402BA45]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldBoots03 [LVLI:0402BA47]</span>
            </details>
        *   <details>
            <summary>SublistRedoranGuardHelmet [LVLI:FE000883]</summary>

            * <span style="color: #00a822;">DLC2ArmorBonemoldHelmet "Casque d'ostalium" [ARMO:0401CD95]</span> x2
            * SublistEnchRedoranGuardHelmet [LVLI:FE000887]
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldHelmet01 [LVLI:0402BA55]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldHelmet02 [LVLI:0402BA57]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldHelmet03 [LVLI:0402BA59]</span>
            </details>
        *   <details>
            <summary>SublistRedoranGuardGauntlets [LVLI:FE000884]</summary>

            * <span style="color: #00a822;">DLC2ArmorBonemoldGauntlets "Gantelets d'ostalium" [ARMO:0401CD94]</span> x2
            * SublistEnchRedoranGuardGauntlets [LVLI:FE000888]
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldGauntlets01 [LVLI:0402BA4F]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldGauntlets02 [LVLI:0402BA51]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldGauntlets03 [LVLI:0402BA53]</span>
            </details>
        </details>
    </details>
*   <details>
    <summary>LItemsRedoranGuardWeapons [LVLI:FE00088B]</summary>

    *   <details>
        <summary>LItemsRedoranGuardWeapons2H [LVLI:FE00088C]</summary>

        *   <details>
            <summary>SublistRedoranGuard2HGreatsword [LVLI:FE000890]</summary>

            * <span style="color: #00a822;">GlassGreatsword "Espadon de verre" [WEAP:000139A7]</span> x3
            * <span style="color: #00a822;">EbonyGreatsword "Espadon d'ébonite" [WEAP:000139AF]</span> x2
            * <span style="color: #00a822;">DaedricGreatsword "Espadon daedrique" [WEAP:000139B7]</span>
            * SublistEnchRedoranGuard2HGreatsword [LVLI:FE000891] x3
                * <span style="color: #00a822;">LItemEnchGlassGreatsword [LVLI:000CB3B7]</span>
                * <span style="color: #00a822;">LItemEnchEbonyGreatsword [LVLI:000CB3C9]</span>
                * <span style="color: #00a822;">LItemEnchDaedricGreatsword [LVLI:000CB3DB]</span>
            </details>
        </details>
    *   <details>
        <summary>LItemsRedoranGuardWeapons1H [LVLI:FE00088D]</summary>

        *   <details>
            <summary>SublistRedoranGuard1HMace [LVLI:FE000893]</summary>

            * <span style="color: #00a822;">GlassMace "Masse de verre" [WEAP:000139A8]</span> x3
            * <span style="color: #00a822;">EbonyMace "Masse d'ébonite" [WEAP:000139B0]</span> x2
            * <span style="color: #00a822;">DaedricMace "Masse daedrique" [WEAP:000139B8]</span>
            * <span style="color: orange;">ccASVSSE001_EbonyMace "Masse d'ébonite" [WEAP:05000E37]</span>
            * SublistEnchRedoranGuard1HMace [LVLI:FE000895] x3
                * <span style="color: #00a822;">LItemEnchGlassMace [LVLI:000CB3B8]</span>
                * <span style="color: #00a822;">LItemEnchEbonyMace [LVLI:000CB3CA]</span>
                * <span style="color: #00a822;">LItemEnchDaedricMace [LVLI:000CB3DC]</span>
            </details>
        *   <details>
            <summary>SublistRedoranGuard1HSword [LVLI:FE000894]</summary>

            * <span style="color: #00a822;">GlassSword "Épée de verre" [WEAP:000139A9]</span> x3
            * <span style="color: #00a822;">EbonySword "Épée d'ébonite" [WEAP:000139B1]</span> x2
            * <span style="color: #00a822;">DaedricSword "Épée daedrique" [WEAP:000139B9]</span>
            * <span style="color: orange;">ccASVSSE001_EbonyScimitar "Cimeterre d'ébonite" [WEAP:05000E38]</span>
            * SublistEnchRedoranGuard1HSword [LVLI:FE000896] x3
                * <span style="color: #00a822;">LItemEnchGlassSword [LVLI:000CB3B9]</span>
                * <span style="color: #00a822;">LItemEnchEbonySword [LVLI:000CB3CB]</span>
                * <span style="color: #00a822;">LItemEnchDaedricSword [LVLI:000CB3DD]</span>
            </details>
        </details>
    *   <details>
        <summary>LItemsRedoranGuard1HShield [LVLI:FE00088E]</summary>

        * LItemsRedoranGuardWeapons1H [LVLI:FE00088D]
        *   <details>
            <summary>SublistRedoranGuardShield [LVLI:FE00088F]</summary>

            * <span style="color: #00a822;">DLC2ArmorBonemoldShield "Bouclier d'ostalium" [ARMO:04026234]</span> x3
            * SublistEnchRedoranGuardShield [LVLI:FE000892] x3
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldShield01 [LVLI:0402BA5A]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldShield02 [LVLI:0402BA5B]</span>
                * <span style="color: #00a822;">DLC2SublistEnchArmorBonemoldShield03 [LVLI:0402BA5C]</span>
            </details>
        </details>
    </details>
*   <details>
    <summary>LItemsRedoranGuardRanged [LVLI:FE0008A3]</summary>

    *   <details>
        <summary>LItemsRedoranGuardMarksmann [LVLI:FE000897]</summary>

        *   <details>
            <summary>SublistRedoranGuardBow [LVLI:FE000898]</summary>

            * <span style="color: #00a822;">GlassBow "Arc de verre" [WEAP:000139A5]</span> x3
            * <span style="color: #00a822;">EbonyBow "Arc d'ébonite" [WEAP:000139AD]</span> x2
            * <span style="color: #00a822;">DaedricBow "Arc daedrique" [WEAP:000139B5]</span>
            * SublistEnchRedoranGuardBow [LVLI:FE000899] x3
                * <span style="color: #00a822;">LItemEnchGlassBow [LVLI:000CB020]</span>
                * <span style="color: #00a822;">LItemEnchEbonyBow [LVLI:000CB3C7]</span>
                * <span style="color: #00a822;">LItemEnchDaedricBow [LVLI:000CB3D9]</span>
            </details>
        *   <details>
            <summary>SublistRedoranGuardArrow [LVLI:FE00089A]</summary>

            * <span style="color: #00a822;">GlassArrow "Flèche de verre" [AMMO:000139BE]</span>
            * <span style="color: #00a822;">EbonyArrow "Flèche d'ébonite" [AMMO:000139BF]</span>
            * <span style="color: #00a822;">DaedricArrow "Flèche daedrique" [AMMO:000139C0]</span>
            * <span style="color: orange;">ccBGSSSE037_CorkbulbArrow "Flèche de bulbe-liège" [AMMO:FE00082F]"</span>
            </details>
        </details>
    *   <details>
        <summary>LItemsRedoranGuardCrossbowman [LVLI:FE0008A2]</summary>

        *   <details>
            <summary>SublistRedoranGuardCrossbow [LVLI:FE00089F]</summary>

            * <span style="color: #00a822;">DLC1CrossBow "Arbalète" [WEAP:02000801]</span> x2
            * <span style="color: orange;">ccFFBSSE002_GlassCrossbow "Arbalète de verre" [WEAP:FE00280A]</span>
            * <span style="color: orange;">ccBGSSSE043_EbonyCrossbow "Arbalète d'ébonite" [WEAP:FE0018A6]</span>
            * <span style="color: orange;">ccFFBSSE002_DaedricCrossbow "Arbalète daedrique" [WEAP:FE002808]</span>
            </details>
        *   <details>
            <summary>SublistRedoranGuardBolt [LVLI:FE0008A4]</summary>

            * <span style="color: #00a822;">DLC1BoltSteel "Carreau d'acier" [AMMO:02000BB3]</span> x3
            * <span style="color: #00a822;">DLC1LItemAmmoSteelBoltEnhancedGated [LVLI:0200F1AE]</span>
            * <span style="color: orange;">ccBGSSSE037_IronBolt "Carreau de fer" [AMMO:FE00083A]</span>
            * <span style="color: orange;">ccBGSSSE037_BonemoldBolt "Carreau d'ostalium" [AMMO:FE000840]</span>
            * <span style="color: orange;">ccBGSSSE037_CorkbulbBolt "Carreau de bulbe-liège" [AMMO:FE000832]</span>
            </details>
        </details>
    </details>
*   <details>
    <summary>SublistRedoranGuardDagger [LVLI:FE00089B]</summary>

    * <span style="color: #00a822;">GlassDagger "Dague de verre" [WEAP:000139A6]</span> x3
    * <span style="color: #00a822;">EbonyDagger "Dague d'ébonite" [WEAP:000139AE]</span> x2
    * <span style="color: #00a822;">DaedricDagger "Dague daedrique" [WEAP:000139B6]</span>
    * SublistEnchRedoranGuardDagger [LVLI:FE00089C] x3
        * <span style="color: #00a822;">LItemEnchGlassDagger [LVLI:000CB021]</span>
        * <span style="color: #00a822;">LItemEnchEbonyDagger [LVLI:000CB3C8]</span>
        * <span style="color: #00a822;">LItemEnchDaedricDagger [LVLI:000CB3DA]</span>
    </details>
</details>

<details>
    <summary id="lls-bandits" style="color: #3BA5EA;">Bandits</summary>

*   <details>
    <summary>LOutfitBanditBreton [LVLI:FE043851]</summary>

    *   <details>
        <summary>LItemsBanditBreton [LVLI:FE043852] <b>*4</b></summary>

        *   <details>
            <summary>SublistBanditBretonBodyGear [LVLI:FE043858]</summary>

            *   <details>
                <summary>SublistBanditBretonCuirassHeavy [LVLI:FE043859]</summary>

                *   <details>
                    <summary>SublistEnchBanditBretonCuirassHeavy [LVLI:FE04385A] <b>*3</b></summary>

                    * <strong><span style="color: #00a822;">SublistEnchArmorIronBoots01 [LVLI:0007A82C]</span>
                    * <span style="color: #00a822;">SublistEnchArmorIronBoots02 [LVLI:000B5086]</span>
                    * <span style="color: #00a822;">SublistEnchArmorIronBoots03 [LVLI:000B5087]</span></strong>
                    </details>
                * <strong><span style="color: #00a822;">ArmorIronCuirass "Armure de fer" [ARMO:00012E49]</span> *4
                * <span style="color: #00a822;">ArmorIronBandedCuirass "Armure de fer renforcée" [ARMO:00013948]</span> *2
                * <span style="color: #00a822;">ArmorSteelCuirassA "Armure d'acier" [ARMO:00013952]</span> *3</strong>
                </details>
            *   <details>
                <summary>SublistBanditBretonCuirassLight [LVLI:FE04385B]</summary>

                *   <details>
                    <summary>SublistEnchBanditBretonCuirassLight [LVLI:FE043853] <b>*3</b></summary>

                    * <strong><span style="color: #00a822;">SublistEnchArmorHideCuirass01 [LVLI:0007A831]</span>
                    * <span style="color: #00a822;">SublistEnchArmorHideCuirass02 [LVLI:000B4215]</span>
                    * <span style="color: #00a822;">SublistEnchArmorHideCuirass03 [LVLI:000B4216]</span>
                    * <span style="color: #00a822;">SublistEnchArmorLeatherCuirass01 [LVLI:000B5071]</span>
                    * <span style="color: #00a822;">SublistEnchArmorLeatherCuirass02 [LVLI:000B5072]</span>
                    * <span style="color: #00a822;">SublistEnchArmorLeatherCuirass03 [LVLI:000B5073]</span></strong>
                    </details>
                * <strong><span style="color: #00a822;">ArmorHideCuirass "Armure en peau" [ARMO:00013911]</span> *4
                * <span style="color: #00a822;">ArmorBanditCuirass "Armure de fourrure" [ARMO:0006F393]</span>
                * <span style="color: #00a822;">ArmorBanditCuirass1 "Armure de fourrure" [ARMO:0010594B]</span>
                * <span style="color: #00a822;">ArmorBanditCuirass2 "Armure de fourrure" [ARMO:0010594D]</span>
                * <span style="color: #00a822;">ArmorBanditCuirass3 "Armure de fourrure" [ARMO:0010594F]</span>
                * <span style="color: #00a822;">ArmorLeatherCuirass "Armure de cuir" [ARMO:0003619E]</span> *3</strong>
                </details>
            *   <details>
                <summary>SublistBanditBretonMageRobes [LVLI:FE043862]</summary>

                * <strong><span style="color: #00a822;">LItemNecromancerRobes [LVLI:00105252]</span>
                * <span style="color: #00a822;">LItemWarlockRobesConjuration [LVLI:00105EEC]</span>
                * <span style="color: #00a822;">LItemWarlockRobesDestruction [LVLI:00105EED]</span>
                * <span style="color: #00a822;">LItemWarlockRobesMagickaRate [LVLI:00105EEF]</span></strong>
                </details>
            </details>
        *   <details>
            <summary>SublistBanditBretonGauntlets [LVLI:FE043860]</summary>

            *   <details>
                <summary>SublistBanditBretonGauntletsHeavy [LVLI:FE043854]</summary>

                *   <details>
                    <summary>SublistEnchBanditBretonGauntletsHeavy [LVLI:FE043856] <b>*3</b></summary>

                    * <strong><span style="color: #00a822;">SublistEnchArmorIronGauntlets01 [LVLI:0007A82D]</span>
                    * <span style="color: #00a822;">SublistEnchArmorIronGauntlets02 [LVLI:000B508A]</span>
                    * <span style="color: #00a822;">SublistEnchArmorIronGauntlets03 [LVLI:000B508B]</span></strong>
                    </details>
                * **<span style="color: #00a822;">ArmorIronGauntlets "Gantelets de fer" [ARMO:00012E46]</span> \*4**
                </details>
            *   <details>
                <summary>SublistBanditBretonGauntletsLight [LVLI:FE04385C]</summary>

                *   <details>
                    <summary>SublistEnchBanditBretonGauntletsLight [LVLI:FE04385E] <b>*3</b></summary>

                    * <strong><span style="color: #00a822;">SublistEnchArmorHideGauntlets01 [LVLI:0007A832]</span>
                    * <span style="color: #00a822;">SublistEnchArmorHideGauntlets02 [LVLI:000B4217]</span>
                    * <span style="color: #00a822;">SublistEnchArmorHideGauntlets03 [LVLI:000B4219]</span>
                    * <span style="color: #00a822;">SublistEnchArmorLeatherGauntlets01 [LVLI:000B5074]</span>
                    * <span style="color: #00a822;">SublistEnchArmorLeatherGauntlets02 [LVLI:000B5075]</span>
                    * <span style="color: #00a822;">SublistEnchArmorLeatherGauntlets03 [LVLI:000B5076]</span></strong>
                    </details>
                * <strong><span style="color: #00a822;">ArmorHideGauntlets "Brassards en peau" [ARMO:00013912]</span> *3
                * <span style="color: #00a822;">ArmorBanditGauntlets "Brassards de fourrure" [ARMO:0006F39B]</span> *3
                * <span style="color: #00a822;">ArmorLeatherGauntlets "Brassards de cuir" [ARMO:00013921]</span> *3</strong>
                </details>
            </details>
        *   <details>
            <summary>SublistBanditBretonBoots [LVLI:FE043861]</summary>

            *   <details>
                <summary>SublistBanditBretonBootsHeavy [LVLI:FE043855]</summary>

                *   <details>
                    <summary>SublistEnchBanditBretonBootsHeavy [LVLI:FE043857] <b>*3</b></summary>

                    * <strong><span style="color: #00a822;">SublistEnchArmorIronBoots01 [LVLI:0007A82C]</span>
                    * <span style="color: #00a822;">SublistEnchArmorIronBoots02 [LVLI:000B5086]</span>
                    * <span style="color: #00a822;">SublistEnchArmorIronBoots03 [LVLI:000B5087]</span></strong>
                    </details>
                * <strong><span style="color: #00a822;">ArmorIronBoots "Bottes de fer" [ARMO:00012E4B]</span> \*4
                * <span style="color: #00a822;">ArmorSteelBootsB "Jambières d'acier" [ARMO:000F6F21]</span> \*3</strong>
                </details>
            *   <details>
                <summary>SublistBanditBretonBootsLight [LVLI:FE04385D]</summary>

                *   <details>
                    <summary>SublistEnchBanditBretonBootsLight [LVLI:FE04385F] <b>*3</b></summary>

                    * <strong><span style="color: #00a822;">SublistEnchArmorHideBoots01 [LVLI:0007A830]</span>
                    * <span style="color: #00a822;">SublistEnchArmorHideBoots02 [LVLI:000B4213]</span>
                    * <span style="color: #00a822;">SublistEnchArmorHideBoots03 [LVLI:000B4214]</span>
                    * <span style="color: #00a822;">SublistEnchArmorLeatherBoots01 [LVLI:000B506E]</span>
                    * <span style="color: #00a822;">SublistEnchArmorLeatherBoots02 [LVLI:000B506F]</span>
                    * <span style="color: #00a822;">SublistEnchArmorLeatherBoots03 [LVLI:000B5070]</span></strong>
                    </details>
                * <strong><span style="color: #00a822;">ArmorHideBoots "Bottes en peau" [ARMO:00013910]</span> \*3
                * <span style="color: #00a822;">ArmorBanditBoots "Chaussures de fourrure" [ARMO:0006F398]</span> \*3
                * <span style="color: #00a822;">ArmorLeatherBoots "Bottes de cuir" [ARMO:00013920]</span> \*3</strong>
                </details>
            </details>
        </details>
    </details>
*   <details>
    <summary>LItemsBanditBretonWeapons [LVLI:FE043863]</summary>

    *   <details>
        <summary>LItemsBanditBretonWeapons2H [LVLI:FE043864]</summary>

        *   <details>
            <summary>SublistBanditBreton2HGreatsword [LVLI:FE043866]</summary>

            *   <details>
                <summary>SublistEnchBanditBreton2HGreatsword [LVLI:FE04386C] <b>*3</b></summary>

                * <strong><span style="color: #00a822;">LItemEnchIronGreatsword [LVLI:0008992D]</span>
                * <span style="color: #00a822;">LItemEnchSteelGreatsword [LVLI:000A6A21]</span></strong>
                </details>
            * <strong><span style="color: #00a822;">IronGreatsword "Espadon de fer" [WEAP:0001359D]</span> \*4
            * <span style="color: #00a822;">SteelGreatsword "Espadon d'acier" [WEAP:00013987]</span> \*3</strong>
            </details>
        *   <details>
            <summary>SublistBanditBreton2HWarhammer [LVLI:FE043868]</summary>

            *   <details>
                <summary>SublistEnchBanditBreton2HWarhammer [LVLI:FE04386E] <b>*3</b></summary>

                * <strong><span style="color: #00a822;">LItemEnchIronWarhammer [LVLI:0008992A]</span>
                * <span style="color: #00a822;">LItemEnchSteelWarhammer [LVLI:000A6A28]</span></strong>
                </details>

            * <strong><span style="color: #00a822;">IronWarhammer "Marteau de fer" [WEAP:00013981]</span> \*4
            * <span style="color: #00a822;">SteelWarhammer "Marteau d'acier" [WEAP:0001398A]</span> \*3</strong>
            </details>
        </details>
    *   <details>
        <summary>LItemsBanditBreton1HShield [LVLI:FE043865]</summary>

        *   <details>
            <summary>LItemsBanditBretonWeapons1H [LVLI:FE043872]</summary>

            *   <details>
                <summary>SublistBanditBreton1HSword [LVLI:FE043869]</summary>

                *   <details>
                    <summary>SublistEnchBanditBreton1HSword [LVLI:FE04386F] <b>*3</b></summary>

                    * <strong><span style="color: #00a822;">LItemEnchIronSword [LVLI:0004B580]
                    * <span style="color: #00a822;">LItemEnchSteelSword [LVLI:0004B583]</strong>
                    </details>
                * <strong><span style="color: #00a822;">IronSword "Épée de fer" [WEAP:00012EB7]</span> \*4
                * <span style="color: #00a822;">SteelSword "Épée d'acier" [WEAP:00013989]</span> \*3</strong>
                </details>
            *   <details>
                <summary>SublistBanditBreton1HMace [LVLI:FE04386B]</summary>

                *   <details>
                    <summary>SublistEnchBanditBreton1HMace [LVLI:FE043871] <b>*3</b></summary>

                    * <strong><span style="color: #00a822;">LItemEnchIronMace [LVLI:0004B57F]</span>
                    * <span style="color: #00a822;">LItemEnchSteelMace [LVLI:0004B582]</span></strong>
                    </details>
                * <strong><span style="color: #00a822;">IronMace "Masse de fer" [WEAP:00013982]</span> \*4
                * <span style="color: #00a822;">SteelMace "Masse d'acier" [WEAP:00013988]</span> \*3</strong>
                </details>
            </details>
        *   <details>
            <summary>SublistBanditBretonShield [LVLI:FE043873]</summary>

            *   <details>
                <summary>SublistEnchBanditBretonShield [LVLI:FE043874]</summary>

                * <strong><span style="color: #00a822;">SublistEnchArmorIronShield01 [LVLI:0007A835]</span>
                * <span style="color: #00a822;">SublistEnchArmorIronShield02 [LVLI:000B508E]</span>
                * <span style="color: #00a822;">SublistEnchArmorIronShield03 [LVLI:000B508F]</span>
                * <span style="color: #00a822;">SublistEnchArmorBandedIronShield01 [LVLI:000B5097]</span>
                * <span style="color: #00a822;">SublistEnchArmorBandedIronShield02 [LVLI:000B5098]</span>
                * <span style="color: #00a822;">SublistEnchArmorBandedIronShield03 [LVLI:000B5099]</span>
                * <span style="color: #00a822;">SublistEnchArmorSteelShield01 [LVLI:000B5104]</span>
                * <span style="color: #00a822;">SublistEnchArmorSteelShield02 [LVLI:000B5105]</span>
                * <span style="color: #00a822;">SublistEnchArmorSteelShield03 [LVLI:000B5106]</span></strong>
                </details>
            * <strong><span style="color: #00a822;">ArmorIronShield "Bouclier de fer" [ARMO:00012EB6]</span> \*4
            * <span style="color: #00a822;">ArmorIronBandedShield "Bouclier de fer renforcé" [ARMO:0001394B]</span> \*2
            * <span style="color: #00a822;">ArmorSteelShield "Bouclier d'acier" [ARMO:00013955]</span> \*3</strong>
            </details>
        </details>
    </details>
*   <details>
    <summary>LItemsBretonMarksmann [LVLI:FE043875]</summary>

    *   <details>
        <summary>SublistBretonBow [LVLI:FE043876]</summary>

        *   <details>
            <summary>SublistEnchBretonBow [LVLI:FE043877]</summary>

            * LItemEnchHuntingBow [LVLI:000AE745]
            * LItemEnchImperialBow [LVLI:000AE746]
            * LItemEnchEbonyBow [LVLI:000CB3C7]
            </details>
        * <strong><span style="color: #00a822;">LongBow "Arc long" [WEAP:0003B562]</span></strong>
    * SublistBretonArrow [LVLI:FE043878]
</details>

<details>
    <summary id="lls-wanderer-encounter" style="color: #3BA5EA;">Wanderer Encounter</summary>

*   <details>
    <summary>LOutfitWESpellswordBreton [LVLI:FE043829]</summary>

    *   <details>
        <summary>LItemsLWESpellswordBreton [LVLI:FE04382C]</summary>

        *   <details>
            <summary>SublistWESpellswordBretonBodyGear [LVLI:FE04382B] <b>*4</b></summary>

            * SublistBretonCuirassHeavy [LVLI:FE04382D]
            * SublistMageRobesAll [LVLI:FE043832]
            </details>
        * SublistBretonGauntletsHeavy [LVLI:FE04382E]
        * SublistBretonBootsHeavy [LVLI:FE04382F]
        *   <details>
            <summary>SublistWESpellswordBretonHeadgear [LVLI:FE043831]</summary>

            * LItemEnchCircletMagicka [LVLI:00107349]
            * LItemRobesCollegeMagickaHood [LVLI:00016E23]
            </details>
        </details>
    </details>
*   <details>
    <summary>LOutfitWESpellswordBretonNoHelmet [LVLI:FE04384C]</summary>

    *   <details>
        <summary>SublistWESpellswordBretonBodyGear [LVLI:FE04382B] <b>*4</b></summary>

        * SublistBretonCuirassHeavy [LVLI:FE04382D]
        * SublistMageRobesAll [LVLI:FE043832]
        </details>
    * SublistBretonGauntletsHeavy [LVLI:FE04382E]
    * SublistBretonBootsHeavy [LVLI:FE04382F]
    </details>
</details>


## <span style="color: teal;" id="outfits">4.3 List of outfits</span>
> *<u>Note</u>: Feel free to use this data in xEdit or to explore SkyPatches, where it is also repeated for easier navigation.*

<details>
<summary id="outfits-stormcloak" style="color: #3BA5EA;">Stormcloaks</summary>

*   <details>
    <summary>OutfitStormcloakGuard [OTFT:FE000826]</summary>

    * LOutfitStormcloakGuard [LVLI:FE00081D]
    </details>
</details>

<details>
<summary style="color: #3BA5EA;" id="outfits-redoran">Redoran</summary>

*   <details>
    <summary>OutfitRedoranGuardExterior [OTFT:FE00087F]</summary>

    * LOutfitRedoranGuardExterior [LVLI:FE000835]
    </details>
*   <details>
    <summary>OutfitRedoranGuardBulwark [OTFT:FE000889]</summary>

    * LOutfitRedoranGuardBulwark [LVLI:FE00088A]
    </details>
</details>

<details>
    <summary id="outfits-bandits" style="color: #3BA5EA;">Bandits</summary>

*   <details>
    <summary>OutfitBanditBreton [OTFT:FE043850]</summary>

    * LOutfitBanditBreton [LVLI:FE043851]
    </details>
</details>

<details>
    <summary id="outfits-wanderer-encounter" style="color: #3BA5EA;">Wanderer Encounter</summary>

*   <details>
    <summary>OutfitWESpellswordBreton [OTFT:FE001828]</summary>

    * LOutfitWESpellswordBreton [LVLI:FE043829]
    </details>
*   <details>
    <summary>OutfitWESpellswordBretonNoHelmet [OTFT:FE04384D]</summary>

    * LOutfitWESpellswordBretonNoHelmet [LVLI:FE04384C]
    </details>
</details>