# Spark-Focus-
A productivity application design to help user's focus <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Spark Focus Timer</title>
    <style>
        body { background-color: #121212; color: white; font-family: sans-serif; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100vh; margin: 0; }
        .timer { font-size: 5rem; font-weight: bold; margin-bottom: 20px; color: #00d4ff; }
        .controls button { padding: 15px 30px; font-size: 1rem; cursor: pointer; border: none; border-radius: 5px; margin: 5px; transition: 0.3s; }
        .start { background-color: #28a745; color: white; }
        .reset { background-color: #dc3545; color: white; }
        h1 { color: #ffcc00; }
    </style>
</head>
<body>

    <h1>Origin Spark Labs</h1>
    <div class="timer" id="display">25:00</div>

    <div class="controls">
        <button class="start" onclick="toggleTimer()" id="startBtn">Start Focus</button>
        <button class="reset" onclick="resetTimer()">Reset</button>
    </div>

    <script>
        let timeLeft = 25 * 60;
        let timerId = null;

        function updateDisplay() {
            const mins = Math.floor(timeLeft / 60);
            const secs = timeLeft % 60;
            document.getElementById('display').textContent = 
                `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
        }

        function toggleTimer() {
            if (timerId) {
                clearInterval(timerId);
                timerId = null;
                document.getElementById('startBtn').textContent = 'Resume';
            } else {
                document.getElementById('startBtn').textContent = 'Pause';
                timerId = setInterval(() => {
                    if (timeLeft > 0) {
                        timeLeft--;
                        updateDisplay();
                    } else {
                        clearInterval(timerId);
                        alert("Time is up! Take a break.");
                    }
                }, 1000);
            }
        }

        function resetTimer() {
            clearInterval(timerId);
            timerId = null;
            timeLeft = 25 * 60;
            updateDisplay();
            document.getElementById('startBtn').textContent = 'Start Focus';
        }
    </script>
</body>
</html>

