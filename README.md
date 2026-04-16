
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quick Questionnaire</title>
    <style>
        body { font-family: sans-serif; display: flex; justify-content: center; padding: 20px; background-color: #f4f4f9; }
        .card { background: white; padding: 2rem; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); width: 100%; max-width: 400px; }
        h2 { color: #333; margin-top: 0; }
        .field { margin-bottom: 1.5rem; }
        label { display: block; margin-bottom: 0.5rem; font-weight: bold; }
        input, select { width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 6px; box-sizing: border-box; }
        button { width: 100%; padding: 12px; background-color: #4CAF50; color: white; border: none; border-radius: 6px; cursor: pointer; font-size: 1rem; }
        button:hover { background-color: #45a049; }
        #results { margin-top: 20px; padding: 15px; background: #e8f5e9; border-radius: 6px; display: none; }
    </style>
</head>
<body>

<div class="card">
    <h2>Questionnaire</h2>
    
    <div class="field">
        <label for="age">What is your age?</label>
        <input type="number" id="age" placeholder="Enter age">
    </div>

    <div class="field">
        <label for="sex">What is your sex?</label>
        <select id="sex">
            <option value="">Select...</option>
            <option value="Male">Male</option>
            <option value="Female">Female</option>
            <option value="Other">Other</option>
            <option value="Prefer not to say">Prefer not to say</option>
        </select>
    </div>

    <button onclick="showResults()">Submit & View Results</button>

    <div id="results">
        <strong>Your Responses:</strong>
        <p id="displayAge"></p>
        <p id="displaySex"></p>
        <button onclick="copyResults()" style="background-color: #2196F3;">Copy Results to Share</button>
    </div>
</div>

<script>
    function showResults() {
        const age = document.getElementById('age').value;
        const sex = document.getElementById('sex').value;

        if(!age || !sex) {
            alert("Please fill out both fields!");
            return;
        }

        document.getElementById('displayAge').innerText = "Age: " + age;
        document.getElementById('displaySex').innerText = "Sex: " + sex;
        document.getElementById('results').style.display = 'block';
    }

    function copyResults() {
        const age = document.getElementById('age').value;
        const sex = document.getElementById('sex').value;
        const text = "Questionnaire Results - Age: " + age + ", Sex: " + sex;
        
        navigator.clipboard.writeText(text).then(() => {
            alert("Results copied to clipboard! You can now paste them in a message.");
        });
    }
</script>

</body>
</html>
