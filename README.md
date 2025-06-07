<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>BMI Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 400px;
            margin: 50px auto;
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 8px;
            background-color: #f9f9f9;
        }
        h1 {
            text-align: center;
            color: #4f2626;
        }
        label {
            display: block;
            margin-top: 15px;
            font-weight: bold;
        }
        input[type="number"] {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            box-sizing: border-box;
            border-radius: 4px;
            border: 1px solid #ccc;
        }
        button {
            margin-top: 20px;
            width: 100%;
            padding: 10px;
            background-color: #007bff;
            border: none;
            color: white;
            font-size: 16px;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        #result {
            margin-top: 20px;
            font-size: 18px;
            font-weight: bold;
            text-align: center;
        }
    </style>
</head>
<body>

\

    <h1>BMI Calculator</h1>
    <label for="weight">Weight (kg):</label>
    <input type="number" id="weight" placeholder="Enter your weight in kilograms" min="1" />


    <label for="height">Height (cm):</label>
    <input type="number" id="height" placeholder="Enter your height in centimeters" min="1" />

    <button onclick="calculateBMI()">Calculate BMI</button>

    <div id="result"></div>
    

    <script>
        function calculateBMI() {
            const weight = parseFloat(document.getElementById('weight').value);
            const heightCm = parseFloat(document.getElementById('height').value);

            if (!weight || !heightCm || weight <= 0 || heightCm <= 0) {
                document.getElementById('result').textContent = 'Please enter valid positive numbers for weight and height.';
                return;
            }

            const heightM = heightCm / 100;
            const bmi = weight / (heightM * heightM);
            const roundedBMI = bmi.toFixed(2);

            let category = '';
            if (bmi < 18.5) {
                category = 'Underweight';
            } else if (bmi < 24.9) {
                category = 'Normal weight';
            } else if (bmi < 29.9) {
                category = 'Overweight';
            } else {
                category = 'Obese';
            }

            document.getElementById('result').textContent = `Your BMI is ${roundedBMI} (${category}).`;
        }
        
    </script>
</body>
</html>
