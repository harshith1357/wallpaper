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
        box-shadow: inset 0px 0px 10px, 0px 0px 35px lightblue;
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
        transition: 0.5s;
        color: lightpink;
        background-color: black;
        box-shadow: 0px 0px 25px lightpink;
      }
      .button:active {
        background-color: lightpink;
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
      .emoji {
        font-size: 80px;
      }
    </style>
    <script>
      function showNumber() {
        var inputElement = document.getElementById('numberInput');
        var number = inputElement.value;
        var dialogueBox = document.getElementById('dialogueBox');

        // Clear previous message
        dialogueBox.innerHTML = '';

        // Validate input
        if (isNaN(number)) {
          dialogueBox.innerHTML = 'Please enter a number.';
        } else {
          // Show dialogue box
          dialogueBox.classList.remove('hidden');

          // Create loading spinner
          var loadingSpinner = document.createElement('div');
          loadingSpinner.classList.add('loader');

          // Append loading spinner to dialogue box
          dialogueBox.appendChild(loadingSpinner);

          // Create loading message
          var loadingMessage = document.createElement('p');
          loadingMessage.innerHTML = 'Decoding your mind...';

          // Append loading message to dialogue box
          dialogueBox.appendChild(loadingMessage);

          // Simulate loading delay
          var delay = 5000; // 5 seconds
          var interval = setInterval(function() {
            // Update loading message
            loadingMessage.innerHTML = 'Reading your mind...';

            // Stop interval after 2 seconds
            setTimeout(function() {
              // Clear loading spinner and message
              dialogueBox.innerHTML = '';

              // Display entered number
              var resultMessage = document.createElement('p');
              resultMessage.innerHTML = 'Your Thinking of Number: ' + number;

              // Append result message to dialogue box
              dialogueBox.appendChild(resultMessage);

              // Display smiling face emojis
              var emojis = document.createElement('div');
              emojis.classList.add('emoji');
              emojis.innerHTML = '&#129325; &#129325; &#129325;';

              // Append emojis to dialogue box
              dialogueBox.appendChild(emojis);
            }, 2000); // Adjust the delay as needed
          }, delay);
        }
      }
    </script>
  </head>
  <body>
    <p class="text">I can Read Your Mind..</p>
    <p class="note"><strong class="strong">Note</strong>: This is a very powerful Mind reader. Do it at your own risk.</p>
    <input id="numberInput" class="input" placeholder="Enter a Number Here" />
    <button class="button" onclick="showNumber()">Submit</button>
    <div id="dialogueBox" class="dialogue-box hidden"></div>
  </body>
</html>

