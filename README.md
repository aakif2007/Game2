<!DOCTYPE html>
<html>
<head>
    <title>Furniture Matching Exercise</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f5e7c8;
            text-align: center;
            padding: 20px;
        }

        h2 {
            color: #d35400;
        }

        .word-container {
            margin-bottom: 20px;
        }

        .word {
            display: inline-block;
            background: orange;
            color: white;
            padding: 10px 18px;
            margin: 5px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
        }

        .selected {
            background: green;
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
