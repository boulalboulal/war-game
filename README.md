<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>War Game with Weapons</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; background-color: #f4f4f4; }
        #gameContainer { width: 70%; margin: 0 auto; }
        .stage { display: none; padding: 20px; margin-top: 20px; background-color: #333; color: white; border-radius: 5px; }
        .character { margin-top: 20px; font-size: 18px; }
        #stageInfo { font-size: 22px; margin-top: 20px; }
        #attackBtn { padding: 10px 20px; background-color: #28a745; color: white; border: none; cursor: pointer; border-radius: 5px; }
        #attackBtn:hover { background-color: #218838; }
        .weaponChoice { margin-top: 20px; }
        select { padding: 5px; font-size: 16px; }
        #gameOver { display: none; margin-top: 20px; color: red; }
    </style>
</head>
<body>
    <div id="gameContainer">
        <h1>War Game with Weapons</h1>
        <div id="characterInfo" class="character">
            <p id="characterName">Character Name: Hero</p>
            <p id="characterHealth">Health: 100</p>
        </div>
        <div id="stageInfo">Stage: 1</div>

        <!-- Weapon Selection -->
        <div class="weaponChoice">
            <label for="weaponSelect">Choose Your Weapon:</label>
            <select id="weaponSelect">
                <!-- Weapons will be added here via JavaScript -->
            </select>
        </div>

        <div id="stage1" class="stage">
            <h3>Stage 1: Dark Forest</h3>
            <p>You face a group of enemies in the dark forest. Defeat 5 enemies to win.</p>
            <button id="attackBtn" onclick="attack()">Attack</button>
        </div>

        <div id="stage2" class="stage">
            <h3>Stage 2: Burnt Village</h3>
            <p>Defend the survivors in the burnt village.</p>
            <button id="attackBtn" onclick="attack()">Attack</button>
        </div>

        <div id="gameOver">
            <h2>You have been defeated!</h2>
            <button onclick="restartGame()">Restart Game</button>
        </div>
    </div>

    <script>
        // Weapon Definitions
        const weapons = [
            { name: "Knife", damage: 10 },
            { name: "Pistol", damage: 20 },
            { name: "Assault Rifle", damage: 30 },
            { name: "Shotgun", damage: 40 },
            { name: "Hand Grenade", damage: 50 },
            { name: "Light Saber", damage: 35 },
            { name: "Giant Hammer", damage: 60 },
            { name: "Bow & Arrows", damage: 25 },
            { name: "Motorcycle Attack", damage: 40 },
            { name: "Mini Tank", damage: 80 },
            { name: "Poison Arrow", damage: 15 },
            { name: "Electric Shield", damage: 0 }, // Just for defense
            { name: "Tear Gas Grenade", damage: 25 },
            { name: "Energy Blade", damage: 50 },
            { name: "Guided Missile", damage: 70 }
        ];

        // Game Variables
        let characterHealth = 100;
        let currentStage = 1;
        let enemiesDefeated = 0;
        let selectedWeapon = weapons[0]; // Default to the first weapon

        // Add weapons to the selection list
        const weaponSelect = document.getElementById("weaponSelect");
        weapons.forEach((weapon, index) => {
            const option = document.createElement("option");
            option.value = index;
            option.textContent = weapon.name;
            weaponSelect.appendChild(option);
        });

        // Update selected weapon
        weaponSelect.addEventListener("change", function() {
            selectedWeapon = weapons[this.value];
            console.log("Selected Weapon: " + selectedWeapon.name);
        });

        // Show the current stage
        function showStage() {
            const allStages = document.querySelectorAll('.stage');
            allStages.forEach(stage => stage.style.display = 'none');
            
            const currentStageDiv = document.getElementById(`stage${currentStage}`);
            if (currentStageDiv) {
                currentStageDiv.style.display = 'block';
            }

            const stageInfo = document.getElementById("stageInfo");
            stageInfo.textContent = `Stage: ${currentStage}`;
        }

        // Attack the enemies
        function attack() {
            const enemiesToDefeat = 5; // Example: number of enemies in Stage 1
            enemiesDefeated++;
            console.log(`Attacked with weapon: ${selectedWeapon.name} and dealt ${selectedWeapon.damage} damage.`);

            if (enemiesDefeated >= enemiesToDefeat) {
                if (currentStage < 2) { // Move to the next stage
                    currentStage++;
                    enemiesDefeated = 0;
                    alert("Enemies defeated, moving to the next stage!");
                } else {
                    alert("You've won all the stages!");
                    return;
                }
            }

            updateCharacterStatus();
            showStage();
        }

        // Update character's status
        function updateCharacterStatus() {
            document.getElementById("characterHealth").textContent = `Health: ${characterHealth}`;
        }

        // Restart the game
        function restartGame() {
            currentStage = 1;
            enemiesDefeated = 0;
            characterHealth = 100;
            document.getElementById("gameOver").style.display = 'none';
            showStage();
        }

        // Start the game
        showStage();
    </script>
</body>
</html>
