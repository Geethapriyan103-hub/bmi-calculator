# bmi-calculator
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>BMI Calculator with Age & Gender</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #e3f2fd;
      padding: 20px;
      text-align: center;
    }

    .container {
      max-width: 400px;
      margin: 50px auto;
      background: white;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 12px rgba(0, 0, 0, 0.15);
    }

    input[type="number"], input[type="radio"] {
      margin: 10px 0;
    }

    input[type="number"] {
      width: 80%;
      padding: 10px;
      font-size: 16px;
    }

    .gender-group {
      margin: 10px 0;
    }

    button {
      padding: 10px 20px;
      font-size: 16px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 15px;
    }

    button:hover {
      background-color: #0056b3;
    }

    .result {
      margin-top: 20px;
      font-size: 18px;
    }

    .status {
      font-weight: bold;
      color: #28a745;
    }
  </style>
</head>
<body>

  <div class="container">
    <h2>BMI Calculator</h2>

    <label for="age">Age:</label><br>
    <input type="number" id="age" placeholder="Enter your age"><br>

    <div class="gender-group">
      Gender:<br>
      <label><input type="radio" name="gender" value="Male" checked> Male</label>
      <label><input type="radio" name="gender" value="Female"> Female</label>
    </div>

    <label for="weight">Weight (kg):</label><br>
    <input type="number" id="weight" placeholder="Enter your weight"><br>

    <label for="height">Height (cm):</label><br>
    <input type="number" id="height" placeholder="Enter your height"><br>

    <button onclick="calculateBMI()">Calculate BMI</button>

    <div class="result" id="result"></div>
  </div>

  <script>
    function calculateBMI() {
      let age = document.getElementById("age").value;
      let weight = document.getElementById("weight").value;
      let height = document.getElementById("height").value;
      let gender = document.querySelector('input[name="gender"]:checked').value;

      if (age === "" || weight === "" || height === "") {
        alert("Please fill in all fields.");
        return;
      }

      height = height / 100;
      let bmi = weight / (height * height);
      bmi = bmi.toFixed(2);

      let status = "";

      if (bmi < 18.5) {
        status = "Underweight";
      } else if (bmi >= 18.5 && bmi < 24.9) {
        status = "Normal weight";
      } else if (bmi >= 25 && bmi < 29.9) {
        status = "Overweight";
      } else {
        status = "Obese";
      }

      document.getElementById("result").innerHTML = `
        Age: <strong>${age}</strong><br>
        Gender: <strong>${gender}</strong><br>
        Your BMI is <strong>${bmi}</strong><br>
        <span class="status">${status}</span>
      `;
    }
  </script>

</body>
</html>
