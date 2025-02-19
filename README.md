<!DOCTYPE html>
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
      background-image: url('https://i.pinimg.com/736x/be/c2/81/bec281f790dfaf7fd6ea3daa50b19f63.jpg'); /* Замени ссылку на изображение */
      background-size: cover;
      background-position: center;
      color: white;
      transition: background-image 0.5s ease; /* Плавный переход фона */
    }
    .overlay {
      background-color: rgba(0, 0, 0, 0.5); /* Затемнение фона для лучшей читаемости текста */
      padding: 20px;
      border-radius: 10px;
    }
    h1 {
      font-size: 3rem;
      margin: 0;
      color: #ffcc00; /* Желтый цвет, как в "Смешариках" */
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    }
    p {
      font-size: 1.5rem;
      margin: 20px 0;
      color: #ffffff;
    }
    button {
      background-color: #ff6600; /* Оранжевый цвет, как у Кроша */
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
      background-color: #cc5200; /* Темнее оранжевый при наведении */
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
        <button onmouseover="changeBackground('Сыщик')" onmouseout="resetBackground()">Сыщик</button>
        <button onmouseover="changeBackground('Ученый')" onmouseout="resetBackground()">Ученый</button>
        <button onmouseover="changeBackground('Маг')" onmouseout="resetBackground()">Маг</button>
      </div>
      <p class="role-description" id="role-description"></p>
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
        body.style.backgroundImage = "url('https://sun1-97.userapi.com/s/v1/ig2/HP7YJ-zW62AOivEPO5P0-RycIHwdFDD7efVjVshc3feYPU2lyZBdotS3f1msU7w2R6Z1Cfw89ltnSakUhdfKNlKg.jpg?quality=96&as=32x32,48x48,72x72,108x108,160x160,240x240,360x360,480x480,540x540,640x640,647x647&from=bu&u=jMrqUchmbZ_50KqD9MNchgoUzw2vxzpUo_UFlOi3Wzk&cs=604x604')"; // Изображение для Сыщика
        description.textContent = "Ты — мастер загадок и поиска подсказок. Твоя задача — находить скрытые улики и разгадывать тайны.";
      } else if (role === "Ученый") {
        body.style.backgroundImage = "url('https://sun9-61.userapi.com/impf/qUXOZgzeX_gtxOav5VcB2HxDrXPLRGm6pZvkSw/XD-Pw0j1D6w.jpg?size=604x604&quality=96&sign=3aad37af161d608001a0bdca241e8a27&type=album')"; // Изображение для Ученого
        description.textContent = "Ты — эксперт по логике и анализу. Твоя задача — решать сложные головоломки и находить научные решения.";
      } else if (role === "Маг") {
        body.style.backgroundImage = "url('https://i.pinimg.com/736x/80/dc/a0/80dca0ccac827bd73762ad12d15400ae.jpg')"; // Изображение для Мага
        description.textContent = "Ты — мастер магии и тайн. Твоя задача — использовать свои способности, чтобы раскрыть секреты.";
      }
    }

    // Функция для сброса фона на исходный
    function resetBackground() {
      const body = document.querySelector("body");
      body.style.backgroundImage = "url('https://i.pinimg.com/736x/be/c2/81/bec281f790dfaf7fd6ea3daa50b19f63.jpg')"; // Исходное изображение
    }
  </script>

</body>
</html>
