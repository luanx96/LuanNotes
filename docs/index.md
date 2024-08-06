<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .quiz-container {
            max-width: 400px;
            margin: 50px auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .quiz-question {
            margin-bottom: 20px;
        }
        .quiz-options label {
            display: block;
            margin-bottom: 10px;
        }
        .result {
            display: none;
            margin-top: 20px;
        }
    </style>
</head>
<body>

<div class="quiz-container">
    <div class="quiz-question">
        <h2>Qual é a capital da França?</h2>
    </div>
    <div class="quiz-options">
        <label>
            <input type="radio" name="quiz" value="a"> Roma
        </label>
        <label>
            <input type="radio" name="quiz" value="b"> Madrid
        </label>
        <label>
            <input type="radio" name="quiz" value="c"> Paris
        </label>
        <label>
            <input type="radio" name="quiz" value="d"> Lisboa
        </label>
    </div>
    <button onclick="checkAnswer()">Submit</button>
    <div class="result" id="result">
        <p id="resultText"></p>
    </div>
</div>

<script>
    function checkAnswer() {
        const options = document.getElementsByName('quiz');
        let selectedValue;
        for (const option of options) {
            if (option.checked) {
                selectedValue = option.value;
                break;
            }
        }

        const resultDiv = document.getElementById('result');
        const resultText = document.getElementById('resultText');

        if (selectedValue === 'c') {
            resultText.textContent = 'Correto! Paris é a capital da França.';
            resultText.style.color = 'green';
        } else {
            resultText.textContent = 'Errado! Tente novamente.';
            resultText.style.color = 'red';
        }

        resultDiv.style.display = 'block';
    }
</script>

</body>
</html>
