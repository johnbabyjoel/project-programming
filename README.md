<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jersey Store</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .container {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 20px;
            padding: 20px;
        }
        .jersey {
            border: 1px solid #ddd;
            padding: 10px;
            border-radius: 10px;
        }
        .jersey img {
            width: 100px;
            height: 100px;
        }
        .size-chart {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            padding: 20px;
            border: 1px solid #000;
        }
    </style>
</head>
<body>
    <h1>Football Jersey Store</h1>
    <div class="container">
        <script>
            const jerseys = [
                {team: "Real Madrid", img: "real_madrid.jpg"},
                {team: "Barcelona", img: "barcelona.jpg"},
                {team: "Manchester United", img: "man_united.jpg"},
                {team: "Liverpool", img: "liverpool.jpg"},
                {team: "Bayern Munich", img: "bayern.jpg"},
                {team: "Brazil", img: "brazil.jpg"},
                {team: "Argentina", img: "argentina.jpg"},
                {team: "France", img: "france.jpg"},
                {team: "Portugal", img: "portugal.jpg"},
                {team: "Italy", img: "italy.jpg"}
            ];
            
            jerseys.forEach(jersey => {
                document.write(`
                    <div class='jersey'>
                        <img src='${jersey.img}' alt='${jersey.team} Jersey'>
                        <h3>${jersey.team}</h3>
                        <button onclick="showSizeChart('${jersey.team}')">Buy Now</button>
                    </div>
                `);
            });
        </script>
    </div>
    
    <div id="sizeChart" class="size-chart">
        <h2>Select Size</h2>
        <p id="selectedJersey"></p>
        <button onclick="goToAddressPage('M')">M</button>
        <button onclick="goToAddressPage('S')">S</button>
        <button onclick="goToAddressPage('L')">L</button>
        <button onclick="goToAddressPage('XL')">XL</button>
        <br><br>
        <button onclick="closeSizeChart()">Close</button>
    </div>
    
    <script>
        function showSizeChart(team) {
            document.getElementById("selectedJersey").innerText = "Jersey: " + team;
            document.getElementById("sizeChart").style.display = "block";
        }
        function closeSizeChart() {
            document.getElementById("sizeChart").style.display = "none";
        }
        function goToAddressPage(size) {
            const team = document.getElementById("selectedJersey").innerText.replace("Jersey: ", "");
            window.location.href = `delivery.html?team=${encodeURIComponent(team)}&size=${encodeURIComponent(size)}`;
        }
    </script>
</body>
</html>
