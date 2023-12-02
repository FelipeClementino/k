<!D<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Date hoje?</title>
  <style>
    /* Estilos simples para o layout */
    body {
      font-family: Arial, sans-serif;
      position: relative;
      height: 100vh;
      margin: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: #f4f4f4;
      overflow: hidden;
    }
    .container {
      text-align: center;
    }
    button {
      padding: 10px 20px;
      margin: 10px;
      cursor: pointer;
      border: none;
      border-radius: 5px;
      position: absolute;
      z-index: 1;
    }
    #sim {
      background-color: #2ecc71; /* Verde */
      color: white;
      left: 50%;
      transform: translateX(-100%);
    }
    #nao {
      background-color: #e74c3c; /* Vermelho */
      color: white;
      left: 50%;
      transform: translateX(50%);
    }
    .heart {
      color: red;
      position: absolute;
      font-size: 40px;
      animation: float 3s ease-in-out infinite;
      z-index: 0;
    }
    @keyframes float {
      0% {
        transform: translateY(0);
      }
      50% {
        transform: translateY(-20px);
      }
      100% {
        transform: translateY(0);
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Date hoje?</h1>
    <button id="sim" onclick="handleResponse('sim')">Sim</button>
    <button id="nao" onmouseover="moveAway()">Não</button>
  </div>

  <script>
    function handleResponse(response) {
      if (response === 'sim') {
        createHearts();
        sendEmailNotification('Resposta: Sim');
      } else {
        sendEmailNotification('Resposta: Não');
      }
    }

    function moveAway() {
      const naoButton = document.getElementById('nao');
      const randomX = Math.random() * (window.innerWidth - naoButton.clientWidth);
      const randomY = Math.random() * (window.innerHeight - naoButton.clientHeight);
      
      naoButton.style.left = `${randomX}px`;
      naoButton.style.top = `${randomY}px`;
    }

    function createHearts() {
      const heartsContainer = document.createElement('div');
      heartsContainer.className = 'hearts-container';

      for (let i = 0; i < 15; i++) {
        const heart = document.createElement('div');
        heart.className = 'heart';
        heart.innerHTML = '&hearts;';
        heart.style.left = `${Math.random() * window.innerWidth}px`;
        heart.style.top = `${Math.random() * window.innerHeight}px`;
        heartsContainer.appendChild(heart);
      }

      document.body.appendChild(heartsContainer);
    }

    function sendEmailNotification(message) {
      // Simulação de envio de e-mail: exibir mensagem no console
      console.log('Email enviado:', message);
    }
  </script>
</body>
</html>
