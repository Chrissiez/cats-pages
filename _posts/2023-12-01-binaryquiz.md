---
toc: true
comments: false
layout: post
title: binary 
description: Our quiz along with binary translator
type: hacks
courses: { compsci: {week: 7} }
---
<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f2e6ff; /* Light Purple background color */
            display: grid;
            place-items: center;
            min-height: 100vh;
        }

        /* Style for the question containers */
        .question-container {
            background-color: #000;
            border-radius: 10px;
            box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
            max-width: 400px;
            margin: 10px;
            padding: 20px;
            text-align: left;
        }

        /* Style for question titles */
        .question h2 {
            font-size: 18px;
            color: #000; /* Set font color to black */
        }

        /* Style for answer choices */
        .question ul {
            list-style-type: none;
            padding: 0;
        }

        .question li {
            padding: 8px 0;
            color: #000; /* Set font color to black */
        }

        /* Style for the correct answer reveal */
        .question details {
            margin-top: 15px;
            cursor: pointer;
        }

        .question summary {
            font-weight: bold;
            color: #000; /* Set font color to black */
        }

        /* Style for the correct answer */
        .question details p {
            margin: 0;
            color: #009900; /* Green color for correct answer */
        }

        /* Arrange questions in two rows using grid layout */
        .questions-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
        }
    </style>
</head>
<body>
    <div class="questions-grid">
        <div class="question-container">
            <div class="question">
                <h2>Binary Question 1</h2>
                <p>How many bits are in binary colors?</p>
                <ul>
                    <li>A) 24</li>
                    <li>B) 16</li>
                    <li>C) 8</li>
                    <li>D) 5</li>
                </ul>
                <details>
                    <summary>Click to reveal the correct answer</summary>
                    <p>The correct answer is A) 24 bits, as there is 8 bits of data for 3 color channels</p>
                </details>
            </div>
        </div>

        <div class="question-container">
            <div class="question">
                <h2>Binary Question 2</h2>
                <p>Convert 30 into a binary number?</p>
                <ul>
                    <li>A) 00011001</li>
                    <li>B) 00011011</li>
                    <li>C) 00011110</li>
                    <li>D) 00111111</li>
                </ul>
                <details>
                    <summary>Click to reveal the correct answer</summary>
                    <p>The correct answer is B) 00011110, solve the problem out. We recommend using a paper and pencil.</p>
                </details>
            </div>
        </div>

        <div class="question-container">
            <div class="question">
                <h2> Computer Science Principals Question 3</h2>
                <p>What is a bit?</p>
                <ul>
                    <li>A) a bit piece of something</li>
                    <li>B) Basic Unit of information and computing and digital communications</li>
                    <li>C) Computer science</li>
                </ul>
                <details>
                    <summary>Click to reveal the correct answer</summary>
                    <p>The correct answer is B) Basic Unit of information and computing and digital communications</p>
                </details>
            </div>
        </div>
    </div>
</body>
</html>






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
       }
       input {
           margin: 5px;
           padding: 8px;
           font-size: 16px;
       }
       button {
           margin: 5px;
           padding: 10px;
           font-size: 16px;
           cursor: pointer;
       }
        #colorShift {
            background-color: #123; 
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
       <p id="currentColor" style="background-color: purple;">Current Color: #123</p>
       <p id="currentBinary" style="background-color: purple;">Current Binary: 01111011</p>
       <button onclick="shiftLeft()">shift left</button>
       <br>
       <button onclick="shiftRight()">shift Right</button>
       <br>
   </div>
   <script>
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
        var backgroundColor = '123';
        var backgroundColorBinary;
        function shiftLeft() {
            backgroundColorBinary = Number(backgroundColor).toString(2);
            backgroundColorBinary = backgroundColorBinary + "0";
            backgroundColor = parseInt(backgroundColorBinary, 2);
            document.getElementById("currentColor").textContent = "Current Color: #" + backgroundColor;
            document.getElementById("currentBinary").textContent = "Current Binary: " + backgroundColorBinary;
            document.getElementById("colorShift").style.background = "#" + backgroundColor;
       }
       function shiftRight() {
            backgroundColorBinary = Number(backgroundColor).toString(2);
            backgroundColorBinary = backgroundColorBinary.substring(0, backgroundColorBinary.length-1);
            backgroundColor = parseInt(backgroundColorBinary, 2);
            document.getElementById("currentColor").textContent = "Current Color: #" + backgroundColor;
            document.getElementById("currentBinary").textContent = "Current Binary: " + backgroundColorBinary;
            document.getElementById("colorShift").style.background = "#" + backgroundColor;
       }
   </script>
</body>
</html>
