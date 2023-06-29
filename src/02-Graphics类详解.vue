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
	antialias: true, // 抗锯齿
});

// 将应用画布添加到DOM中
document.body.appendChild(app.view as any);

// 创建一个矩形
const rectangle = new PIXI.Graphics();
// 设置边框样式
rectangle.lineStyle(4, 0xff0000, 1);
rectangle.beginFill(0x66ccff);
rectangle.drawRect(200, 200, 300, 100);
rectangle.endFill();

rectangle.scale.set(2, 2); // 矩形缩放
rectangle.position.set(300, 100); // 位移，相对于左上角
rectangle.rotation = 0.5; // 旋转，相对于左上角
rectangle.pivot.set(150, 50); // 锚点 如旋转，位移的基点，x y 也是从左上角开始计算

// 将矩形添加到舞台
app.stage.addChild(rectangle);

// 创建一个圆形
const circle = new PIXI.Graphics();
circle.beginFill("yellow");
circle.drawCircle(0, 0, 32);
circle.endFill();
circle.position.set(300, 300);
app.stage.addChild(circle);
</script>
