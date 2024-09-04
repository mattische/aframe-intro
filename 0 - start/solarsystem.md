# solsystem

Nu har du kommit en bit med A-Frame och det övningen blir slutet för introt til A-Frame.

Övningen här är att skapa ett "solsystem" i A-Frame. 

- Skapa en scen i vilken du placerar ett antal planeter med olika färger och storlek.
Lägg till åtminstone 7-8 olika planeter av olika storlek, färg och positioner. Lägg till en "sol/stjärna" som är gul och störst av planeterna (himlakropparna).
- Försök hitta en bild som är passande i ditt solsystem och som du lägger till i sky-komponenten.
- Hitta ett passande bakgrundsljud som spelar automatiskt.
- Lägg till ytterligare som gör att du övar på det du hittills lärt dig.






![solsystem](https://github.com/mattische/aframe-intro/blob/77ac0cf15dac19ab102dcc30665c85c0ce037a82/0%20-%20start/solar.png)

*en första början på ett enkelt solsystem skulle kunna se ut så här kanske?*


**tips**

om du fastnar totalt eller inte har en aning om hur du ska börja kan du ta en titt på en alternativ lösning nedan.

**Men** - försök själv först!

<details>

<summary>solarsystem</summary>

### en lösning

Detta är ett alternativ till lösning. Obs, ingen media eller texturer.

Planeterna med ringar runt är egna entiteter

```html
<html>
  <head>
    <script src="https://aframe.io/releases/1.6.0/aframe.min.js"></script>
  </head>
  <body>
    <a-scene background="color: midnightblue">
      <!-- Sun -->
      <a-sphere 
        color="#F5C85D"
        position="-13 2 -10" 
        radius="4"></a-sphere>

      <!-- Mercury -->
      <a-sphere
        color="#AF886D"
        position="-7 2 -10"
        radius=".25"></a-sphere>

      <!-- Venus -->
      <a-sphere 
        color="#ECBFBF"
        position="-5 2 -10" 
        radius=".5"></a-sphere>

      <!-- Earth -->
      <a-sphere 
        color="#6DCBE7"
        position="-3 2 -10" 
        radius=".5"></a-sphere>

      <!-- Mars -->
      <a-sphere 
        color="#CF503A"
        position="-1 2 -10" 
        radius=".25"></a-sphere>

      <!-- Jupiter -->
      <a-sphere 
        color="#C9957A"
        position="1 2 -10"
        radius="1"></a-sphere>
      
      <!-- Saturn -->
      <a-sphere 
        color="#F8EC99"
        position="4 2 -10" 
        radius=".8"></a-sphere>

      <!-- Uranus -->
      <a-sphere 
        color="#73AAF8"
        position="7 2 -10"
        radius=".75"></a-sphere>

      <!-- Neptune -->
      <a-sphere 
        color="#3453BD"
        position="10 2 -10" 
        radius=".75"></a-sphere>
     
<!-- Dessa planeter har ringar runt sig - torii (singular torus) vilket är en primitive/shape som kan användas för att göra "donuts", tuber/tubes och, som i det här fallet, ringar.
Ringarna är placerade i a-entity, som kan ses som en container/behållare som i sig kan innehålla komponenter (och funktionalitet/interaktivitet).
 -->
      <a-entity id="saturn-container" position="4 2 -10">
        <a-sphere position="0 0 0 " radius=".8" color="#F8EC99" id="saturn"></a-sphere>
        <a-torus id="saturn-ring-1" color="#57524A" segments-tubular="50" radius="3.2" radius-tubular="0.1" rotation="90 0 0" scale=".44 .44 0.04"></a-torus>
        <a-torus id="saturn-ring-2" color="#A29A87" segments-tubular="50" radius="2.4" radius-tubular="0.2" rotation="90 0 0" scale=".44 .44 0.04"></a-torus>
      </a-entity>

      <a-entity id="uranus-container" position="7 2 -10">
        <a-sphere id="uranus" radius=".75" color="#73AAF8"></a-sphere>
        <a-torus id="uranus-ring" color="#FFFFFF" segments-tubular="50" radius="1.5" radius-tubular="0.01" rotation="-10 90 0" scale=".75 .75 0.075"></a-torus>
      </a-entity>
      

    </a-scene>
  </body>
</html>
```

</details>
