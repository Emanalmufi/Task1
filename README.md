# Task1 
```
<?php Header("Cache-Control: max-age=3000, must-revalidate"); ?>
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta http-equiv="Cache-Control" content="no-cache, no-store, must-revalidate" />
        <meta http-equiv="Pragma" content="no-cache" />
        <meta http-equiv="Expires" content="0" />
        <title>Speech to text conversion using JavaScript</title>
        <meta name="description" content="">
        <meta name="viewport" content="width=device-width, initial-scale=1">

        <link href="https://fonts.googleapis.com/css?family=Shadows+Into+Light" rel="stylesheet">

    </head>
    <body>
        <div class="mycontainer">

            <h1>Speech to text conversion using JavaScript</h1>

            <div class="mywebapp"> 
                <div class="input">
                    <textarea id="textbox" rows="6"></textarea>
                </div>         
                <button id="start-btn" title="Start">Start</button>
                <p id="instructions">Press the Start button</p>
            </div>
        </div>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
        <script src="script.js"></script>
        <script>
            var SpeechRecognition = window.webkitSpeechRecognition;
  var recognition = new SpeechRecognition();
  var Textbox = $('#textbox');
  var instructions = $('instructions');
  var Content = '';
  recognition.continuous = true;
  recognition.onresult = function(event) {
    var current = event.resultIndex;
    var transcript = event.results[current][0].transcript;
      Content += transcript;
      Textbox.val(Content);
  };
  recognition.onstart = function() { 
    instructions.text('Running.');
  }
  recognition.onspeechend = function() {
    instructions.text('No activity.');
  }
  recognition.onerror = function(event) {
    if(event.error == 'no-speech') {
      instructions.text('Try again.');  
    }
  }
  $('#start-btn').on('click', function(e) {
    if (Content.length) {
      Content += ' ';
    }
    recognition.start();
  });
  Textbox.on('input', function() {
    Content = $(this).val();
  })
        </script>
    </body>
</html>
```
##ForESP32
Steps:
1- Plug the ESP32 to your PC or laptob by using micro cable.
2- Go to Tools > Board > Boards Manager > from the search bar write "esp32" > click on install.
3- Go to Tools > Board > select the name of your ESP32 board.
4- Go to Tools > Port and select a COM port available.
5- write the following code in arduion editor :

/* 
```
  Blink

  Turns an LED on for one second, then off for one second, repeatedly.

  Most Arduinos have an on-board LED you can control. On the UNO, MEGA and ZERO
  it is attached to digital pin 13, on MKR1000 on pin 6. LED_BUILTIN is set to
  the correct LED pin independent of which board is used.
  If you want to know what pin the on-board LED is connected to on your Arduino
  model, check the Technical Specs of your board at:
  https://www.arduino.cc/en/Main/Products

  modified 8 May 2014
  by Scott Fitzgerald
  modified 2 Sep 2016
  by Arturo Guadalupi
  modified 8 Sep 2016
  by Colby Newman

  This example code is in the public domain.

  https://www.arduino.cc/en/Tutorial/BuiltInExamples/Blink
*/

// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for a second
}
```
6- Press the upload button
