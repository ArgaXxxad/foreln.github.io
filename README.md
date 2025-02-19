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
    }
    h1 {
      font-size: 3rem;
      margin: 0;
      color: #ffcc00;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    }
    p {
      font-size: 1.5rem;
      margin: 20px 0;
      color: #ffffff;
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
    .role-selection {
      margin-top: 20px;
    }
    .role-description {
      font-size: 1rem;
      color: #ddd;
      margin-top: 10px;
    }
    .response-box {
      margin-top: 20px;
    }
    input {
      padding: 10px;
      font-size: 1rem;
      margin-right: 10px;
      border-radius: 5px;
    }
    .message {
      margin-top: 20px;
      font-size: 1.5rem;
      color: #ffcc00;
      font-weight: bold;
    }
    #back-button {
      position: absolute;
      top: 20px;
      left: 20px;
    }
    .answer-line {
      margin-top: 20px;
      font-size: 1.2rem;
      color: #ddd;
    }

    /* Стили для пятой страницы с цифрами */
    #congratulation-page .moving-numbers {
      font-size: 2rem;
      font-weight: bold;
      color: #00FF00;
      position: absolute;
      top: 60%; /* Поднимаем блок с цифрами ниже */
      left: 50%;
      transform: translateX(-50%);
      white-space: nowrap;
      margin-top: 20px; /* Добавим немного пространства сверху */
    }

    /* Новая страница для продолжения */
    #continue-page {
      display: none;
      text-align: center;
      background-color: rgba(0, 0, 0, 0.7);
      padding: 30px;
      border-radius: 10px;
    }

  </style>
