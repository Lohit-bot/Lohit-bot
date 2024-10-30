<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tourist Helper App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Tourist Helper App</h1>
        <input type="text" id="search" placeholder="Enter place name..." />
        <button onclick="searchPlace()">Search</button>
        <div id="results"></div>
    </div>
    <script src="script.js"></script>
</body>
</html>


body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 600px;
    margin: auto;
    background: white;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
}

input {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
}

button {
    width: 100%;
    padding: 10px;
    background-color: #5cb85c;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #4cae4c;
}

#results {
    margin-top: 20px;
}

const places = [
    { name: "Eiffel Tower", price: "€25", description: "Iconic landmark in Paris." },
    { name: "Statue of Liberty", price: "$20", description: "Symbol of freedom in New York." },
    { name: "Great Wall of China", price: "¥60", description: "Ancient wall stretching across northern China." },
    { name: "Machu Picchu", price: "$50", description: "Incan city set in the Andes mountains of Peru." },
];

function searchPlace() {
    const query = document.getElementById("search").value.toLowerCase();
    const results = places.filter(place => place.name.toLowerCase().includes(query));
    
    displayResults(results);
}

function displayResults(results) {
    const resultsDiv = document.getElementById("results");
    resultsDiv.innerHTML = ""; // Clear previous results

    if (results.length === 0) {
        resultsDiv.innerHTML = "<p>No results found.</p>";
        return;
    }

    results.forEach(place => {
        const placeDiv = document.createElement("div");
        placeDiv.className = "place";
        placeDiv.innerHTML = `<h2>${place.name}</h2><p>${place.description}</p><p>Price: ${place.price}</p>`;
        resultsDiv.appendChild(placeDiv);
    });
}


