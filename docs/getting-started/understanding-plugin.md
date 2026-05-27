<!DOCTYPE html>
<html lang="mg">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Andrana Lalao Domino</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #2c3e50;
            color: white;
            text-align: center;
            padding: 20px;
        }
        #table {
            background-color: #27ae60;
            border: 5px solid #1e824c;
            border-radius: 10px;
            min-height: 120px;
            margin: 20px auto;
            max-width: 500px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            padding: 10px;
        }
        .domino {
            background-color: white;
            color: black;
            border: 2px solid #333;
            border-radius: 5px;
            padding: 10px 15px;
            font-weight: bold;
            font-size: 20px;
            cursor: pointer;
            display: inline-block;
        }
        #hand {
            margin-top: 30px;
        }
        #status {
            font-size: 18px;
            color: #f1c40f;
            margin-top: 15px;
        }
    </style>
</head>
<body>

    <h1>Dika Tsotra: Fitsipika Domino</h1>
    <p>Kitiho ny domino eny an-tananao mba hametrahana azy eo amin'ny latabatra maitso.</p>

    <h3>Ny Latabatra (Table):</h3>
    <div id="table">
        <div class="domino" id="domino-fixe">3 | 4</div>
    </div>

    <h3>Ny Tananao (Hand):</h3>
    <div id="hand">
        <div class="domino" onclick="milalao(4, 5, this)">4 | 5</div>
        <div class="domino" onclick="milalao(1, 2, this)">1 | 2</div>
        <div class="domino" onclick="milalao(3, 6, this)">3 | 6</div>
    </div>

    <div id="status">Andrasana ny fihetsikao...</div>

    <script>
        // Ny laharan'ny domino eo amin'ny latabatra amin'izao (3 sy 4)
        // Ny sisiny havia dia 3, ny sisiny havanana dia 4
        let sisinyHavia = 3;
        let sisinyHavanana = 4;

        function milalao(laharanaA, laharanaB, fitaovana) {
            let statusDiv = document.getElementById('status');
            let tableDiv = document.getElementById('table');

            // Fanamarinana: Mifanaraka amin'ny sisiny havanana ve ilay domino kilihina?
            if (laharanaA === sisinyHavanana) {
                // Manova ny laharan'ny sisiny havanana vaovao
                sisinyHavanana = laharanaB;
                
                // Mamorona domino vaovao eo amin'ny latabatra
                let dominoVaovao = document.createElement('div');
                dominoVaovao.className = 'domino';
                dominoVaovao.innerText = laharanaA + " | " + laharanaB;
                tableDiv.appendChild(dominoVaovao);

                // Fafana eny an-tanana ilay domino efa nilalaovana
                fitaovana.style.display = 'none';
                statusDiv.innerText = "Mety tsara! Nifindra ho " + sisinyHavanana + " ny sisiny havanana.";
                statusDiv.style.color = "#2ecc71";
            } 
            // Fanamarinana faharoa: Raha mivadika ilay domino (ohatra: 3 sy 6 mifanaraka amin'ny sisiny havia)
            else if (laharanaA === sisinyHavia) {
                sisinyHavia = laharanaB;
                
                let dominoVaovao = document.createElement('div');
                dominoVaovao.className = 'domino';
                dominoVaovao.innerText = laharanaB + " | " + laharanaA;
                // Apetraka eo aloha (havia)
                tableDiv.insertBefore(dominoVaovao, tableDiv.firstChild);

                fitaovana.style.display = 'none';
                statusDiv.innerText = "Mety tsara! Nifindra ho " + sisinyHavia + " ny sisiny havia.";
                statusDiv.style.color = "#2ecc71";
            }
            else {
                // Raha tsy mifanaraka ny laharana
                statusDiv.innerText = "Tsy mety io! Tsy mifanaraka ny laharana (" + laharanaA + "|" + laharanaB + ") amin'ny eo amin'ny latabatra.";
                statusDiv.style.color = "#e74c3c";
            }
        }
    </script>
</body>
</html>
