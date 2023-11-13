<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Binary Code Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        textarea {
            width: 80%;
            height: 100px;
        }
    </style>
</head>
<body>
    <h2>Binary Code Converter</h2>

    <label for="text">Enter the text to convert to binary:</label><br>
    <textarea id="text" placeholder="Enter text"></textarea><br>
    <button onclick="textToBinary()">Convert to Binary</button><br>
    <label for="binary">Binary Code:</label><br>
    <textarea id="binary" readonly></textarea><br><br>

    <label for="binaryInput">Enter the binary code to convert to text:</label><br>
    <textarea id="binaryInput" placeholder="Enter binary code"></textarea><br>
    <button onclick="binaryToText()">Convert to Text</button><br>
    <label for="textOutput">Text:</label><br>
    <textarea id="textOutput" readonly></textarea>

    <script>
        function textToBinary() {
            const textInput = document.getElementById('text').value;
            const binaryOutput = textInput.split('').map(char => ' ' + char.charCodeAt(0).toString(2).padStart(8, '0')).join('');
            document.getElementById('binary').value = binaryOutput.trim();
        }

        function binaryToText() {
            const binaryInput = document.getElementById('binaryInput').value.replace(/\s+/g, ' ');
            const textOutput = binaryInput.split(' ').map(binVal => String.fromCharCode(parseInt(binVal, 2))).join('');
            document.getElementById('textOutput').value = textOutput;
        }
    </script>
</body>
</html>