</head>
<body>

  <!-- Первая страница: Приветствие -->
  <div id="welcome-page">
    <div class="overlay">
      <h1>Привет, Boba!</h1>
      <p>Готов начать приключение?</p>
      <button onclick="startAdventure()">Йесс, Йессс!</button>
    </div>
  </div>

  <!-- Вторая страница: Выбор роли -->
  <div id="role-selection-page" class="hidden">
    <div class="overlay">
      <h2>Выбери роль</h2>
      <p>В зависимости от роли будут разные задания, загадки и головоломки.</p>
      <div class="role-selection">
        <button onmouseover="changeBackground('Сыщик')" onmouseout="resetBackground()" onclick="startTask('Сыщик')">Сыщик</button>
        <button onmouseover="changeBackground('Ученый')" onmouseout="resetBackground()" onclick="alert('Задания для этой роли еще нет!')">Ученый</button>
        <button onmouseover="changeBackground('Маг')" onmouseout="resetBackground()" onclick="alert('Задания для этой роли еще нет!')">Маг</button>
      </div>
      <p class="role-description" id="role-description"></p>
    </div>
  </div>

  <!-- Третья страница: Задание -->
  <div id="task-page" class="hidden">
    <div class="overlay">
      <h1>Расшифруй это</h1>
      <p>Задание для тебя: <br> 01001001 01100110 00100000 01111001 01101111 01110101 00100000 01100111 01110101 01100101 01110011 01110011 01100101 01100100 00100000 01110100 01101000 01100001 01110100 00101100 00100000 01100111 01101111 01101111 01100100 00100000 01100110 01101111 01110010 00100000 01111001 01101111 01110101 00101110 00100000 01001110 01101111 01110111 00101100 00100000 01110111 01110010 01101001 01110100 01100101 00100000 01100100 01101111 01110111 01101110 00100000 01110111 01101000 01100101 01110010 01100101 00100000 01111001 01101111 01110101 00100000 01100001 01101110 01100100 00100000 01001001 00100000 01100110 01101001 01110010 01110011 01110100 00100000 01101101 01100101 01110100 00101110</p>

      <div class="response-box">
        <input type="text" id="user-response" placeholder="Введите ответ" />
        <button onclick="checkAnswer()">Отправить ответ</button>
      </div>

      <div id="message" class="message"></div>
      
      <button id="back-button" onclick="goBackToRoleSelection()">Назад</button>
    </div>
  </div>

  <!-- Четвертая страница: Цитата -->
  <div id="quote-page" class="hidden">
    <div class="overlay">
      <h1>Пусть будет терпимее к чужим чувствам.</h1>
      <p>В этой Вселенной и так маловато искренней любви.</p>
      <p><strong>Чья это фраза?</strong></p>

      <!-- Поле для ответа -->
      <div class="response-box">
        <input type="text" id="quote-answer" placeholder="Введите ответ" />
        <button onclick="checkQuoteAnswer()">Отправить ответ</button>
      </div>

      <div id="quote-message" class="message"></div>
      
      <button id="back-button" onclick="goBackToTaskPage()">Назад</button>
    </div>
  </div>

  <!-- Пятая страница: Поздравление с цифрами -->
  <div id="congratulation-page" class="hidden">
    <div class="overlay">
      <h1>Поздравляем, Boba!</h1>
      <p>Ты прошел все задания и стал настоящим героем приключения!</p>
      
      <!-- Текст с цифрами, теперь жирным шрифтом -->
      <p>Запомни эти цифры, сделай Screenshot или запиши:</p>
      <div id="moving-numbers" class="moving-numbers">
        <span style="font-weight: bold;">42.876151</span>, <span style="font-weight: bold;">74.614705</span>
      </div>
      
      <!-- Кнопка продолжить -->
      <button onclick="continueAdventure()">Продолжить</button>
    </div>
  </div>

  <!-- Страница продолжения -->
  <div id="continue-page" class="hidden">
    <div class="overlay">
      <h1>Ты достиг великого успеха!</h1>
      <p>Теперь ты готов к новым испытаниям. Следующая глава приключения открывается!</p>
      <!-- Здесь можно добавить дополнительные задания или историю -->
      <button onclick="goBackToRoleSelection()">Вернуться на начало</button>
    </div>
  </div>

  <script>
    // Функция для начала приключения
    function startAdventure() {
      document.getElementById("welcome-page").classList.add("hidden");
      document.getElementById("role-selection-page").classList.remove("hidden");
    }

    // Функция для изменения фона при наведении
    function changeBackground(role) {
      const body = document.querySelector("body");
      const description = document.getElementById("role-description");

      if (role === "Сыщик") {
        body.style.backgroundImage = "url('https://sun1-97.userapi.com/s/v1/ig2/HP7YJ-zW62AOivEPO5P0-RycIHwdFDD7efVjVshc3feYPU2lyZBdotS3f1msU7w2R6Z1Cfw89ltnSakUhdfKNlKg.jpg?quality=96&as=32x32,48x48,72x72,108x108,160x160,240x240,360x360,480x480,540x540,640x640,647x647&from=bu&u=jMrqUchmbZ_50KqD9MNchgoUzw2vxzpUo_UFlOi3Wzk&cs=604x604')";
        description.textContent = "Ты — мастер загадок и поиска подсказок. Твоя задача — находить скрытые улики и разгадывать тайны.";
      } else if (role === "Ученый") {
        body.style.backgroundImage = "url('https://sun9-61.userapi.com/impf/qUXOZgzeX_gtxOav5VcB2HxDrXPLRGm6pZvkSw/XD-Pw0j1D6w.jpg?size=604x604&quality=96&sign=3aad37af161d608001a0bdca241e8a27&type=album')";
        description.textContent = "Ты — эксперт по логике и анализу. Твоя задача — решать сложные головоломки и находить научные решения.";
      } else if (role === "Маг") {
        body.style.backgroundImage = "url('https://i.pinimg.com/736x/80/dc/a0/80dca0ccac827bd73762ad12d15400ae.jpg')";
        description.textContent = "Ты — мастер магии и тайн. Твоя задача — использовать свои способности, чтобы раскрыть секреты.";
      }
    }

    // Функция для перехода к заданию (только для Сыщика)
    function startTask(role) {
      if (role === "Сыщик") {
        document.getElementById("role-selection-page").classList.add("hidden");
        document.getElementById("task-page").classList.remove("hidden");
      }
    }

    // Функция для проверки правильности ответа на задание
    function checkAnswer() {
      const userResponse = document.getElementById("user-response").value.trim();
      const messageBox = document.getElementById("message");

      if (userResponse === "ЦУМ" || userResponse === "Цум" || userResponse === "цум") {
        messageBox.textContent = "Молодец принцесса!";
        messageBox.style.color = "#00FF00"; // Зеленый цвет для успеха
        setTimeout(() => {
          document.getElementById("task-page").classList.add("hidden");
          document.getElementById("quote-page").classList.remove("hidden");
        }, 2000); // Переход на следующую страницу через 2 секунды
      } else {
        messageBox.textContent = "Попробуй еще раз!";
        messageBox.style.color = "#FF0000"; // Красный цвет для ошибки
      }
    }

    // Функция для проверки правильности ответа на цитату
    function checkQuoteAnswer() {
      const userQuoteAnswer = document.getElementById("quote-answer").value.trim();
      const quoteMessageBox = document.getElementById("quote-message");

      if (userQuoteAnswer.toLowerCase() === "ежик" || userQuoteAnswer.toLowerCase() === "ёжик" || userQuoteAnswer.toLowerCase() === "ёж" || userQuoteAnswer.toLowerCase() === "еж") {
        quoteMessageBox.textContent = "Надеюсь ты не использовала интернет?! haha";
        quoteMessageBox.style.color = "#00FF00"; // Зеленый цвет для успеха
        setTimeout(() => {
          document.getElementById("quote-page").classList.add("hidden");
          document.getElementById("congratulation-page").classList.remove("hidden");
        }, 2000); // Переход на поздравительную страницу через 2 секунды
      } else {
        quoteMessageBox.textContent = "Попробуй еще раз!";
        quoteMessageBox.style.color = "#FF0000"; // Красный цвет для ошибки
      }
    }

    // Функция для продолжения приключения
    function continueAdventure() {
      document.getElementById("congratulation-page").classList.add("hidden");
      document.getElementById("continue-page").classList.remove("hidden");
    }

    // Функция для возврата на страницу выбора роли
    function goBackToRoleSelection() {
      document.getElementById("task-page").classList.add("hidden");
      document.getElementById("role-selection-page").classList.remove("hidden");
    }

    // Функция для возврата на страницу задания
    function goBackToTaskPage() {
      document.getElementById("quote-page").classList.add("hidden");
      document.getElementById("task-page").classList.remove("hidden");
    }

  </script>

</body>
</html>
