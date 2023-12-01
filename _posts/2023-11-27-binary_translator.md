---
toc: true
comments: false
layout: post
title: binary translator
description: transforms words to binary
type: hacks
courses: { compsci: {week: 7} }
---

<!DOCTYPE HTML>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Binary Translator</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f4f4f4;
      font-family: Arial, sans-serif;
    }

    .translator-container {
      text-align: center;
      border: 2px solid #333;
      padding: 20px;
      border-radius: 10px;
      background-color: white;
      margin: 10px;
    }

    input {
      margin: 5px;
      padding: 8px;
      font-size: 16px;
      width: 80%;
      box-sizing: border-box;
    }

    button {
      margin: 5px;
      padding: 10px;
      font-size: 16px;
      cursor: pointer;
      transition: background-color 0.3s ease-in-out;
    }

    #colorShift {
      background-color: #123;
      transition: background-color 0.5s ease-in-out;
    }

    p {
      padding: 5px;
      margin: 5px;
      font-size: 14px;
      color: #333;
    }

    #currentColor, #currentBinary {
      background-color: purple;
      color: white;
      padding: 8px;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <div class="translator-container">
    <label for="text">Text:</label>
    <br>
    <input type="text" id="text" placeholder="Enter text">
    <br>
    <button onclick="textToBinary()">To Binary</button>
    <br>
    <label for="binary">Binary:</label>
    <br>
    <input type="text" id="binary" placeholder="Enter binary">
    <br>
    <button onclick="binaryToText()">To Text</button>
  </div>
  <div class="translator-container" id="colorShift">
    <p id="currentColor">Current Color: #123</p>
    <p id="currentBinary">Current Binary: 01111011</p>
    <button onclick="shiftLeft()">Shift Left</button>
    <br>
    <button onclick="shiftRight()">Shift Right</button>
  </div>
  <script>
    let backgroundColor = '123';
    let backgroundColorBinary;

    function textToBinary() {
      const textInput = document.getElementById('text').value;
      const binaryOutput = textInput.split('').map(char => char.charCodeAt(0).toString(2)).join(' ');
      document.getElementById('binary').value = binaryOutput;
    }

    function binaryToText() {
      const binaryInput = document.getElementById('binary').value;
      const textOutput = binaryInput.split(' ').map(bin => String.fromCharCode(parseInt(bin, 2))).join('');
      document.getElementById('text').value = textOutput;
    }

    function shiftLeft() {
      backgroundColorBinary = Number(backgroundColor).toString(2);
      backgroundColorBinary += "0";
      backgroundColor = parseInt(backgroundColorBinary, 2);
      updateColor();
    }

    function shiftRight() {
      backgroundColorBinary = Number(backgroundColor).toString(2);
      backgroundColorBinary = backgroundColorBinary.substring(0, backgroundColorBinary.length - 1);
      backgroundColor = parseInt(backgroundColorBinary, 2);
      updateColor();
    }

    function updateColor() {
      document.getElementById("currentColor").textContent = "Current Color: #" + backgroundColor;
      document.getElementById("currentBinary").textContent = "Current Binary: " + backgroundColorBinary;
      document.getElementById("colorShift").style.backgroundColor = "#" + backgroundColor;
    }
  </script>
</body>
</html>




