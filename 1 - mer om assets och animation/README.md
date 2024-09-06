# Mer om assets, animation och interaktion

*i det här avsnittet ska vi titta på hur man kan använda 3D-modeller, skapa animationer samt titta på enkel interaktion*

```
Läs först den här sidan och sedan kan du fortsätta genom att läsa och ta till dig materialet i kronologisk ordning.
Precis som tidigare, börja med filerna i nummerordning;

- "1.1 - ...md"
- "1.2 - ...md"
- "1.3 - ...md"

osv

```

## ett ord om asset-magement
Du har tidigare sett och lärt dig att lägga till texturer, bilder, audio och video. För det har du använt asset-manegement med den inbyggda < a-asset > komponenten.
Det kan vara bra att veta att man faktiskt kan infoga t ex bilder direkt via src-attributet för t ex en box.
Fördelen är att man snabbt kan testa saker, men detta är inte rekommenderat att i förlängningen göra på det sättet.

Använd just asset-management eftersom då "preloadas" all media och är redo för användning - man försäkrar sig om att alla assets är redo och laddade före dom ska användas. Risken är annars att någon resurs kanske inte laddas in korrekt (särskilt om du har många filer som ska användas) och hela scenen/appen fungerar inte som tänkt.


Titta på nedan exempel - där laddas en 3d-modell in (en .gltf-fil) via assets. I själva scenen visas också att modellen kan laddas direkt, men som sagt - det är inte rekommenderat.

```html
<a-scene>
  <a-assets>
    <!-- en 3D-modell laddas -->
    <a-asset-item id="tree" src="tree.gltf"></a-asset-item>
  </a-assets>

  <!-- här använder vi ovan 'preloadade' modell/asset, vi använde asset management. -->
  <a-gltf-model src="#tree"></a-gltf-model>

  <!-- ok, vi hämtar en asset/modell via src. Detta kallas 'inline'.
       Inte rekommenderat, men för att testa/i en utvecklingsfas är det ok. 
       Ändra till asset manegement innan det rullas ut live/i produktion. -->
  <a-gltf-model src="tree.gltf"></a-gltf-model>
</a-scene>
```

Läs mer om asset management här https://aframe.io/docs/1.6.0/core/asset-management-system.html


## animationer
Det finns olika typer av animationer i A-Frame, exempelvis så kan man använda tidsbaserade eller oändliga animationer eller t ex animationer som aktiveras av en interaktion av användaren.
Man kan göra animationer lite olika beroende på vad det är för komponent, te x för en box så finns en property/attribut som heter just animation.

Läs mer här https://aframe.io/docs/1.6.0/components/animation.html


## interaktion
kan också göras på flera olika sätt (till väldigt avancerat med egen JavaScript), men allting handlar oftats om att en användare interagerar med något objekt, t ex en box.

Vi ska ta en liten titt på det här i övningarna som kommer.

