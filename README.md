<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0"
    />
    <title>3D Wireframe Cube</title>
    <style>
      body {
        margin: 0;
      }
    </style>
  </head>
  <body>
    <script src="https://threejs.org/build/three.js"></script>
    <script>
      // Set up scene
      const scene = new THREE.Scene();
      const camera = new THREE.PerspectiveCamera(
        75,
        window.innerWidth / window.innerHeight,
        0.1,
        1000
      );
      const renderer = new THREE.WebGLRenderer();
      renderer.setSize(window.innerWidth, window.innerHeight);
      document.body.appendChild(renderer.domElement);

      // Create wireframe cube
      const geometry = new THREE.BoxGeometry();
      const wireframe = new THREE.WireframeGeometry(geometry);
      const material = new THREE.LineBasicMaterial({
        color: 0x00ff00,
      });
      const cube = new THREE.LineSegments(wireframe, material);
      scene.add(cube);

      // Position camera
      camera.position.z = 5;

      // Render loop
      const animate = function () {
        requestAnimationFrame(animate);

        // Rotate cube
        cube.rotation.x += 0.01;
        cube.rotation.y += 0.01;

        renderer.render(scene, camera);
      };

      animate();
    </script>
  </body>
</html>
