
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Get a Joke!</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(to right, #FF7F50, #FF6347);
      color: white;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 20px;
      height: 100vh;
      text-align: center;
      margin: 0;
    }

    h1 {
      font-size: 36px;
      margin-bottom: 20px;
      text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
    }

    p {
      font-size: 18px;
      margin-bottom: 30px;
    }

    .joke {
      background: #ffebcd;
      color: #333;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
      font-size: 22px;
      font-weight: bold;
      width: 60%;
      max-width: 500px;
      min-height: 120px;
      margin-top: 20px;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      margin-left: auto;
      margin-right: auto;
    }

    .joke:hover {
      transform: scale(1.05);
      box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
    }

    button {
      padding: 15px 30px;
      font-size: 18px;
      border: none;
      background-color: #ff6347;
      color: white;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 20px;
      transition: background-color 0.3s ease, transform 0.3s ease;
    }

    button:hover {
      background-color: #ff4500;
      transform: scale(1.1);
    }

    button:active {
      background-color: #d84b16;
    }

    .footer {
      position: absolute;
      bottom: 20px;
      width: 100%;
      text-align: center;
    }

    .footer span {
      font-size: 16px;
      color: white;
    }

    @media (max-width: 600px) {
      h1 {
        font-size: 28px;
      }

      button {
        font-size: 16px;
        padding: 12px 25px;
      }
    }
  </style>
</head>
<body>

<h1>Joke shop</h1>
<h1>Want to Hear a Joke?</h1>
<p>Click the button below to get a random joke</p>

<div class="joke" id="joke">
  Click the button to get a joke.
</div>

<button onclick="getJoke()">Get Joke</button>

<div class="footer">
  <span>&copy; 2025 Joke Shop. All rights reserved by CB.</span>
</div>

<script>
  async function getJoke() {
    try {
      const response = await fetch('https://v2.jokeapi.dev/joke/Any?type=single');
      const data = await response.json();

      if (data.error) {
        document.getElementById('joke').innerText = 'Sorry, no jokes available at the moment!';
      } else {
        document.getElementById('joke').innerText = data.joke;
      }
    } catch (error) {
      console.error('Error fetching joke:', error);
      document.getElementById('joke').innerText = 'Something went wrong. Please try again later!';
    }
  }
</script>

</body>
</html>
