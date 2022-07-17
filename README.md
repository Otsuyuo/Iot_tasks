# Iot_task1-
Convert Speech to Text
<!DOCTYPE html>
<html lang="en">
  
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content=
        "width=device-width, initial-scale=1.0">
  
    <title>Speech to Text</title>
    <style type="text/css">
        body {background-color: powderblue;}
        .words{ max-width: 100px;
                margin: 0 auto;
                margin-top: 100px;
                padding: 15px 100px;
                text-align: center;
                background-color: white;}

    </style>
</head>
  
<body>
    <div class="words" contenteditable>
        <p style = "color:red;" >Your speech :</p>
        <p></p>
        <p id="p"></p>
    </div>
    
  
    <script>
        var speech = true;
        window.SpeechRecognition = window.SpeechRecognition
                        || window.webkitSpeechRecognition;
  
        const recognition = new SpeechRecognition();
        recognition.interimResults = true;
        const words = document.querySelector('.words');
        words.appendChild(p);
  
        recognition.addEventListener('result', e => {
            const transcript = Array.from(e.results)
                .map(result => result[0])
                .map(result => result.transcript)
                .join('')
  
            document.getElementById("p").innerHTML = transcript;
            console.log(transcript);
        });
          
        if (speech == true) {
            recognition.start();
            recognition.addEventListener('end', recognition.start);
        }
    </script>
</body>
  
</html>
