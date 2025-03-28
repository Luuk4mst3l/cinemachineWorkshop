# Animation Workshop 2 - Cinemachine

Welkom bij de Cinemachine workshop van Animation. In deze workshop ga je je eerste Cinemachine cameras maken, en hun desbetreffende behaviour aanpassen doormiddel van de timeline en/of scripts.

## Workshop Inhoud

- [Wat leer je](#wat-leer-je)
- [De Cinemachine opzet](#de-cinemachine-opzet)
- [Cinemachine Timeline & Dolly's](#timeline-en-dollys)
- [Cinemachine Scripting en Blending](#scripting-en-blending)

## Wat leer je

- Verschillende Cinemachine cameras gebruiken, zoals een normale virtuele camera en een dolly camera.
- Cinemachine gebruiken met een timeline.
- Cinemachine gebruiken met een script.
- Het blenden van de cameras.

## De Cinemachine Opzet

1. **Clone Workshop Project**

   - Ga naar de github en clone het project.

2. **Import Cinemachine Package (al gedaan)**

   - Ga naar `window` > `Package Manager`.
   - Zoek op "Cinemachine" in de zoekbalk.
   - Klik op "Install" om de package toe te voegen aan het project.
   - Deze package is in het gedownloade project al geinstalleerd, maar het is goed om het proces van installatie een keertje gedaan te hebben. :)

3. **Scene Selecteren**

   - Voor deze workshop, selecteer in de folder `Scenes`, de Scene`WorkshopScene`.
   - In deze Scene zijn al wat objecten te vinden die helpen met het visualiseren van de camera werking.

4. **Cinemachine brain toevoegen**

   - In je `Hierarchy`, klik op de Main Camera.
   - Voeg aan de Main Camera een component toe door in de `Inspector` op "Add Component" te klikken
   - Zoek dan op "Cinemachine Brain" en voeg deze toe aan de Main Camera.

5. **Maak een Cinemachine Camera**

   - In de `Hierarchy`, klik op de Create knop > `Cinemachine` > `Cinemachine Camera`.
   - Geef de `Cinemachine Camera` zo nodig een naam, maar je kan het ook standaard laten.
   - Selecteer het gemaakte `Cinemachine Camera` object en reset de `Transform` door op de 3 puntjes te klikken en dan `Reset`.
   - Verplaats de camera zodat deze boven de grond hangt, bijvoorbeeld `Y = 2`

6. **Pas je Camera aan**

   - Nu je een Camera aangemaakt en geplaatst hebt, kan je andere onderdelen van de camera aanpassen via de `Inspector`.
   - Terwijl je de camera geselecteerd hebt, vouw het tabje `Lens` uit. Experimenteer met de `Vertical FOV` totdat je tevreden bent met de camera.

7. **Target Tracking aanpassen**

   - Selecteer een `Tracking Target` door het 'Cube' object uit de Hierarchy in de selectiebox te slepen, of klik op het selectieknopje `๏` en klik dan op "Cube".
   - Nu je de `Tracking Target` hebt geselecteerd, kan je je camera behaviour aanpassen rekening houdende met deze target.
   - In de Inspector onder het kopje **Procedural Components** > `Rotation Control` > en kies `Rotation Composer`.

8. **Rotation composer gebruiken**

   - Selecteer de camera en ga naar de "Game" view. Hierin is een geel vierkantje te zien die je kan verslepen. Versleep deze en bekijk hoe het er uit ziet. Hierbij pas je de `Screen Position` aan.
   - Ook kan je voor dead zones kiezen. De camera beweegt dan alleen mee wanneer de focus (Het gele vierkantje) buiten de dead zone ligt.
   - Naast de screen position, kan er ook een `Hard Limit` toegevoegd worden. Deze limits dienen als het uiterste voor hoe ver de focus van de tracking target af kan komen, voordat hij bijdraait.
   - Experimenteer met de opties totdat je tevreden bent.

9. **Test de camera**
   - Druk op play en aanschouw je creatie :D

## Timeline en Dollys

_Zet ter gemak de eerste gemaakt `CinemachineCamera` uit door het vinkje weg te halen in de `Inspector`_

1. **Maak een dollycam aan**

   - Je kunt gemakkelijk een dolly cam aanmaken door een nieuw GameObject te creëren. Klik op de `Create` knop > `Cinemachine` > `Dolly Camera With Spline` en noem deze voor het gemak "DollyCamera".
     > De Spline is de lijn waar de camera opzit, zoals bij een achtbaan. De Dolly camera loopt dus altijd over deze lijn.

2. **Splines**

   - Selecteer de `Dolly Spline`, ga naar de `tools` in de scene view en selecteer de bovenste tool 'Spline'.
   - Je krijgt nu een lijntje te zien met twee blauwe uiteindes. Versleep een of beide uiteindes naar een willekeurige positie. Deze uiteindes worden `Knots` genoemd.
   - Op de spline zijn er nu nog maar 2 Knots. Voeg een nieuwe `Knot` toe door bij de tools op de onderste tool `Create Spline` te klikken. (zorg dat je het `Dolly Spline` object geselecteerd hebt)
   - Klik vervolgens op een van de twee bestaande `Knots` en vervolgens op een plek voor de nieuwe `Knot` in de scene view. Er ontstaat dan automatisch een gebogen lijn vanaf de bestaande `Knot` naar de nieuwe `Knot`.

3. **Positie op de spline**

   - Selecteer je gemaakte `DollyCamera` camera object en navigeer in je inspector naar het `Cinemachine Spline Dolly` component.
   - Je kan de DollyCamera verschuiven over de spline door de waarde van `Position` aan te passen. Hierbij zijn 3 waardes te selecteren
   - Kies een van de positie types naar keuze, wij raden
     `Normalized` aan.

   | Position type | Waarde                    | Betekenis                                                                                                                                             |
   | ------------- | ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Distance      | 0 - Spline Length (float) | Hierbij wordt gekeken naar de totale lengte van de spline, van begin tot eind                                                                         |
   | Normalized    | 0 - 1                     | Dit is een genormaliseerde waarde van de totale lengte op een schaal van 0 (begin) tot 1 (eind)                                                       |
   | Knot          | 0 - N<sub>`knots`</sub>   | Hierbij bepaald je positie van de camera op punten tussen knots, deze afgelegde afstand tussen knots kan verschillen. |

4. **Timeline op een dollycam**

   - Zorg ervoor dat je een Timeline panel beschikbaar hebt. Als je deze nog niet hebt, navigeer naar `Window` > `Sequencing` > `Timeline`.
   - Selecteer je `DollyCamera` object, en klik op de `Create` knop in de Timeline. Geef deze Timeline `.playable` een naam naar keuze.
   - In de Timeline panel, klik op de plus `+` en dan `Animation Track`.
   - In de gemaakte animation track zie je dat er een leeg object is voor de Animator. Sleep de `DollyCamera` uit de `Hierarchy` hierin, of selecteer deze door op de target knop `๏` te klikken en dan `DollyCamera`.

5. **De dollycam animeren**
   - In de Timeline panel is een witte balk te zien die bepaald op welke plek de animaties moeten komen. Sleep deze naar het begin, en druk dan op de rode "Start Recording" knop.
   - Stel de position in van de DollyCamera onder de `Cinemachine Spline Dolly` component, zet deze bijvoorbeeld op 1 als de waarde Normalized is.
   - Versleep de witte balk op te timeline nu naar achter. Pas daarna ook weer de position van de `DollyCamera` aan, bijvoorbeeld de waarde op 0 zetten.
   - Druk vervolgens op de "End Recording" knop. (Dezelfde knop als beginnen met recorden) Op de timeline is nu te zien dat er twee ruitjes zijn, dit zijn de `keyframes` en bepalen in dit geval de start en eindposities van de DollyCamera. 
   - De tijd dat de dolly er over doet om van punt A naar punt B te gaan is afhankelijk van de Animatietijd die jij hebt gegeven tussen de twee keyframes. 

6. **Test je DollyCamera**
   - Druk op de play knop om de animatie van je DollyCamera te zien.

7. **Andere Camera instellingen**
   - Je kan, omdat het verder gewoon een normale cinemachine camera is, dezelfde instellingen gebruiken die je bij het eerste hoofdstuk gemaakt hebt. Voeg bijvoorbeeld hetzelfde `Cube` Object toe aan de Tracking Target. Selecteer daarbij weer een `Rotation Control` naar keuze.

## Scripting en Blending

1. **Blend Instellen via Cinemachine Brain**

   - Selecteer de `Main Camera` waar een Cinemachine Brain component op staat.
   - Onder "Custom Blends" klik je op het tandwiel-icoon.
   - Kies `New Blender Settings` om een nieuw blend-profiel aan te maken.
   - Klik op de nieuw gemaakte asset en voeg blends toe tussen verschillende Cinemachine camera’s.

2. **Priority Gebruiken om Overgangen te Beheersen**
   - Elke Cinemachine camera heeft een Priority waarde.
   - De camera met de hoogste Priority wordt actief. Deze is bijvoorbeeld handmatig in te stellen in de `Inspector` door het `Priority` veld aan te vinken.
   - Verander de Priority van de camera's tijdens runtime (bijvoorbeeld via een script of een trigger) om vloeiende overgangen te maken.

_Voorbeeld van een Script om Priority te Wijzigen_

```
using UnityEngine;
using Unity.Cinemachine;

public class CameraSwitcher : MonoBehaviour
{
    [SerializeField] private CinemachineCamera camera1; //Je eerst gemaakt Cinemachine Camera, vergeet deze niet weer aan te zetten
    [SerializeField] private CinemachineCamera camera2; //Een andere Cinemachine Camera, zoals de Dolly Camera

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Alpha1))
        {
            camera1.Priority = 9;
            camera2.Priority = 5;
        }
        if (Input.GetKeyDown(KeyCode.Alpha2))
        {
            camera1.Priority = 5;
            camera2.Priority = 10;
        }
    }
}
```

Met dit script kun je met de toetsen 1 en 2 wisselen tussen twee Cinemachine-camera's met een vloeiende overgang.
