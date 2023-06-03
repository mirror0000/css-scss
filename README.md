# CSS-SCSS
This repo is a project to design and implement various animations including 3D and slider using CSS and SCSS.
All animations were inspired and implemented by CodePen.
- [CSS-SCSS](#css-scss)
  - [Table of contents](#table-of-contents)
  - [3D Card](#3d-card)
    - [CSS](#css)
  - [3D Carousel](#3d-carousel)
    - [Start Effect](#start-effect)
    - [Image 3D Effect](#image-3d-effect)
    - [Mouse Event Effect](#mouse-event-effect)
  - [3D Card Effect](#3d-card-effect)
    - [Add mouse event listener](#add-mouse-event-listener)
  - [3D Image Hover](#3d-image-hover)
    - [Animation](#animation)

## Table of contents[](#table-of-contents)
- 3D Card

## 3D Card[](#3d-card)
<img align="center" src="/screenshot/3D_Card/screenshot.jpg" alt="3D Card" style="width:100%;height:100%"/>
This project is a project that implements a 3D card using CSS.

### CSS
```
.card:hover .wrapper {
  transform: perspective(900px) translateY(-5%) rotateX(25deg) translateZ(0);
  box-shadow: 2px 35px 32px -8px rgba(0, 0, 0, 0.75);
  -webkit-box-shadow: 2px 35px 32px -8px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 2px 35px 32px -8px rgba(0, 0, 0, 0.75);
}
```

## 3D Carousel[](#3d-carousel)
<img align="center" src="/screenshot/3D_Carousel/Carousel.jpg" alt="3D_Carousel" style="width:100%;height:100%"/>
This project is a project that implements the image carousel effect using CSS and JavaScript.

### Start Effect
```
for (var i = 0; i < imgs.length; i++) {
    imgs[i].style.transform = "rotateY(" + i * (360 / imgs.length) + "deg) translateZ(" + radius + "px)";
    imgs[i].style.transition = "transform 1s";
    imgs[i].style.transitionDelay = delayTime || (imgs.length - i) / 4 + "s";
  }
```

### Image 3D Effect
```
img {
  transform-style: preserve-3d;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  line-height: 200px;
  font-size: 50px;
  text-align: center;
  box-shadow: 0 0 8px #fff;
  -webkit-box-reflect: below 10px linear-gradient(transparent, transparent, #0005);
}
```

### Mouse Event Effect
```
document.onpointerdown = function (e) {
  clearInterval(wheel.timer);
  e = e || window.event;
  var sX = e.clientX, sY = e.clientY;

  this.onpointermove = function (e) {
    e = e || window.event;
    var nX = e.clientX, nY = e.clientY;
    desX = nX - sX;
    desY = nY - sY;
    tX += desX * 0.1;
    tY += desY * 0.1;
    applyTransform(wheel);
    sX = nX;
    sY = nY;
  };

  this.onpointerup = function (e) {
    wheel.timer = setInterval(function () {
      desX *= 0.95;
      desY *= 0.95;
      tX += desX * 0.1;
      tY += desY * 0.1;
      applyTransform(wheel);
      playSpin(false);
      if (Math.abs(desX) < 0.5 && Math.abs(desY) < 0.5) {
        clearInterval(wheel.timer);
        playSpin(true);
      }
    }, 17);
    this.onpointermove = this.onpointerup = null;
  };

  return false;
};
```

## 3D Card Effect[](#3d-card-effect)
<img align="center" src="/screenshot/3D_Card_Effect/3D_Card_Effect.jpg" alt="3D Card Effect" style="width:100%;height:100%"/>
This project is a project that shows a 3D card using mouse events.

### Add mouse event listener
```
container.addEventListener("mousemove", (e) => {
  let X = (window.innerWidth / 2 - e.pageX) / 30;
  let Y = (window.innerHeight / 2 - e.pageY) / 30;

  card.style.transition = "none";
  card.style.transform = `rotateX(${X}deg) rotateY(${Y}deg)`;
});
```

## 3D Image Hover[](#3d-image-hover)
<img align="center" src="/screenshot/3D_Image_Hover/3DImageHover.jpg" alt="3D Image Hover" style="width:100%;height:100%"/>
This project implemented multiple sliders animation using CSS.

### Animation
```
.container:hover img:nth-child(4) {
  transform: translate(160px, -160px);
  opacity: 1;
}

.container:hover img:nth-child(3) {
  transform: translate(120px, -120px);
  opacity: 0.8;
}

.container:hover img:nth-child(2) {
  transform: translate(80px, -80px);
  opacity: 0.6;
}

.container:hover img:nth-child(1) {
  transform: translate(40px, -40px);
  opacity: 0.4;
}
```