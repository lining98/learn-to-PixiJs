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

// 创建一个纹理
const texture = PIXI.Texture.from("./vite.svg");

// 创建一个精灵
const sprite = new PIXI.Sprite(texture);
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
sprite.alpha = 0.6;

// 将精灵添加到舞台
app.stage.addChild(sprite);

// ticker 实现动画
app.ticker.add((delta) => {
	sprite.rotation += 0.01 * delta;
});

// 为精灵添加交互事件
sprite.interactive = true;
// 精灵派加点击事件
sprite.on("click", (e) => {
	console.log(e, "sprite click");
});

// 鼠标进入移出事件
sprite.on("pointerenter", () => (sprite.alpha = 1));
sprite.on("pointerleave", () => (sprite.alpha = 0.5));

// 创建矩形
const rect = new PIXI.Graphics()
rect.beginFill(0xff0000)
rect.drawRect(300, 300, 150, 150)
rect.endFill()

app.stage.addChild(rect)
rect.interactive = true

// 给矩形添加点击事件
rect.on("click", e => {
  console.log(e, "rect click!")
})
</script>
