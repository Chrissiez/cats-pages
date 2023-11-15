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
        textarea {
            width: 80%;
            height: 100px;
        }
    </style>
</head>
<body>
    <h2>Binary Shift Code Game</h2>

    <label for="text">Enter the text to encode:</label><br>
    <textarea id="text" placeholder="Enter text"></textarea><br>
    <button onclick="encodeText()">Encode Text</button><br>
    <label for="encodedBinary">Encoded Binary:</label><br>
    <textarea id="encodedBinary" readonly></textarea><br><br>

    <label for="shiftAmount">Enter the shift amount:</label><br>
    <input type="number" id="shiftAmount" placeholder="Enter shift amount" min="1" value="1"><br>
    <button onclick="shiftBinary()">Shift Binary</button><br>
    <label for="shiftedBinary">Shifted Binary:</label><br>
    <textarea id="shiftedBinary" readonly></textarea><br><br>

    <button onclick="decodeText()">Decode Text</button><br>
    <label for="decodedText">Decoded Text:</label><br>
    <textarea id="decodedText" readonly></textarea>

    <script>
        function textToBinary(text) {
            return text.split('').map(char => ' ' + char.charCodeAt(0).toString(2).padStart(8, '0')).join('');
        }

        function binaryToText(binary) {
            return binary.split(' ').map(binVal => String.fromCharCode(parseInt(binVal, 2))).join('');
        }

        function encodeText() {
            const textInput = document.getElementById('text').value;
            const encodedBinary = textToBinary(textInput);
            document.getElementById('encodedBinary').value = encodedBinary.trim();
        }

        function shiftBinary() {
            const encodedBinary = document.getElementById('encodedBinary').value.replace(/\s+/g, ' ');
            const shiftAmount = parseInt(document.getElementById('shiftAmount').value, 10);
            const shiftedBinary = encodedBinary.split(' ').map(binVal => shiftBinaryValue(binVal, shiftAmount)).join('');
            document.getElementById('shiftedBinary').value = shiftedBinary.trim();
        }

        function shiftBinaryValue(binaryValue, shiftAmount) {
            const binaryArray = binaryValue.split('');
            for (let i = 0; i < binaryArray.length; i++) {
                if (binaryArray[i] !== ' ') {
                    binaryArray[i] = binaryArray[i] === '0' ? '1' : '0';
                }
            }
            return binaryArray.join('');
        }

function decodeText() {
    const shiftedBinary = document.getElementById('shiftedBinary').value.replace(/\s+/g, ' ');
    const decodedText = binaryToText(shiftedBinary);

    if (decodedText.trim() === '') {
        document.getElementById('decodedText').value = 'Invalid binary input. Please check the binary code and try again.';
    } else {
        document.getElementById('decodedText').value = 'Decoded Text: ' + decodedText;
    }
}
    </script>
</body>
</html>
