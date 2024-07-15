# virtual-customizable-dummy-code
A repository for virtual customizable dummy code 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Personalize Your Body Shape</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        /* Additional CSS styles for this page */
        body {
            font-family: Arial, sans-serif;
            background-color: #f7f7f7;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            max-width: 500px;
            margin: 0 auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        h1 {
            color: #333;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .height-input {
            display: flex;
            gap: 10px;
        }

        .height-input input {
            width: 50%;
        }

        .options {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .options input {
            display: none;
        }

        .options label {
            display: block;
            padding: 10px 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
            cursor: pointer;
        }

        .options input:checked + label {
            background-color: #ff69b4;
            color: #fff;
            border-color: #ff69b4;
        }

        button {
            display: block;
            width: 100%;
            padding: 15px;
            background-color: #ff69b4;
            color: #fff;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            margin-top: 20px;
        }

        /* Responsive styles */
        @media (max-width: 768px) {
            .height-input {
                flex-direction: column;
            }

            .height-input input {
                width: 100%;
            }
        }
    </style>
</head>
<body background="photo 2.jpg">
    <div class="container">
        <h1>Personalize your body shape</h1>
        <p>Enter your body measurements:</p>

        <form id="bodyShapeForm">
            <div class="form-group">
                <label for="height">Height</label>
                <div class="height-input">
                    <input type="number" id="height-ft" name="height-ft" min="0" max="8" placeholder="ft" required>
                    <input type="number" id="height-in" name="height-in" min="0" max="11" placeholder="in" required>
                </div>
            </div>

            <div class="form-group">
                <label for="weight">Weight (kg)</label>
                <input type="number" id="weight" name="weight" min="0" placeholder="kg" required>
            </div>

            <div class="form-group">
                <label>Band Size</label>
                <div class="options">
                    <input type="radio" id="band-28" name="band" value="28" required>
                    <label for="band-28">28</label>

                    <input type="radio" id="band-30" name="band" value="30">
                    <label for="band-30">30</label>

                    <input type="radio" id="band-32" name="band" value="32">
                    <label for="band-32">32</label>

                    <input type="radio" id="band-34" name="band" value="34">
                    <label for="band-34">34</label>

                    <input type="radio" id="band-36" name="band" value="36">
                    <label for="band-36">36</label>

                    <input type="radio" id="band-38" name="band" value="38">
                    <label for="band-38">38</label>
                </div>
            </div>

            <div class="form-group">
                <label>Cup Size</label>
                <div class="options">
                    <input type="radio" id="cup-AA" name="cup" value="AA" required>
                    <label for="cup-AA">AA</label>

                    <input type="radio" id="cup-A" name="cup" value="A">
                    <label for="cup-A">A</label>

                    <input type="radio" id="cup-B" name="cup" value="B">
                    <label for="cup-B">B</label>

                    <input type="radio" id="cup-C" name="cup" value="C">
                    <label for="cup-C">C</label>

                    <input type="radio" id="cup-D" name="cup" value="D">
                    <label for="cup-D">D</label>

                    <input type="radio" id="cup-DD" name="cup" value="DD">
                    <label for="cup-DD">DD</label>
                </div>
            </div>

            <div class="form-group">
                <label>Choose body shape</label>
                <div class="options">
                    <input type="radio" id="rectangle" name="body-shape" value="Rectangle" checked required>
                    <label for="rectangle">
                        <img src="pearbody type.png" alt="pear" height="200px">
                    </label>

                    <input type="radio" id="apple" name="body-shape" value="Apple">
                    <label for="apple">
                        <img src="apple.png" alt="Apple" height="200px">
                    </label>
                </div>
            </div>

            <button type="button" onclick="submitForm()">Done</button>
        </form>

        <!-- Ready Player Me iframe -->
        <iframe src="about:blank" style="width:100%; height:600px; display:none;" id="rpm-iframe"></iframe>
    </div>

    <script>
        function submitForm() {
            const heightFt = document.getElementById('height-ft').value;
            const heightIn = document.getElementById('height-in').value;
            const weight = document.getElementById('weight').value;
            const bandSize = document.querySelector('input[name="band"]:checked').value;
            const cupSize = document.querySelector('input[name="cup"]:checked').value;
            const bodyShape = document.querySelector('input[name="body-shape"]:checked').value;

            // Store form data in sessionStorage (can also use localStorage)
            const formData = {
                height: ${heightFt} ft ${heightIn} in,
                weight: ${weight} kg,
                bandSize,
                cupSize,
                bodyShape
            };
            sessionStorage.setItem('formData', JSON.stringify(formData));

            // Check if all necessary inputs are filled
            if (heightFt && heightIn && weight && bandSize && cupSize && bodyShape) {
                // Display Ready Player Me iframe
                document.getElementById('rpm-iframe').style.display = 'block';
                document.getElementById('rpm-iframe').src = 'https://readyplayer.me/avatar';

                // Optionally, hide the form after displaying the iframe
                document.getElementById('bodyShapeForm').style.display = 'none';
            } else {
                alert('Please fill out all body size inputs.');
            }
        }
    </script>
</body>
</html>
