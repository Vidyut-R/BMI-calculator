# BMI-calculator
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BMI Calculator</title>
<style>
.card {          width: 400px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    margin: 20px auto;}
label {display: block;
    margin-bottom: 5px;}
input[type="number"] {width: 100%;
    padding: 8px;
    margin-bottom: 15px;
    border: 1px solid #ddd;
    border-radius: 4px;
    box-sizing: border-box;}
button {background-color: #007bff;
    color: white;
    padding: 10px 15px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;}
button:hover {background-color: #0056b3;}
#result {margin-top: 20px;
    font-weight: bold;}
.result-category {margin-top: 10px;
    font-style: italic;}
.underweight {color: orange;}
.normal {color: green;}
.overweight {color: red;}
.obese {color: red;}
</style>
</head>
<body>
<div class="card">
    <h2>BMI Calculator</h2>
    <label for="weight">Weight (kg):</label>
    <input type="number" id="weight" placeholder="Enter weight">
    <label for="height">Height (cm):</label>
    <input type="number" id="height" placeholder="Enter height">
    <button onclick="calculateBMI()">Calculate BMI</button>
    <div id="result"></div>
</div>
<script>
function calculateBMI() {
    let weight = parseFloat(document.getElementById("weight").value);
    let height = parseFloat(document.getElementById("height").value);
    if (isNaN(weight) || isNaN(height) || weight <= 0 || height <= 0) {
        document.getElementById("result").innerHTML = "Please enter valid values.";
        return;}
    let heightInMeters = height / 100;
    let bmi = weight / (heightInMeters * heightInMeters);
    let bmiRounded = bmi.toFixed(2);
    let category = "";
    if (bmi < 18.5) {category = "Underweight";} 
    else if (bmi >= 18.5 && bmi <= 24.9) {category = "Normal";} 
    else if (bmi >= 25 && bmi <= 29.9) {category = "Overweight";}
    else {category = "Obese"}
    let resultDiv = document.getElementById("result");
    resultDiv.innerHTML = ""; // Clear previous results
    let bmiDisplay = document.createElement("p");
    bmiDisplay.textContent = "BMI: " + bmiRounded;
    resultDiv.appendChild(bmiDisplay);
    let categoryDisplay = document.createElement("p");
    categoryDisplay.classList.add("result-category");
    categoryDisplay.classList.add(category.toLowerCase());
    categoryDisplay.textContent = "Category: " + category;
    resultDiv.appendChild(categoryDisplay);}
</script>
</body>
</html>
