<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Valentine's Seating Finder</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: system-ui, Arial, sans-serif;
      background: linear-gradient(135deg, #ff5f6d, #ffc371);
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0;
    }
    .card {
      background: white;
      padding: 2rem;
      border-radius: 16px;
      max-width: 400px;
      width: 100%;
      text-align: center;
      box-shadow: 0 10px 25px rgba(0,0,0,0.15);
    }
    h1 {
      margin-bottom: 1rem;
    }
    input {
      padding: 12px;
      width: 100%;
      border-radius: 8px;
      border: 1px solid #ddd;
      margin-bottom: 1rem;
      font-size: 16px;
    }
    button {
      padding: 12px;
      width: 100%;
      border: none;
      border-radius: 8px;
      background: #ff5f6d;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background: #e94b5a;
    }
    .result {
      margin-top: 1rem;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <div class="card">
    <h1>💘 Find Your Seat</h1>
    <p>Enter your full name</p>
    <input id="name" placeholder="e.g. John Doe" />
    <button onclick="findSeat()">Find My Seat</button>
    <div class="result" id="result"></div>
  </div>

  <script>
    const guests = {
      "John Doe": "Table 2, Seat B",
      "Jane Smith": "Table 1, Seat A",
      "Michael Brown": "Table 3, Seat C"
      // ADD MORE NAMES BELOW
    };

    function normalize(str) {
      return str.trim().toLowerCase();
    }

    function findSeat() {
      const nameInput = normalize(document.getElementById("name").value);
      const resultEl = document.getElementById("result");

      const entry = Object.entries(guests).find(
        ([name]) => normalize(name) === nameInput
      );

      if (entry) {
        resultEl.innerHTML = `🎉 You are seated at <br><strong>${entry[1]}</strong>`;
      } else {
        resultEl.innerHTML = "❌ Name not found. Please check spelling or see the host.";
      }
    }
  </script>

</body>
</html>
