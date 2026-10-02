---
title: "DIY 2.4GHz Signal Jammer"
date: 2026-09-30T12:19:00-07:00
draft: false
author: "nosebleeeddd"
tags:
  - DIY
  - Soldering
  - Jammer
image: /images/jammer2.4ghz.jpg
description: "asdad"
toc: true
mathjax: false
---

## Flashing Firmware

This schematic is compatible with the EmenstaV1 Firmware on Github.
Use the web flasher to flash the firmware to ESP32, 

hold down boot to enable flasher.


Disrupts up to 10 meters.

Upgrade NRF24 to E01-ML01DP5 for longer range disruption!

### Build Materials:
```
proto-board x1
ESP32 WROOM-U x1
NRF24L01+PA+LNA x2-4
blue led x1
10uF 50v electrolytic CAP x2
104 ceramic CAP x2
4.7k ohm Resistor x1
0.96 OLED I2C x1
3.7V Li-Ion Battery x1
JST PH 2.0 Connector x1
TP4056 Charging Module (Micro-USB/Type-C) x1
Mini Slide Switch x1
Button x1
PVC Board
M3 Nut/Screw
```

<div id="jam-fig" style="float:right;margin:0 0 20px 25px;width:240px;text-align:center;">
<img id="jam-thumb" src="/images/jammer.jpg" alt="Jammer Pic" style="width:100%;display:block;cursor:zoom-in;" data-images="/images/jammer.jpg,/images/jammer1.jpg,/images/jammer2.jpg,/images/jammer3.jpg,/images/jammer4.jpg,/images/jammer2.4ghz.jpg" />
<div id="jam-label" style="margin-top:6px;font-size:14px;opacity:.75;cursor:pointer;"></div>
</div>
<div id="jam-viewer" hidden>
<button id="jam-close" aria-label="Close gallery">&times;</button>
<button id="jam-prev" aria-label="Previous picture">&#8249;</button>
<button id="jam-next" aria-label="Next picture">&#8250;</button>
<div id="jam-track"></div>
<div id="jam-count"></div>
</div>
<style>
#jam-viewer{position:fixed;inset:0;z-index:9999;background:rgba(0,0,0,.95);display:flex}
#jam-viewer[hidden]{display:none}
#jam-track{display:flex;width:100%;height:100%;overflow-x:auto;scroll-snap-type:x mandatory;scrollbar-width:none}
#jam-track::-webkit-scrollbar{display:none}
#jam-track .slide{flex:0 0 100%;height:100%;scroll-snap-align:center;display:flex;align-items:center;justify-content:center;padding:48px 56px;box-sizing:border-box;color:#fff;font:16px sans-serif}
#jam-track img{max-width:100%;max-height:100%;object-fit:contain}
#jam-viewer button{position:absolute;z-index:2;background:rgba(255,255,255,.12);color:#fff;border:0;cursor:pointer;font-size:32px;line-height:1;width:44px;height:44px;border-radius:50%}
#jam-viewer button:hover,#jam-viewer button:focus-visible{background:rgba(255,255,255,.3);outline:none}
#jam-close{top:12px;right:12px}
#jam-prev{left:10px;top:50%;transform:translateY(-50%)}
#jam-next{right:10px;top:50%;transform:translateY(-50%)}
#jam-count{position:absolute;bottom:14px;left:0;right:0;text-align:center;color:#ddd;font:14px sans-serif}
@media (max-width:600px){#jam-prev,#jam-next{display:none}#jam-track .slide{padding:48px 8px}}
</style>
<script>
(function(){
  var thumb=document.getElementById('jam-thumb'),
      label=document.getElementById('jam-label'),
      viewer=document.getElementById('jam-viewer'),
      track=document.getElementById('jam-track'),
      count=document.getElementById('jam-count');
  var urls=thumb.dataset.images.split(',');
  label.textContent='1 / '+urls.length+' \u2013 click to view all';
  urls.forEach(function(u){
    var s=document.createElement('div');s.className='slide';
    var i=document.createElement('img');i.src=u;i.alt='Jammer picture';
    i.onerror=function(){s.textContent='Could not load '+u;};
    s.appendChild(i);track.appendChild(s);
  });
  function update(){
    var n=Math.round(track.scrollLeft/track.clientWidth)+1;
    count.textContent=n+' / '+urls.length;
  }
  function step(d){track.scrollBy({left:d*track.clientWidth,behavior:'smooth'});}
  function open(){
    viewer.hidden=false;document.body.style.overflow='hidden';
    track.scrollLeft=0;update();
    document.getElementById('jam-close').focus();
  }
  function close(){viewer.hidden=true;document.body.style.overflow='';}
  thumb.addEventListener('click',open);
  label.addEventListener('click',open);
  document.getElementById('jam-close').addEventListener('click',close);
  document.getElementById('jam-prev').addEventListener('click',function(){step(-1);});
  document.getElementById('jam-next').addEventListener('click',function(){step(1);});
  track.addEventListener('scroll',update);
  track.addEventListener('click',function(e){if(e.target===track||e.target.className==='slide')close();});
  document.addEventListener('keydown',function(e){
    if(viewer.hidden)return;
    if(e.key==='Escape')close();
    if(e.key==='ArrowLeft')step(-1);
    if(e.key==='ArrowRight')step(1);
  });
})();
</script>


### NOTES:
For the 0.96 Display I bent female header pins to make a socket, 
this way we can disconnect the display for portability

After wiring/soldering everything I used double sided tape to mount the 3.7v to the PVC cutout.

I also used double sided tape for the TP4056 Chargeboard on the back of the protoboard,
that way we can use the JST connector to easily disconnect the lipo and open the device if needed.



