# CengkB.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Random Dog Website</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
      background-color: #f0f8ff;
    }

    h1 {
      color: #333;
    }

    img {
      width: 300px;
      border-radius: 10px;
      margin-top: 20px;
      box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
    }

    button {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      background-color: #4CAF50;
      color: white;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    button:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body>
  <h1>Random Dog Image</h1>
  
  <div id="content"></div>
  
  <button onclick="getDogImage()">Get New Dog</button>

  <script>
    async function getDogImage() {
      try {
        const response = await fetch('https://dog.ceo/api/breeds/image/random');
        const data = await response.json();
        const contentDiv = document.getElementById('content');
        contentDiv.innerHTML = ''; // Eski fotoğrafı temizle
        const img = document.createElement('img');
        img.src = data.message;
        img.alt = "Random Dog";
        contentDiv.appendChild(img);
      } catch (error) {
        console.error('Error fetching dog image:', error);
      }
    }

    
    getDogImage();
  </script>
</body>
</html>
