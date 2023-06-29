<template>
	<div>app</div>
</template>

<script setup lang="ts">
// 导入pixi
import * as PIXI from "pixi.js";

// 创建应用
const app = new PIXI.Application({
	width: window.innerWidth,
	height: window.innerHeight,
	backgroundColor: 0x1099bb,
	resolution: window.devicePixelRatio || 1, // 像素比
});

// 将应用画布添加到DOM中
document.body.appendChild(app.view as any);

// 添加场景1的资源
PIXI.Assets.addBundle("scene1", {
	pic1: "https://pic.rmb.bdstatic.com/05b0ea405c9e690ab51627853a13de56.jpeg",
	pic2: "https://img14.360buyimg.com/pop/jfs/t1/23739/35/2224/12087/5c1b0581E1fa6c1c3/58519cee2a0039e0.jpg",
});

const assets = PIXI.Assets.loadBundle("scene1", (progress) => {
	console.log("加载完成", progress);
});

// 异步加载资源
const texturesPromise = PIXI.Assets.load(["pic1", "pic2"], (progress) => {
	console.log("加载完成", progress);
});

// 加载完成后创建精灵
// texturesPromise.then((textures) => {
assets.then((textures) => {
	// 创建容器
	const container = new PIXI.Container();
	// 创建一个精灵
	const sprite = new PIXI.Sprite(textures.pic2);
	// 锚点
	sprite.anchor.set(0.5, 0.5);

	// 设置位置
	sprite.x = app.screen.width / 2;
	sprite.y = app.screen.height / 2;

	// 旋转45度
	sprite.rotation = Math.PI / 4;

	// 设置缩放
	sprite.scale.set(2, 2);

	// 设置透明度
	sprite.alpha = 0.8;

	// 将精灵添加到舞台
	container.addChild(sprite);

	// 创建精灵2
	const sprite2 = new PIXI.Sprite(textures.pic1);
	sprite2.scale.set(0.2);
	container.addChild(sprite2);
	app.stage.addChild(container);
});
</script>
