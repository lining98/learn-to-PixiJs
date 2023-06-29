<template>
	<div></div>
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

// 绘制圆形
const ellipse = new PIXI.Graphics();
ellipse.beginFill(0x66ccff);
ellipse.drawEllipse(0, 0, 164, 64);
ellipse.endFill();
ellipse.position.set(300, 200);
app.stage.addChild(ellipse);

// 绘制多边形
const polygon = new PIXI.Graphics();
polygon.beginFill(0x660000);
// 参数一个数组，数组中的每一个元素是一个点的坐标，每两个元素是一个点的x坐标和y坐标
polygon.drawPolygon([0, 0, 100, 0, 100, 100, 0, 100]);
polygon.endFill();
polygon.position.set(600, 200);
app.stage.addChild(polygon);

// 绘制多边形
const arc = new PIXI.Graphics();
arc.beginFill(0x660000);
// arc(x坐标,y坐标,半径,其实角度,结束角度,顺/逆时针)
arc.arc(0, 0, 32, 0, Math.PI, false);
arc.endFill();
arc.position.set(300, 400);
app.stage.addChild(arc);

// 绘制线段
const line = new PIXI.Graphics();
line.lineStyle(10,0x660000,0.6); // 宽度，颜色，透明度
line.moveTo(0, 0);
line.lineTo(100, 100);
line.lineTo(200, 50);
line.endFill();
line.position.set(500, 400);
app.stage.addChild(line);
</script>
