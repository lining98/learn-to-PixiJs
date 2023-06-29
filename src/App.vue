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

// 创建一个矩形
const rectangle = new PIXI.Graphics()
rectangle.beginFill(0x66ccff)
rectangle.drawRect(200,200,164,64)
rectangle.endFill()

// 将矩形添加到舞台
app.stage.addChild(rectangle)
</script>

<style lang="css">
canvas {
	width: 100vw;
	height: 100vh;
	position: absolute;
	left: 0;
	top: 0;
}
</style>
