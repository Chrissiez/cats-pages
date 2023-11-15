<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Binary Shift Code Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }

        #binaryCode {
            font-size: 18px;
            margin-bottom: 20px;
        }

        #decodedText {
            font-size: 20px;
            font-weight: bold;
        }

        #shiftButton {
            padding: 10px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Binary Shift Code Game</h1>

    <div id="binaryCode">01001000 01100101 01101100 01101100 01101111</div>
    <button id="shiftButton" onclick="shiftBinary()">Shift</button>
    <div id="decodedText"></div>

    <script>
        let currentShift = 0;

        function binaryToText(binary) {
            return binary.split(' ').map(bin => String.fromCharCode(parseInt(bin, 2))).join('');
        }

        function shiftBinary() {
            const binaryCodeElement = document.getElementById('binaryCode');
            const decodedTextElement = document.getElementById('decodedText');

            const binaryCode = binaryCodeElement.innerText.trim().replace(/\s+/g, ' ');
            const decodedText = binaryToText(binaryCode);

            currentShift++;
            const shiftedBinary = [...decodedText].map(char => (char.charCodeAt(0) + currentShift).toString(2)).join(' ');

            binaryCodeElement.innerText = shiftedBinary;
            decodedTextElement.innerText = 'Decoded Text: ' + decodedText;
        }
    </script>
</body>
</html>
