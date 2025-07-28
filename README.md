<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Invitación Especial</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600&family=Open+Sans&display=swap" rel="stylesheet">
  <style>
    :root {
      --navy: #0b1a33;
      --gold: #d4af37;
      --white: #ffffff;
      --light-blue: #e9eff8;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      font-family: 'Open Sans', sans-serif;
      background-color: var(--white);
      color: var(--navy);
      line-height: 1.6;
    }

    .container {
      max-width: 800px;
      margin: auto;
      padding: 2rem;
    }

    .card {
      background: var(--light-blue);
      border: 2px solid var(--gold);
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
      padding: 2.5rem;
      margin-bottom: 2rem;
      opacity: 0;
      transform: translateY(50px);
      transition: all 0.8s ease-out;
    }

    .card.visible {
      opacity: 1;
      transform: translateY(0);
    }

    h1, h2 {
      font-family: 'Playfair Display', serif;
      color: var(--gold);
      text-align: center;
    }

    h1 {
      font-size: 2.5rem;
    }

    h2 {
      font-size: 2rem;
      margin-top: 1.5rem;
    }

    .line {
      height: 4px;
      width: 80px;
      background-color: var(--gold);
      margin: 1rem auto 2rem;
      border-radius: 10px;
    }

    p {
      text-align: center;
      font-size: 1.1rem;
      color: var(--navy);
    }

    .details {
      background-color: var(--white);
      border-left: 5px solid var(--gold);
      padding: 1.2rem;
      border-radius: 12px;
      margin-top: 1rem;
    }

    .details p {
      text-align: left;
      margin: 0.3rem 0;
    }

    .button {
      display: block;
      width: fit-content;
      margin: 2rem auto 1rem;
      background-color: var(--gold);
      color: var(--white);
      padding: 0.8rem 1.5rem;
      border-radius: 30px;
      text-decoration: none;
      font-weight: bold;
      transition: background-color 0.3s ease;
      box-shadow: 0 4px 10px rgba(0,0,0,0.15);
    }

    .button:hover {
      background-color: #b8912e;
    }

    .countdown {
      text-align: center;
      font-size: 1.2rem;
      margin: 1.5rem 0;
      color: var(--navy);
    }

    .footer {
      text-align: center;
      margin-top: 2rem;
      font-size: 0.95rem;
      color: #666;
    }

    @media (max-width: 600px) {
      h1 {
        font-size: 2rem;
      }

      h2 {
        font-size: 1.6rem;
      }
    }
  </style>
</head>
<body>

  <div class="container">

    <!-- Encabezado -->
    <div class="card" id="intro">
      <h1>Estás Invitado</h1>
      <p>A un día lleno de amor y bendiciones</p>
      <div class="line"></div>

      <div class="countdown">
        🕒 Faltan <span id="dias"></span> días, <span id="horas"></span> horas y <span id="minutos"></span> minutos para el gran día.
      </div>
    </div>

    <!-- Bautizo -->
    <div class="card" id="bautizo">
      <h2>Bautizo de Emiliano Rodríguez Gómez</h2>
      <p>Nos encantaría que nos acompañaras<br>en este momento tan especial.</p>

      <div class="details">
        <p><strong>📍 Lugar:</strong> Parroquia San José, Ciudad de México</p>
        <p><strong>📅 Fecha:</strong> Domingo 25 de agosto de 2025</p>
        <p><strong>⏰ Hora:</strong> 12:00 p.m.</p>
      </div>
    </div>

    <!-- Boda -->
    <div class="card" id="boda">
      <h2>Boda Civil de Mariana & Alejandro</h2>
      <p>Después del bautizo, celebremos también<br>nuestra unión civil.</p>

      <div class="details">
        <p><strong>📍 Lugar:</strong> Salón Gardenia, Ciudad de México</p>
        <p><strong>⏰ Hora:</strong> 2:00 p.m.</p>
      </div>
    </div>

    <!-- Confirmación -->
    <div class="card">
      <p>Te esperamos con cariño para celebrar en familia<br>este día tan especial. 💙💍✨</p>

      <a class="button" href="https://wa.me/5215555555555?text=Confirmo%20mi%20asistencia%20al%20bautizo%20y%20boda%20civil%20de%20Emiliano,%20Mariana%20y%20Alejandro." target="_blank">
        Confirmar Asistencia
      </a>

      <div class="footer">
        Con cariño: Familia Rodríguez Gómez
      </div>
    </div>

  </div>

  <script>
    // Mostrar tarjetas al hacer scroll
    const cards = document.querySelectorAll('.card');
    const showOnScroll = () => {
      const triggerBottom = window.innerHeight * 0.9;
      cards.forEach(card => {
        const boxTop = card.getBoundingClientRect().top;
        if (boxTop < triggerBottom) {
          card.classList.add('visible');
        }
      });
    };

    window.addEventListener('scroll', showOnScroll);
    window.addEventListener('load', showOnScroll);

    // Cuenta regresiva
    const evento = new Date("2025-08-25T12:00:00").getTime();
    const diasEl = document.getElementById("dias");
    const horasEl = document.getElementById("horas");
    const minutosEl = document.getElementById("minutos");

    function actualizarCuenta() {
      const ahora = new Date().getTime();
      const diferencia = evento - ahora;

      const dias = Math.floor(diferencia / (1000 * 60 * 60 * 24));
      const horas = Math.floor((diferencia % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutos = Math.floor((diferencia % (1000 * 60 * 60)) / (1000 * 60));

      diasEl.textContent = dias;
      horasEl.textContent = horas;
      minutosEl.textContent = minutos;
    }

    actualizarCuenta();
    setInterval(actualizarCuenta, 60000);
  </script>

</body>
</html>
