<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Furniture Word Game</title>
    <style>
        body { font-family: 'Arial', sans-serif; background-color: #f0f9ff; display: flex; flex-direction: column; align-items: center; padding: 20px; }
        h1 { color: #2c3e50; }
        .game-container { display: flex; gap: 40px; margin-top: 20px; max-width: 900px; }
        
        /* Containers for words and images */
        .column { display: flex; flex-direction: column; gap: 15px; }
        
        .item { 
            padding: 15px 25px; background: white; border: 2px solid #3498db; 
            border-radius: 8px; cursor: pointer; text-align: center;
            transition: all 0.2s; user-select: none; font-weight: bold;
        }
        
        .img-slot {
            width: 100px; height: 100px; background: #ecf0f1;
            border: 2px dashed #bdc3c7; border-radius: 8px;
            display: flex; align-items: center; justify-content: center;
            font-size: 40px; position: relative;
        }

        .selected { background: #3498db; color: white; transform: scale(1.05); }
        .matched { background: #2ecc71 !important; border-color: #27ae60 !important; color: white; cursor: default; }
        .wrong { background: #e74c3c !important; border-color: #c0392b !important; color: white; }

        #score-board { margin-bottom: 20px; font-size: 1.2rem; }
        button { margin-top: 20px; padding: 10px 20px; cursor: pointer; background: #3498db; color: white; border: none; border-radius: 5px; }
    </style>
</head>
<body>

    <h1>Furniture Matching Game</h1>
    <div id="score-board">Items Remaining: <span id="count">12</span></div>

    <div class="game-container">
        <div class="column" id="words-container"></div>
        
        <div class="column" id="images-container"></div>
    </div>

    <button onclick="location.reload()">Reset Game</button>

    <script>
        const furnitureData = [
            { name: 'Bed', icon: '🛏️' },
            { name: 'Sofa', icon: '🛋️' },
            { name: 'Wardrobe', icon: '👗' },
            { name: 'Chair', icon: '🪑' },
            { name: 'Bath', icon: '🛀' },
            { name: 'Shower', icon: '🚿' },
            { name: 'Armchair', icon: '💺' },
            { name: 'Oven', icon: '🍳' },
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(3, 180px);
            gap: 20px;
            justify-content: center;
        }

        .card {
            background: white;
            border: 2px solid #ccc;
            padding: 10px;
            border-radius: 10px;
        }

        .card img {
            width: 120px;
            height: 120px;
            object-fit: contain;
        }

        .drop-area {
            margin-top: 10px;
            border: 2px dashed #999;
            padding: 10px;
            min-height: 40px;
            border-radius: 8px;
        }

        .correct {
            background: lightgreen;
        }

        .wrong {
            background: #ffb3b3;
        }
    </style>
</head>

<body>

    <h2>Furniture Matching Exercise</h2>
    <p>Click a word and match it to the correct picture.</p>

    <div class="word-container">
        <span class="word" data-word="bed">Bed</span>
        <span class="word" data-word="chair">Chair</span>
        <span class="word" data-word="table">Table</span>
        <span class="word" data-word="sofa">Sofa</span>
        <span class="word" data-word="bath">Bath</span>
        <span class="word" data-word="cupboard">Cupboard</span>
    </div>

    <div class="grid">

        <div class="card">
            <img src="https://cdn-icons-png.flaticon.com/512/3050/3050525.png">
            <div class="drop-area" data-answer="bed"></div>
        </div>

        <div class="card">
            <img src="https://cdn-icons-png.flaticon.com/512/892/892458.png">
            <div class="drop-area" data-answer="chair"></div>
        </div>

        <div class="card">
            <img src="https://cdn-icons-png.flaticon.com/512/2421/2421989.png">
            <div class="drop-area" data-answer="cupboard"></div>
        </div>

        <div class="card">
            <img src="https://cdn-icons-png.flaticon.com/512/2933/2933885.png">
            <div class="drop-area" data-answer="bath"></div>
        </div>

        <div class="card">
            <img src="https://cdn-icons-png.flaticon.com/512/3082/3082037.png">
            <div class="drop-area" data-answer="sofa"></div>
        </div>

        <div class="card">
            <img src="https://cdn-icons-png.flaticon.com/512/1533/1533768.png">
            <div class="drop-area" data-answer="table"></div>
        </div>

    </div>

    <script>
        let selectedWord = "";

        const words = document.querySelectorAll(".word");

        words.forEach(word => {
            word.addEventListener("click", () => {

                document.querySelectorAll(".word")
                    .forEach(w => w.classList.remove("selected"));

                word.classList.add("selected");
                selectedWord = word.dataset.word;
            });
        });

        const areas = document.querySelectorAll(".drop-area");

        areas.forEach(area => {
            area.addEventListener("click", () => {

                if (!selectedWord) {
                    alert("Select a word first!");
                    return;
                }

                area.innerHTML = selectedWord;if (selectedWord === area.dataset.answer) {
                    area.classList.add("correct");
                    area.classList.remove("wrong");
                } else {
                    area.classList.add("wrong");
                    area.classList.remove("correct");
                }

                document.querySelectorAll(".word")
                    .forEach(w => w.classList.remove("selected"));

                selectedWord = "";
            });
        });
    </script>

</body>
</html>
