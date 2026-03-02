# 128177.github.io
初稿
[index.html](https://github.com/user-attachments/files/25684537/index.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>摩托车3D版画设计器</title>
<script src="https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/three@0.160.0/examples/js/loaders/GLTFLoader.js"></script>
<script src="https://cdn.jsdelivr.net/npm/three@0.160.0/examples/js/controls/OrbitControls.js"></script>
<script src="https://cdn.jsdelivr.net/npm/konva@9.3.6/konva.min.js"></script>
<link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
<script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
<h1>摩托车3D版画设计器</h1>
<div id="container" style="width:100%;height:800px;background:#eee"></div>

<script>
let scene,camera,renderer,controls;
init();
function init(){
scene=new THREE.Scene();
scene.background=new THREE.Color(0xf0f0f0);
camera=new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,0.1,1000);
camera.position.z=3;
renderer=new THREE.WebGLRenderer({antialias:true});
renderer.setSize(window.innerWidth,window.innerHeight);
document.getElementById("container").appendChild(renderer.domElement);
controls=new THREE.OrbitControls(camera,renderer.domElement);
const light=new THREE.AmbientLight(0xffffff,1);
scene.add(light);
const loader=new THREE.GLTFLoader();
loader.load("https://raw.githubusercontent.com/KhronosGroup/glTF-Sample-Models/master/2.0/Box/glTF/Box.gltf",gltf=>{
scene.add(gltf.scene);
});
animate();
}
function animate(){
requestAnimationFrame(animate);
controls.update();
renderer.render(scene,camera);
}
</script>
</body>
</html>
