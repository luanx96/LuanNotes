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
            max-width: 600px;
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
        .buttons {
            margin-top: 20px;
        }
        .buttons button {
            margin-right: 10px;
        }
    </style>
</head>
<body>

<div class="quiz-container">
    <div class="quiz-question" id="questionText">
        <!-- Questão será inserida aqui via JavaScript -->
    </div>
    <div class="quiz-options" id="quizOptions">
        <!-- Opções serão inseridas aqui via JavaScript -->
    </div>
    <div class="buttons">
        <button onclick="checkAnswer()">Submit</button>
        <button onclick="showAnswer()">Mostrar Resposta</button>
        <button onclick="nextQuestion()">Próxima Questão</button>
        <button onclick="resetQuiz()">Tentar Novamente</button>
    </div>
    <div class="result" id="result">
        <p id="resultText"></p>
    </div>
</div>

<script>
    const questions = [
        {
            question: "Encontre o conjunto de soluções da inequação -2x - x + 1 >= 0",
            options: [
                "a. ]−1; 0,5]",
                "b. [−1; 0,5[",
                "c. [1; 0,5[",
                "d. [−1; 0,5]",
                "e. ]−1; 0,5["
            ],
            correctAnswer: "d"
        },
        {
            question: "Encontre o conjunto de soluções da inequação 3x^2 - x^2 >= 0",
            options: [
                "a. S = {x ∈ R / 3 <= x^2 >= 0}",
                "b. S = {x ∈ R / x = 3}",
                "c. S = {x ∈ R / 1 <= x^2 <= 3}",
                "d. S = {x ∈ R / 0 <= x^2 <= 3}",
                "e. S = {x ∈ R / 1 <= x^2 >= 3}"
            ],
            correctAnswer: "d"
        },
        {
            question: "Qual o resultado da inequação 2x - 18 > 4x - 38?",
            options: [
                "a. x > 10",
                "b. x é um número natural",
                "c. x = 10",
                "d. x é par",
                "e. x < 10"
            ],
            correctAnswer: "e"
        },
        {
            question: "Marque a alternativa que não representa a solução da inequação quociente x²−4x+3 > 0 / x²−7x+10",
            options: [
                "a. S = {1< x < 3 ou 2< x <5}",
                "b. S = {1 <= x <= 2 ou 3 <= x <= 5}",
                "c. S = {x <1 ou 2 < x < 3 ou x >5}",
                "d. S = {−1 < x ou − 3< x< − 2 ou x< − 5}",
                "e. S = {x > 1 ou 2< x < 5 }"
            ],
            correctAnswer: "b"
        },
        {
            question: "Em R, qual é a solução da inequação x−4 / 3x <= 0 ?",
            options: [
                "a. [4; + ∞ [",
                "b. ]- ∞ ; 0[ ∪ [4; + ∞ [",
                "c. ]- ∞ ; 4]",
                "d. ]0, 4]"
            ],
            correctAnswer: "c"
        },
        {
            question: "Os valores que não pertencem a solução da inequação: –x^2 – 3x – 2 <= 0 são?",
            options: [
                "a. S = {x ∈ R / -2 < x < -1}",
                "b. S = {x ∈ R / x <= 2 ou x > -1}",
                "c. S = {x ∈ R / x <= -1 ou x >= -2}",
                "d. S = {x ∈ R / x <= -2 ou x >= -1}"
            ],
            correctAnswer: "a"
        },
        {
            question: "Encontre as soluções da inequação 3x + 19 < 40 e diga qual é o primeiro número inteiro que a satisfaz:",
            options: [
                "a. x < 7",
                "b. 3 <= x <= 7",
                "c. x = 7",
                "d. x >= 7",
                "e. x = 6"
            ],
            correctAnswer: "e"
        },
        {
            question: "Encontre o conjunto de soluções da inequação x^2 - 6x + 5 <= 0.",
            options: [
                "a. S = {x ∈ R / 1 <= x <= 5}",
                "b. S = {x ∈ R / 1 >= x <= 5}",
                "c. S = {x ∈ R / 1 <= x = 5}",
                "d. S = {x ∈ R / 1 >= x >= 5}",
                "e. S = {x ∈ R / 1 <= x >= 5}"
            ],
            correctAnswer: "a"
        },
        {
            question: "A solução da inequação: (2x + 1) / (x + 2) <= 0 é?",
            options: [
                "a. S = {x ∈ R / -2 < x <= -1}",
                "b. S = {x ∈ R / -1 <= x <= 2}",
                "c. S = {x ∈ R / -2 <= x <= -1}",
                "d. S = {x ∈ R / -2 <= x >= -1}"
            ],
            correctAnswer: "c"
        },
        {
            question: "O conjunto numérico representado graficamente pela parte que está pintada de VERMELHO é:",
            options: [
                "a. ]− ∞ , −4[",
                "b. ]−4, + ∞ [",
                "c. ]− ∞ , −4]",
                "d. ] ∞ , −4]"
            ],
            correctAnswer: "a"
        }
    ];

    let currentQuestionIndex = 0;

    function loadQuestion() {
        const question = questions[currentQuestionIndex];
        document.getElementById('questionText').textContent = question.question;
        const optionsContainer = document.getElementById('quizOptions');
        optionsContainer.innerHTML = '';
        question.options.forEach((option, index) => {
            const label = document.createElement('label');
            label.innerHTML = `<input type="radio" name="quiz" value="${String.fromCharCode(97 + index)}"> ${option}`;
            optionsContainer.appendChild(label);
        });
    }

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
        const correctAnswer = questions[currentQuestionIndex].correctAnswer;

        if (selectedValue === correctAnswer) {
            resultText.textContent = 'Correto!';
            resultText.style.color = 'green';
        } else {
            resultText.textContent = 'Errado! Tente novamente.';
            resultText.style.color = 'red';
        }

        resultDiv.style.display = 'block';
    }

    function showAnswer() {
        const resultDiv = document.getElementById('result');
        const resultText = document.getElementById('resultText');
        
        resultText.textContent = `A resposta correta é: ${questions[currentQuestionIndex].correctAnswer}.`;
        resultText.style.color = 'blue';

        resultDiv.style.display = 'block';
    }

    function resetQuiz() {
        const options = document.getElementsByName('quiz');
        for (const option of options) {
            option.checked = false;
        }

        const resultDiv = document.getElementById('result');
        const resultText = document.getElementById('resultText');

        resultDiv.style.display = 'none';
        resultText.textContent = '';
    }

    function nextQuestion() {
        if (currentQuestionIndex < questions.length - 1) {
            currentQuestionIndex++;
            resetQuiz();
            loadQuestion();
        } else {
            alert("Você chegou ao fim do quiz!");
        }
    }

    window.onload = loadQuestion;
</script>

</body>
</html>
