<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Champions League Bracket - 8 Teams</title>
    <style>
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background: linear-gradient(135deg, #0a1f3d, #1e3a8a);
            color: white;
            margin: 0;
            padding: 20px;
            min-height: 100vh;
        }
        .header {
            text-align: center;
            margin-bottom: 30px;
        }
        .header h1 {
            color: #ffd700;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
        }
        .bracket-container {
            max-width: 1100px;
            margin: 0 auto;
            background: rgba(0, 0, 0, 0.4);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.6);
        }
        .round {
            display: flex;
            justify-content: space-between;
            margin-bottom: 60px;
        }
        .round-title {
            text-align: center;
            color: #ffd700;
            margin-bottom: 20px;
            font-size: 1.3em;
        }
        .match {
            background: rgba(255,255,255,0.1);
            border: 2px solid #3b82f6;
            border-radius: 8px;
            padding: 12px;
            width: 220px;
            margin: 15px 0;
            position: relative;
        }
        .team {
            padding: 10px;
            margin: 5px 0;
            background: rgba(255,255,255,0.15);
            border-radius: 6px;
            display: flex;
            align-items: center;
        }
        .team input {
            background: transparent;
            border: none;
            color: white;
            font-size: 1.1em;
            flex: 1;
            outline: none;
        }
        .team input[readonly] {
            cursor: default;
        }
        .score {
            width: 40px;
            text-align: center;
            font-weight: bold;
            background: rgba(0,0,0,0.3);
            border-radius: 4px;
            margin-left: 8px;
        }
        .connector {
            position: absolute;
            height: 2px;
            background: #60a5fa;
            top: 50%;
        }
        .final {
            margin: 40px auto;
            width: 300px;
        }
        .winner {
            text-align: center;
            font-size: 1.5em;
            color: #ffd700;
            margin-top: 20px;
        }
        .controls {
            text-align: center;
            margin: 20px 0;
        }
        button {
            background: #3b82f6;
            color: white;
            border: none;
            padding: 12px 24px;
            margin: 0 10px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
        }
        button:hover {
            background: #2563eb;
        }
        .view-mode .team input {
            background: rgba(255,255,255,0.2);
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>🏆 UEFA Champions League</h1>
        <p id="mode-title">8-Team Knockout Bracket</p>
    </div>

    <div class="bracket-container" id="bracket">
        <!-- Quarterfinals -->
        <div>
            <div class="round-title">Quarterfinals</div>
            <div class="round">
                <!-- Match 1 -->
                <div class="match">
                    <div class="team"><input type="text" class="team-name" placeholder="Team 1" value=""></div>
                    <div class="team"><input type="text" class="team-name" placeholder="Team 2" value=""></div>
                    <input type="number" class="score" placeholder="0" min="0">
                    <input type="number" class="score" placeholder="0" min="0">
                </div>
                <!-- Match 2 -->
                <div class="match">
                    <div class="team"><input type="text" class="team-name" placeholder="Team 3" value=""></div>
                    <div class="team"><input type="text" class="team-name" placeholder="Team 4" value=""></div>
                    <input type="number" class="score" placeholder="0" min="0">
                    <input type="number" class="score" placeholder="0" min="0">
                </div>
                <!-- Match 3 -->
                <div class="match">
                    <div class="team"><input type="text" class="team-name" placeholder="Team 5" value=""></div>
                    <div class="team"><input type="text" class="team-name" placeholder="Team 6" value=""></div>
                    <input type="number" class="score" placeholder="0" min="0">
                    <input type="number" class="score" placeholder="0" min="0">
                </div>
                <!-- Match 4 -->
                <div class="match">
                    <div class="team"><input type="text" class="team-name" placeholder="Team 7" value=""></div>
                    <div class="team"><input type="text" class="team-name" placeholder="Team 8" value=""></div>
                    <input type="number" class="score" placeholder="0" min="0">
                    <input type="number" class="score" placeholder="0" min="0">
                </div>
            </div>
        </div>

        <!-- Semifinals -->
        <div>
            <div class="round-title">Semifinals</div>
            <div class="round">
                <div class="match">
                    <div class="team"><input type="text" class="team-name sf1" placeholder="Winner QF1" readonly></div>
                    <div class="team"><input type="text" class="team-name sf2" placeholder="Winner QF2" readonly></div>
                    <input type="number" class="score" placeholder="0" min="0">
                    <input type="number" class="score" placeholder="0" min="0">
                </div>
                <div class="match">
                    <div class="team"><input type="text" class="team-name sf3" placeholder="Winner QF3" readonly></div>
                    <div class="team"><input type="text" class="team-name sf4" placeholder="Winner QF4" readonly></div>
                    <input type="number" class="score" placeholder="0" min="0">
                    <input type="number" class="score" placeholder="0" min="0">
                </div>
            </div>
        </div>

        <!-- Final -->
        <div class="final">
            <div class="round-title">FINAL</div>
            <div class="match" style="margin: 0 auto; width: 280px;">
                <div class="team"><input type="text" class="team-name final1" placeholder="Winner SF1" readonly></div>
                <div class="team"><input type="text" class="team-name final2" placeholder="Winner SF2" readonly></div>
                <input type="number" class="score" placeholder="0" min="0">
                <input type="number" class="score" placeholder="0" min="0">
            </div>
            <div class="winner">
                Champion: <span id="champion" style="color:#ffd700; font-weight:bold;"></span>
            </div>
        </div>
    </div>

    <div class="controls">
        <button onclick="toggleMode()">Switch to View Mode</button>
        <button onclick="saveBracket()">Save to Local Storage</button>
        <button onclick="loadBracket()">Load Saved Bracket</button>
        <button onclick="resetBracket()">Reset All</button>
    </div>

    <script>
        let isEditMode = true;

        function toggleMode() {
            isEditMode = !isEditMode;
            const bracket = document.getElementById('bracket');
            if (isEditMode) {
                document.getElementById('mode-title').textContent = "8-Team Knockout Bracket (Edit Mode)";
                bracket.classList.remove('view-mode');
                document.querySelectorAll('input.team-name:not(.sf1):not(.sf2):not(.sf3):not(.sf4):not(.final1):not(.final2)').forEach(input => {
                    input.removeAttribute('readonly');
                });
            } else {
                document.getElementById('mode-title').textContent = "8-Team Knockout Bracket (View Mode)";
                bracket.classList.add('view-mode');
                document.querySelectorAll('input.team-name').forEach(input => {
                    input.setAttribute('readonly', true);
                });
            }
        }

        function saveBracket() {
            const data = {};
            document.querySelectorAll('input').forEach((input, index) => {
                data[index] = input.value;
            });
            localStorage.setItem('championsLeagueBracket', JSON.stringify(data));
            alert('Bracket saved successfully!');
        }

        function loadBracket() {
            const saved = localStorage.getItem('championsLeagueBracket');
            if (saved) {
                const data = JSON.parse(saved);
                document.querySelectorAll('input').forEach((input, index) => {
                    if (data[index] !== undefined) input.value = data[index];
                });
                alert('Bracket loaded!');
            } else {
                alert('No saved bracket found.');
            }
        }

        function resetBracket() {
            if (confirm('Reset all fields?')) {
                document.querySelectorAll('input').forEach(input => {
                    input.value = '';
                });
            }
        }

        // Auto-update semifinals and final placeholders (basic simulation)
        function updateProgression() {
            // This is a simple demo - in a full version you could add logic to propagate winners
            console.log("Bracket updated");
        }

        // Add event listeners for auto-update
        document.addEventListener('input', () => {
            updateProgression();
        });

        // Initialize
        window.onload = () => {
            document.getElementById('mode-title').textContent = "8-Team Knockout Bracket (Edit Mode)";
        };
    </script>
</body>
</html>
