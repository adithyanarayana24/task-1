# task-1
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Temperature Converter</title>
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(to right, #ff758c, #ff7eb3);
            color: #333;
        }

        .converter {
            text-align: center;
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background-color: #ffffff;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
            animation: fadeIn 0.5s ease-in-out;
        }

        h2 {
            font-size: 1.8rem;
            color: #ff7eb3;
            margin-bottom: 20px;
        }

        label {
            font-size: 1rem;
            font-weight: bold;
            color: #555;
        }

        select, input {
            width: 100%;
            padding: 12px;
            margin: 8px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
            outline: none;
            font-size: 1rem;
            background-color: #f9f9f9;
            transition: background-color 0.3s ease;
        }

        select:hover, input:hover {
            background-color: #f1f1f1;
        }

        button {
            background-color: #ff758c;
            color: white;
            padding: 12px;
            border: none;
            width: 100%;
            cursor: pointer;
            border-radius: 5px;
            font-size: 1rem;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #ff5f73;
        }

        #result {
            width: 100%;
            padding: 12px;
            margin-top: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            outline: none;
            font-weight: bold;
            font-size: 1.1rem;
            color: #333;
            background-color: #f9f9f9;
        }

        @media screen and (max-width: 500px) {
            .converter {
                width: 90%;
            }
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }
    </style>
</head>

<body>
    <div class="converter">
        <h2>Temperature Converter</h2>
        <label for="fromUnit">From:</label>
        <select id="fromUnit">
            <option value="C">Celsius</option>
            <option value="F">Fahrenheit</option>
            <option value="K">Kelvin</option>
            <option value="R">Rankine</option>
        </select>
        <label for="toUnit">To:</label>
        <select id="toUnit">
            <option value="C">Celsius</option>
            <option value="F">Fahrenheit</option>
            <option value="K">Kelvin</option>
            <option value="R">Rankine</option>
        </select>
        <label for="temperature">Temperature</label>
        <input type="number" id="temperature" placeholder="Enter Temperature">
        <button onclick="convert()">Convert</button>

        <label for="result">Result:</label>
        <input type="text" id="result" readonly>
    </div>
    <script>
        function convert() {
            var fromUnit = document.getElementById('fromUnit').value;
            var toUnit = document.getElementById('toUnit').value;
            var temperature = parseFloat(document.getElementById('temperature').value);

            var convertedValue;
            var resultUnit;

            switch (fromUnit) {
                case 'C':
                    if (toUnit === 'F') {
                        convertedValue = (temperature * 9 / 5) + 32;
                        resultUnit = 'F';
                    } else if (toUnit === 'K') {
                        convertedValue = temperature + 273.15;
                        resultUnit = 'K';
                    } else if (toUnit === 'R') {
                        convertedValue = (temperature + 273.15) * 9 / 5;
                        resultUnit = 'R';
                    } else {
                        convertedValue = temperature;
                        resultUnit = 'C';
                    }
                    break;
                case 'F':
                    if (toUnit === 'C') {
                        convertedValue = (temperature - 32) * 5 / 9;
                        resultUnit = 'C';
                    } else if (toUnit === 'K') {
                        convertedValue = (temperature - 32) * 5 / 9 + 273.15;
                        resultUnit = 'K';
                    } else if (toUnit === 'R') {
                        convertedValue = temperature + 459.67;
                        resultUnit = 'R';
                    } else {
                        convertedValue = temperature;
                        resultUnit = 'F';
                    }
                    break;
                case 'K':
                    if (toUnit === 'C') {
                        convertedValue = temperature - 273.15;
                        resultUnit = 'C';
                    } else if (toUnit === 'F') {
                        convertedValue = (temperature - 273.15) * 9 / 5 + 32;
                        resultUnit = 'F';
                    } else if (toUnit === 'R') {
                        convertedValue = temperature * 9 / 5;
                        resultUnit = 'R';
                    } else {
                        convertedValue = temperature;
                        resultUnit = 'K';
                    }
                    break;
                case 'R':
                    if (toUnit === 'C') {
                        convertedValue = (temperature - 491.67) * 5 / 9;
                        resultUnit = 'C';
                    } else if (toUnit === 'K') {
                        convertedValue = temperature * 5 / 9;
                        resultUnit = 'K';
                    } else if (toUnit === 'F') {
                        convertedValue = temperature - 459.67;
                        resultUnit = 'F';
                    } else {
                        convertedValue = temperature;
                        resultUnit = 'R';
                    }
                    break;
            }

            document.getElementById('result').value = convertedValue.toFixed(2) + ' ' + resultUnit;
        }
    </script>
</body>

</html>
