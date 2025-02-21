 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fun Facts</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        h1 {
            margin-bottom: 20px;
        }
        #fact {
            margin: 20px;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background-color: #fff;
            transition: opacity 0.5s ease;
            opacity: 0;
        }
        #fact.show {
            opacity: 1;
        }
        button {
            padding: 10px 20px;
            margin: 5px;
            border: none;
            border-radius: 5px;
            background-color: #007BFF;
            color: white;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>

    <h1>Fun Facts</h1>
    <button id="factButton">Show Random Fact</button>
    <div id="fact"></div>
    <button id="shareButton" style="display:none;">Share on Twitter</button>

    <script>
        const facts = [
            "Bananas are berries, but strawberries aren't.",
            "Honey never spoils.",
            "A group of flamingos is called a 'flamboyance'.",
            "Octopuses have three hearts.",
            "Wombat poop is cube-shaped.",
            "A day on Venus is longer than a year on Venus."
        ];

        const factButton = document.getElementById('factButton');
        const factDisplay = document.getElementById('fact');
        const shareButton = document.getElementById('shareButton');

        factButton.addEventListener('click', () => {
            const randomIndex = Math.floor(Math.random() * facts.length);
            const randomFact = facts[randomIndex];

            factDisplay.textContent = randomFact;
            factDisplay.classList.add('show');

            // Show the share button
            shareButton.style.display = 'inline-block';
            shareButton.setAttribute('data-text', randomFact);
        });

        shareButton.addEventListener('click', () => {
            const factToShare = shareButton.getAttribute('data-text');
            const twitterUrl = `https://twitter.com/intent/tweet?text=${encodeURIComponent(factToShare)}`;
            window.open(twitterUrl, '_blank');
        });
    </script>

</body>
</html>
