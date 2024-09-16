# js + A-Frame == sant

https://aframe.io/docs/1.6.0/introduction/javascript-events-dom-apis.html


*Det här är en "liten" introduktion till JavaScript i A-Frame. Det finns betydligt mer möjligheter än vad som tas upp här - förhoppningsvis ger detta en ingång och en förståelse för att du ska kunna ta det vidare om du vill.*

#### TOC
- [intro](#intro)


## intro
Med JavaScript och DOM kan vi programmatiskt ändra scenen och dess komponenter. 
Precis som vid vanlig webbutveckling. A-Frame ger tillgång till JavaScript, DOM API:er och three.js under huven. Förutom att förändara egenskaper hos objekt i en scen kan vi lägga till och hantera events, lägga till och ta bort objekt etc etc. Med JS kan vi alltså göra mycket mer avancerad logik.

I förlängningen så innebär ju också detta att vi skulle kunna göra riktigt avancerade applikationer med ramverk, enheter och plattformar inkluderade. Vi skulle kunna använda node, databaser, IoT, mobila enheter, bluetooth etc etc. Detta går vi dock inte in på här :)

Glöm inte att vi självklart kan använda **konsollen** i webbläsaren - ```console.log``` är självklart tillgängligt. Ett tips är alltså att 'som vanligt' använda just det för att t ex inspektera element och testa kommandon.

## querySelector
När vi använder JS för att **komma åt A-Frame komponenter** så rekommenderas att gå via ```document.querySelector('a-entity')``` eller ```document.querySelectorAll('a-entity')```

## Object3D

Nu vet vi hur vi kan komma åt en komponent. Om vi sedan ska förändra dess egenskaper och t ex färg eller material så kan vi göra detta via metoden ```setAttribute()```. T ex ```entityEl.setAttribute('material', 'color', 'red');```

Några undantag finns dock, i synnerhet när det gäller position, rotation, skala och visibilitet så rekommenderas att gå via en property direkt på objektet som heter ```object3D```.
T ex ```entityEl.object3D.position.x += 5;```

## infoga JS-kod
När du ska infoga JS i din lösning så rekommenderas starkt att du kapslar (registrerar) in din kod som en A-Frame-komponent. 
Komponenter modulariserar kod, gör logik och beteende synligt för HTML och säkerställer att koden exekveras vid rätt tidpunkt (t.ex. efter att scenen och entiteterna har laddats in och initierats).
Detta innebär alltså att vi lägger till och registerar vår kod som en komponent till A-Frame.
Vi gör det i ```head```i html-filen.


Exempelvis, om vi vill skapa en funktion till vilken vi kan skicka en sträng som ska skrivas ut i konsollen med ```console-log```:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>exempel</title>
    <script src="https://aframe.io/releases/1.6.0/aframe.min.js"></script>
    
    <!-- HÄR, EFTER A-FRAME, INFOGAR VI VÅR KOMPONENT (som får heta 'log') -->
    <script>
      AFRAME.registerComponent('log', {
            schema: {type: 'string'},

            init: function () {
                let stringToLog = this.data;
                console.log(stringToLog);
            }
        });
    </script>
  </head>
  <body>
    <!-- vår komponent/kod körs via attributet log. Värdet skickas med som argument -->
    <a-scene log="Hurra en scene!">
        <a-box log="Hurra en box!"></a-box>
    </a-scene>
  </body>
</html>
```


Med JS kan vi t ex;
- Få en referens till elementet ```<a-scene>``` med ```let sceneEl = document.querySelector('a-scene');```
- Få en referens till alla ```<a-entity>```-element med ```sceneEl.querySelectorAll('a-entity');```
- Få en referens till boxentiteten med ```sceneEl.querySelector('#box');```
- Få en referens till samtliga entiteter i scenen via ett ```.querySelectorAll()```-anrop genom att använda multi-element selector. 
- Vi kan också använda ```.querySelectorAll()```-anrop för att välja eventuella HTML-klasser

Exempel där vi förändrar egenskaper hos några eniteter:

```html
let sceneEl = document.querySelector('a-scene'); 
sceneEl.querySelector('a-box').setAttribute('light', {color: '#ACC', intensity: 0.75});
sceneEl.querySelector('a-cylinder').setAttribute('geometry', 'height', 0.5);
sceneEl.querySelector('a-sphere').setAttribute('material', 'color', 'gray');
```

Som nämnts tidigare och som en påminnelse; vi kan också t ex lägga till/editera och hantera element, events etc i vår scen.


#### Övning med JS

Utgå ifrån följande scen (copy/paste) till din egna fil:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>JavaScript - övning</title>
    <script src="https://aframe.io/releases/1.6.0/aframe.min.js"></script>
  </head>
  <body>
    <a-scene js-ex>
      <a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9"></a-box>
      <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
      <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D"></a-cylinder>
      <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="orange"></a-plane>
      <a-sky color="#ECECEC"></a-sky>
    </a-scene>
  </body>
</html>
```

**Gör följande genom att lägga till egen JS-kod till filen ovan:**

- Ändra 'rotation' på box:en 
- Ändra storlek/scale på cylinder 
- Ändra sphere så den inte inte syns längre (ta ej bort)
- Ändra valfria properties på objekten.
- Se inledande exempel på den här sidan där en funktion läggs till. Utgå ifrån det exemplet och lägg till en egen funktion som gör något du själv hittar på, t ex förändrar färg på en box eller liknande.
- Läs på om events och lägg till ett click-event för ett objekt. När man klicka på objektet ska du förändra något attribut, t ex färgen. Events: https://aframe.io/docs/1.6.0/introduction/javascript-events-dom-apis.html#events-and-event-listeners

*Tips:*

*du kan använda scenens id (js-ex) för att via den komma åt boxen, sfären etc.*
*se i exemplet ovan...*

<details>

<summary>Om du kör fast....</summary>
    
    
```html

        <script>
        AFRAME.registerComponent('school-playground', {
            init: function () {
            // Solution for Modifying Entities.
            var sceneEl = document.querySelector('a-scene'); 
            sceneEl.querySelector('a-box').object3D.rotation.divideScalar(2);
            sceneEl.querySelector('a-cylinder').object3D.scale.set(2, 2, 2);
            sceneEl.querySelector('a-sphere').object3D.visible = false;
            }

            var boxEl = sceneEl.querySelector('a-box')
          
            boxEl.addEventListener('click', function () {
                boxEl.setAttribute('color', 'blue');  
            });
            boxEl.emit('click');
        });
        </script>
```

</details>


