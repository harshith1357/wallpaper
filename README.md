<!DOCTYPE html>
<html>
<head>
    <title>Mind Reader</title>
    <style>
        .input {
            border-radius: 20px;
            padding: 30px 30px;
            text-align: center;
            margin: 0 auto;
            width: 80%;
            max-width: 400px;
            padding: 2em 4em;
            font-size: 40px;
            margin-left: 3em;
            margin-top: 8em;
            background-color: black;
            color: white;
            box-shadow: inset 0px 0px 10px, 0px 0px 35px lightpink;
            font-weight: 700;
        }

        .dialogue-box {
            background-color: black;
            color: white;
            text-align: center;
            font-size: 40px;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
        }

        .hidden {
            display: none;
        }

        .button {
            border-radius: 20px;
            margin-top: 20px;
            padding: 80px 90px;
            font-size: 40px;
            position: absolute;
            top: 20em;
            transition: 0.1s;
            color: lightblue;
            background-color: black;
            box-shadow: 0px 0px 25px lightblue;
        }

        .button:active {
            background-color: lightblue;
        }

        .loader {
            border: 16px solid #f3f3f3;
            border-radius: 50%;
            border-top: 16px solid #3498db;
            width: 120px;
            height: 120px;
            -webkit-animation: spin 2s linear infinite; /* Safari */
            animation: spin 2s linear infinite;
        }

        body {
            justify-content: center;
            align-items: center;
            display: flex;
            background-color: black;
        }

        /* Safari */
        @-webkit-keyframes spin {
            0% {
                -webkit-transform: rotate(0deg);
            }
            100% {
                -webkit-transform: rotate(360deg);
            }
        }

        @keyframes spin {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }

        .text {
            text-align: center;
            position: absolute;
            font-size: 80px;
            color: white;
            top: 10px;
            text-shadow: 0px 0px 10px red;
            animation-name: text;
            animation-duration: 4s;
        }

        @keyframes text {
            0% {
                top: -150px;
            }
            100% {
                top: 10px;
            }
        }

        .note {
            position: absolute;
            text-align: center;
            color: white;
            font-size: 60px;
            top: 20em;
            -webkit-text-stroke: 1px red;
            animation-name: note;
            animation-duration: 2s;
        }

        .strong {
            color: black;
            -webkit-text-stroke: 2px red;
        }

        @keyframes note {
            from {
                top: 90em;
            }
            to {
                top: 20em;
            }
        }

    </style>
</head>
<body>
    <P class="text">Name Converter ..</P>
    <p class="note"> <strong class="strong">Note</strong>:Know your Name in Japanese</p>
    <input id="numberInput" class="input" placeholder="Enter your Name" pattern="[A-Za-z]+" title="Please enter only alphabets." required/>
    <button class="button" onclick="showNumber()">Submit</button>
    <div id="dialogueBox" class="dialogue-box hidden"></div>

    <script>
        function translateName(nameInput) {
            const translationMap = {
                'a': 'ka', 'b': 'tu', 'c': 'mi', 'd': 'te', 'e': 'ku',
                'f': 'ru', 'g': 'ji', 'h': 're', 'i': 'ki', 'j': 'zu',
                'k': 'me', 'l': 'ta', 'm': 'rin', 'n': 'to', 'o': 'mo',
                'p': 'no', 'q': 'ke', 'r': 'shi', 's': 'su', 't': 'chi',
                'u': 'do', 'v': 'ru', 'w': 'mei', 'x': 'na', 'y': 'fu', 'z': 'ze'
            };
            let translatedName = '';

            for (let i = 0; i < nameInput.length; i++) {
                const char = nameInput.charAt(i).toLowerCase();
                const translation = translationMap[char] || char; // Use translation from map or the original char if not found
                translatedName += translation;
            }

            return translatedName;
        }

        function showNumber() {
            var inputElement = document.getElementById('numberInput');
            var areaName = inputElement.value;
            var dialogueBox = document.getElementById('dialogueBox');

            // Clear previous message
            dialogueBox.innerHTML = '';

            // Validate input
            if (!/^[a-zA-Z]+$/.test(areaName)) {
                dialogueBox.innerHTML = 'Please enter only alphabets.';
            } else {
                // Translate the entered area name
                var translatedName = translateName(areaName);

                // Show dialogue box
                dialogueBox.classList.remove('hidden');

                // Create loading spinner
                var loadingSpinner = document.createElement('div');
                loadingSpinner.classList.add('loader');

                // Append loading spinner to dialogue box
                dialogueBox.appendChild(loadingSpinner);

                // Create loading message
                var loadingMessage = document.createElement('p');
                loadingMessage.innerHTML = 'Analysing your Name...';

                // Append loading message to dialogue box
                dialogueBox.appendChild(loadingMessage);

                // Simulate loading delay
                setTimeout(function () {
                    // Update loading message
                    loadingMessage.innerHTML = 'Converting your Name ...';

                    // Simulate additional loading delay
                    setTimeout(function () {
                        // Clear loading spinner and message
                        dialogueBox.innerHTML = '';

                        // Display translated area name and the weather query
                        var resultMessage = document.createElement('p');
                        resultMessage.innerHTML = '' + translatedName;

                        // Append result message to dialogue box
                        dialogueBox.appendChild(resultMessage);
                    }, 2000); // Adjust the delay as needed
                }, 2000); // Adjust the delay as needed
            }
        }
    </script>
</body>
</html

