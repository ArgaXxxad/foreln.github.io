<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Приключение Boba</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      text-align: center;
      background-image: url('https://i.pinimg.com/736x/be/c2/81/bec281f790dfaf7fd6ea3daa50b19f63.jpg');
      background-size: cover;
      background-position: center;
      color: white;
      transition: background-image 0.5s ease;
    }
    .overlay {
      background-color: rgba(0, 0, 0, 0.5);
      padding: 20px;
      border-radius: 10px;
      width: 90%;
      max-width: 600px;
    }
    h1 {
      font-size: 2.5rem;
      margin: 0;
      color: #ffcc00;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    }
    button {
      background-color: #ff6600;
      color: white;
      border: none;
      padding: 15px 30px;
      font-size: 1.2rem;
      cursor: pointer;
      border-radius: 5px;
      margin: 10px;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #cc5200;
    }
    .hidden {
      display: none;
    }
  </style>
</head>
<body>

  <div id="welcome-page" class="page">
    <div class="overlay">
      <h1>Привет, Boba!</h1>
      <p>Готов начать приключение?</p>
      <button onclick="startAdventure()">Йесс, Йессс!</button>
    </div>
  </div>

  <div id="role-selection-page" class="page hidden">
    <div class="overlay">
      <h2>Твоя роль сыщик</h2>
      <p>Выбор без выбора ВА ХА ХА</p>
      <button onclick="startTask()">Начать!</button>
    </div>
  </div>

  <div id="task-page" class="page hidden">
    <div class="overlay">
      <h1>Расшифруй это</h1>
      <p>Задание для тебя, Расшифруй это: <br> 01010100 01101000 01100101 00100000 01110000 01101100 01100001 01100011 01100101 00100000 01110111 01101000 01100101 01110010 01100101 00100000 01001001 00100000 01100111 01100001 01110110 01100101 00100000 01111001 01101111 01110101 00100000 01110100 01101000 01100101 00100000 01100010 01101111 01101111 01101011 00101100 00100000 01110111 01101000 01100001 01110100 00100111 01110011 00100000 01110100 01101000 01100101 00100000 01101110 01100001 01101101 01100101 00100000 01101111 01100110 00100000 01110100 01101000 01100101 00100000 01110000 01101100 01100001 01100011 01100101 00111111</p>
      <input type="text" id="user-response" placeholder="Введите ответ" />
      <button onclick="checkAnswer()">Отправить ответ</button>
      <div id="message"></div>
      <div id="hint"></div> <!-- Подсказка для двоичного кода -->
    </div>
  </div>

  <div id="quote-page" class="page hidden">
    <div class="overlay">
      <h1>Пусть будет терпимее к чужим чувствам.</h1>
      <p>В этой Вселенной и так маловато искренней любви.</p>
      <p><strong>Чья это фраза?</strong></p>
      <input type="text" id="quote-answer" placeholder="Введите ответ" />
      <button onclick="checkQuoteAnswer()">Отправить ответ</button>
      <div id="quote-message"></div>
    </div>
  </div>

  <div id="congratulation-page" class="page hidden">
    <div class="overlay">
      <h1>Поздравляем, Boba!</h1>
      <p>Ты прошел все задания и стал настоящим героем приключения!</p>
      <p>Запомни эти цифры, сделай Screenshot или запиши:</p>
      <div id="moving-numbers">
        <span style="font-weight: bold;">42.876151</span>, <span style="font-weight: bold;">74.614705</span>
      </div>
      <button onclick="continueAdventure()">Продолжить</button>
    </div>
  </div>

  <div id="final-question-page" class="page hidden">
    <div class="overlay">
      <h1>Как назывался фильм, который только вдвоем смотрели в Кинотеатре?</h1>
      <input type="text" id="final-answer" placeholder="Введите ответ" />
      <button onclick="checkFinalAnswer()">Отправить ответ</button>
      <div id="final-message"></div>
      <div id="hint"></div> <!-- Подсказка для финального вопроса -->
    </div>
  </div>

  <div id="new-page" class="page hidden">
    <div class="overlay">
      <h1>Поздравляем, ты выиграл! Но это только начало</h1>
      <button onclick="window.location.href='https://argaxxxad.github.io/Forelnt/'">Перейти на сайт</button>
    </div>
  </div>

  <script>
    function startAdventure() {
      document.getElementById("welcome-page").classList.add("hidden");
      document.getElementById("role-selection-page").classList.remove("hidden");
      document.body.style.backgroundImage = "url('https://i.pinimg.com/736x/56/66/99/5666990515d098359d3a78dc920d799c.jpg')";  // Фон для страницы "Роль сыщика"
    }

    function startTask() {
      document.getElementById("role-selection-page").classList.add("hidden");
      document.getElementById("task-page").classList.remove("hidden");
      document.body.style.backgroundImage = "url('https://i.pinimg.com/736x/8a/14/28/8a1428c84de967a20bbebb9b570053d7.jpg')";  // Фон для страницы задания
    }

    function checkAnswer() {
      const userResponse = document.getElementById("user-response").value.trim();
      const correctAnswer = "ЦУМ";  // правильный ответ
      const messageBox = document.getElementById("message");

      if (userResponse.toLowerCase() === correctAnswer.toLowerCase()) {
        messageBox.textContent = "Молодец!";
        messageBox.style.color = "#00FF00";
        setTimeout(() => {
          document.getElementById("task-page").classList.add("hidden");
          document.getElementById("quote-page").classList.remove("hidden");
          document.body.style.backgroundImage = "url('https://citaty.info/files/quote-pictures/442623-smeshariki.jpg')";  // Фон для страницы цитаты
        }, 2000);
      } else {
        messageBox.textContent = "Попробуй еще раз!";
        messageBox.style.color = "#FF0000";
        // Подсказка для двоичного кода
        const hintBox = document.getElementById("hint");
        hintBox.textContent = "Подсказка: попробуй перевести двоичный код в текст и ответить на вопрос!";
      }
    }

    function checkQuoteAnswer() {
      const userQuoteAnswer = document.getElementById("quote-answer").value.trim();
      const quoteMessageBox = document.getElementById("quote-message");

      if (userQuoteAnswer.toLowerCase() === "ежик" || userQuoteAnswer.toLowerCase() === "ёжик" || userQuoteAnswer.toLowerCase() === "ёж" || userQuoteAnswer.toLowerCase() === "еж") {
        quoteMessageBox.textContent = "Правильно!";
        quoteMessageBox.style.color = "#00FF00";
        setTimeout(() => {
          document.getElementById("quote-page").classList.add("hidden");
          document.getElementById("congratulation-page").classList.remove("hidden");
          document.body.style.backgroundImage = "url('https://i.pinimg.com/736x/f0/d7/99/f0d799f031476828b642107e53a47e3e.jpg')";  // Фон для страницы поздравления
        }, 2000);
      } else {
        quoteMessageBox.textContent = "Подсказка: это маленькое животное!";
        quoteMessageBox.style.color = "#FF0000";
      }
    }

    function continueAdventure() {
      document.getElementById("congratulation-page").classList.add("hidden");
      document.getElementById("final-question-page").classList.remove("hidden");
      document.body.style.backgroundImage = "url('https://static.kinoafisha.info/upload/articles/480272640223.jpg')";  // Фон для финального вопроса
    }

    function checkFinalAnswer() {
      const finalAnswer = document.getElementById("final-answer").value.trim().toLowerCase();
      const finalMessageBox = document.getElementById("final-message");
      const hintBox = document.getElementById("hint");

      if (finalAnswer === "призраки в венеции" || finalAnswer === "призраки") {
        finalMessageBox.textContent = "Ты прав!";
        finalMessageBox.style.color = "#00FF00";
        setTimeout(() => {
          document.getElementById("final-question-page").classList.add("hidden");
          document.getElementById("new-page").classList.remove("hidden");
          document.body.style.backgroundImage = "url('https://pic3.fc-zenit.ru/upload/gallery/video/13128/247153_s1200.jpg')";  // Фон для страницы победы
        }, 2000);
      } else {
        finalMessageBox.textContent = "Не сдавайся, попробуй еще раз!";
        finalMessageBox.style.color = "#FF0000";
        hintBox.textContent = "Подсказка: это фильм о духах!";
      }
    }
  </script>

</body>
</html>
