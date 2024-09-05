```html
<a-scene>
  <a-assets>
    <a-asset-item id="tree" src="tree.gltf"></a-asset-item>
  </a-assets>

  <!-- Using the asset management system. -->
  <a-gltf-model src="#tree"></a-gltf-model>

  <!-- Defining the URL inline. Not recommended but more comfortable for web developers. -->
  <a-gltf-model src="tree.gltf"></a-gltf-model>
</a-scene>
```
