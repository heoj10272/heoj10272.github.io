---
layout: welcome
title: Portfolio
permalink: /portfolio/
more_posts: posts.md
sidebar: true
order: 2
---

* * *
<center>
<span style=
"font-size:170%;
font-weight:bold">
허재영
</span>
</center>

    <canvas id="canvas" width="300" height="300"></canvas>

    <script type="importmap">
    {
      "imports": {
        "three": "https://unpkg.com/three@0.141.0/build/three.module.js",
        "GLTFLoader" : "https://unpkg.com/three@0.141.0/examples/jsm/loaders/GLTFLoaders.js"
    }
    </script>

    <script type="module">
        import {GLTFLoader} from 'GLTFLoader';
        import * as THREE from 'three';
        let scene = new THREE.Scene();
        let renderer = new THREE.WebGLRenderer({
            canvas : document.querySelector('#canvas'),
            antialias : true
        });
        renderer.outputEncoding = THREE.sRGBEncoding;

        let camera = new THREE.PerspectiveCamera(30, 1);
        camera.position.set(0,0,5);

        scene.background = new THREE.Color('white');
        let light = new THREE.DirectionalLight(0xffff00, 10);
        scene.add(light);

        let loader = new GLTFLoader();
        loader.load('/assets/img/shiba/scene.gltf', function(gltf){
            scene.add(gltf.scene);
            renderer.render(scene, camera);
            function animate(){
                requestAnimationFrame(animate)
                renderer.render(scene, camera);
            }
            animate();
        });


    </script>

<center>MAJOR : COMPUTER ENGINEERING</center>

<center>Seokyeong University</center>

<center>124, Seokyeong-ro, Seongbuk-gu, Seoul, Republic of Korea</center>

## Personal Data
---
> 1998.12.15 출생

> 연락처: heoj10272@skuniv.ac.kr

> Github : <a href="https://github.com/heoj10272">https://github.com/heoj10272</a>


## Education
---
> Mar.2017 ~ 현재 : 서경대학교 컴퓨터공학과<br>
> Feb.2022 ~ 현재 : SKU Algoritm Study<br>
> Jun.2022 ~ 현재 : AWSKRUG AWS Study


## Research Interest
---

* WEB
    + HTML
    + JSP
    + SPRING

* DATABASE
    + ORACLE
    + MYSQL

* CLOUD
    + AWS
    + GCP

## Project
---
시각장애인을 위한 장애물 탐지, 위치 공유 어플리케이션 개발

## Work Experiences
---
> **종이와 연필 - LG 유플러스**

> **종이와 연필 - LX Pantos**

## Skills and Certification
---
-Language : C++




