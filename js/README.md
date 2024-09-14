# js + A-Frame == sant

https://aframe.io/docs/1.6.0/introduction/javascript-events-dom-apis.html

Med JavaScript och DOM kan vi programmatiskt ändra scenen och dess komponenter. 
Precis som vid vanlig webbutveckling. A-Frame ger tillgång till JavaScript, DOM API:er och three.js under huven. Med detta kan vi göra mycket mer avancerad logik.

Vi kan självklart använda **konsollen** i webbläsaren - ```console.log``` är självklart tillgängligt. Ett tips är alltså att 'som vanligt' använda just det för att t ex inspektera element och testa kommandon.

När vi använder JS för att komma åt A-Frame komponenter så rekommenderas ```document.querySelector('a-entity')``` eller ```document.querySelectorAll('a-entity')```


### infoga JS-kod
När du ska infoga JS i din lösning så rekommenderas starkt att du kapslar (registrerar) in din kod som en A-Frame-komponent. 
Komponenter modulariserar kod, gör logik och beteende synligt för HTML och säkerställer att koden exekveras vid rätt tidpunkt (t.ex. efter att scenen och entiteterna har laddats in och initierats).
Detta innebär alltså att vi lägger till och registerar vår kod som en komponent till A-Frame.
Vi gör det i ```head```i html-filen.


Exempelvis, om vi vill skapa en funktion till vilken vi kan skicka en sträng som ska skrivas ut i konsollen med ```console-log``:

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
- Få en referens till sphere- och cylinder-entiteterna i ett ```.querySelectorAll()```-anrop genom att använda multi-element selector. 
- Få en referens till sfär- och cylinderentiteterna i ett ```.querySelectorAll()```-anrop genom att lägga till och välja HTML-klasser

Exempel där vi förändrar egenskaper hos några eniteter:

```html
let sceneEl = document.querySelector('a-scene'); 
sceneEl.querySelector('a-box').setAttribute('rotation', {x: 0, y: 0, z: 0});
sceneEl.querySelector('a-cylinder').setAttribute('geometry', 'height', 0.5);
sceneEl.querySelector('a-sphere').setAttribute('material', {metalness: 1});
```

Med JS kan vi också t ex lägga till element, events, hantera events etc för element i vår scen.


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

- Ändra 'rotation' på box:en (förändra 'rotation'-komponenten för boxen)
- Ändra 'height' på cylinder (geometry-komponentens property height ska förändras)
- Ändra sphere så att dess 'material' ändras - du ska ge ett annat värde för 'metalness' property:n

*Tips:*

*du kan använda scenens id (js-ex) för att via den komma åt boxen, sfären etc.*

*det finns en funktion som heter ```setAttribute()``` som kan användas på  respektive primitive. T ex ```'geometry', 'height', 0.5```eller ```'rotation', {x: 0, y: 0, z: 0}```*

<details>
<summary>Om du kör fast....</summary>
    ```html
    <script>
        AFRAME.registerComponent('school-playground', {
            init: function () {
            // Solution for Modifying Entities.
            var sceneEl = document.querySelector('a-scene'); 
            sceneEl.querySelector('a-box').setAttribute('rotation', {x: 0, y: 0, z: 0});
            sceneEl.querySelector('a-cylinder').setAttribute('geometry', 'height', 0.5);
            sceneEl.querySelector('a-sphere').setAttribute('material', {metalness: 1});
            }
        });
        </script>
    ```
</details>

