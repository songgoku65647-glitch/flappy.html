# flappy.html
Videogame 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dark King Flappy</title>
<style>
  body {
    margin: 0;
    background: #0a0a0a;
    display: flex;
    flex-direction: column;
    align-items: center;
    font-family: Arial, sans-serif;
    color: #ff0000;
  }
  canvas {
    background: #111;
    display: block;
    margin: 20px auto;
    border: 3px solid #ff0000;
  }
  h1 {
    text-align: center;
  }
</style>
</head>
<body>
<h1>Dark King Flappy</h1>
<p>Score: <span id="score">0</span></p>
<canvas id="gameCanvas" width="320" height="480"></canvas>

<script>
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

let bird = { x: 50, y: 240, width: 30, height: 30, velocity: 0 };
let gravity = 0.6;
let jump = -10;
let pipes = [];
let pipeWidth = 50;
let pipeGap = 120;
let frame = 0;
let score = 0;

function resetGame() {
  bird.y = 240;
  bird.velocity = 0;
  pipes = [];
  frame = 0;
  score = 0;
  document.getElementById('score').innerText = score;
}

function createPipe() {
  let topHeight = Math.random() * (canvas.height - pipeGap - 50) + 20;
  pipes.push({ x: canvas.width, top: topHeight, bottom: topHeight + pipeGap });
}

function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  // Draw bird
  ctx.fillStyle = '#ff0000';
  ctx.fillRect(bird.x, bird
