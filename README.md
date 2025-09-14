<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Zombie Shooter</title>
<link rel="manifest" href="manifest.json">
<style>
html,body{height:100%;margin:0;background:#050608;color:#eee;font-family:Inter,system-ui,Arial}
#container{width:100%;height:100%;position:relative;overflow:hidden}
canvas{display:block}
.hud{position:absolute;left:12px;top:12px;z-index:10}
.panel{position:absolute;right:12px;top:12px;background:rgba(0,0,0,0.6);padding:10px;border-radius:8px}
#shop{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);background:rgba(4,6,10,0.96);padding:18px;border:2px solid #2b0000;border-radius:12px;display:none;z-index:50;width:min(980px,94%);max-height:86%;overflow:auto}
.btn{display:inline-block;padding:8px 12px;background:#0b7cc6;color:white;border-radius:8px;cursor:pointer;margin-right:8px}
.preview3d{width:300px;height:300px;background:#0a0a0a;border-radius:8px;display:flex;align-items:center;justify-content:center}
.shop-list{max-height:520px;overflow:auto}
.char-row{padding:8px;border-bottom:1px solid rgba(255,255,255,0.03);display:flex;justify-content:space-between;align-items:center}
.small{font-size:12px;color:#b8c7d9}
.loadingScreen{position:absolute;left:0;right:0;top:0;bottom:0;background:linear-gradient(180deg,#000 0%,#05050a 60%);display:flex;flex-direction:column;align-items:center;justify-content:center;z-index:60}
.menu{position:absolute;left:0;right:0;top:0;bottom:0;display:flex;flex-direction:column;align-items:center;justify-content:center;z-index:55}
.menuCard{background:rgba(2,2,2,0.8);padding:18px;border-radius:12px;border:1px solid rgba(255,0,0,0.06);text-align:center}
.copyright{font-size:12px;color:#9faab6;margin-top:12px}
.footerNote{position:absolute;left:50%;transform:translateX(-50%);bottom:12px;color:#8c9aa6;font-size:12px}
</style>
</head>
<body>
<div id="container"></div>

<div class="loadingScreen" id="loadingScreen">
<h1 style="font-size:48px;color:#ff3b3b;margin:0">Zombie Shooter</h1>
<div class="copyright">© 2025 Leostar. All rights reserved.<br>No part of this game may be reproduced.<br>Names, costumes, characters, and all elements are the trademarks of Leostar.</div>
<div style="height:18px"></div>
<div class="menuCard" style="margin-top:18px">
<div style="margin-bottom:10px"><button class="btn" id="btnPlay">Play</button> <button class="btn" id="btnShop">Shop</button></div>
<div style="margin-top:10px" class="small">Move: WASD • Aim: Mouse • Shoot: Click/Touch • Switch weapon: 1–8</div>
</div>
</div>

<div class="hud" id="hud" style="display:none">
<div class="row">Level: <span id="level">1</span>  Score: <span id="score">0</span>  Money: $<span id="money">0</span></div>
<div class="row">Character: <span id="charName">Lowbrown</span> | Weapon: <span id="weaponName">Pistol</span></div>
<div class="row"><button class="btn" id="openShop">Open Shop</button></div>
</div>

<div class="panel" id="rightPanel" style="display:none">
<div>Lives: <span id="lives">3</span></div>
<div>Enemies: <span id="enemiesCount">0</span></div>
</div>

<div id="shop">
<h2>Shop — Weapons & Characters</h2>
<div style="display:flex;gap:12px">
<div class="preview3d" id="preview3d">Preview</div>
<div style="flex:1">
<div style="display:flex;gap:8px;margin-bottom:8px">
<div class="btn" id="tabWeapons">Weapons</div>
<div class="btn" id="tabCharacters">Characters# Leo
