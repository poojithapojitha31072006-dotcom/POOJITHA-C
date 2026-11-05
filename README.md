
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Movie Ticket Booking System</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    background: #101018;
    color: white;
}

header {
    background: #1c1c29;
    padding: 20px 7%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 15px;
}

header h2 {
    color: #ff4757;
}

nav a {
    color: white;
    text-decoration: none;
    margin-left: 20px;
}

nav a:hover {
    color: #ff4757;
}

.hero {
    text-align: center;
    padding: 45px 15px;
    background: linear-gradient(120deg, #351329, #17172c);
}

.hero h1 {
    font-size: 36px;
    margin-bottom: 12px;
}

.hero p {
    color: #ddd;
}

.section {
    padding: 35px 7%;
}

.section h2 {
    margin-bottom: 25px;
    color: #ff4757;
}

.movies {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
    gap: 25px;
}

.movie {
    background: #20202c;
    border-radius: 12px;
    overflow: hidden;
    text-align: center;
    padding-bottom: 18px;
    transition: 0.3s;
}

.movie:hover {
    transform: translateY(-5px);
}

.movie img {
    width: 100%;
    height: 260px;
    object-fit: cover;
}

.movie h3 {
    margin: 14px 5px 8px;
}

.movie p {
    color: #bbb;
    margin-bottom: 12px;
}

button {
    background: #ff4757;
    color: white;
    border: none;
    padding: 11px 20px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 15px;
}

button:hover {
    background: #e52d40;
}

.booking {
    background: #20202c;
    padding: 25px;
    border-radius: 12px;
    max-width: 700px;
    margin: auto;
}

.booking h2 {
    color: #ff4757;
    margin-bottom: 20px;
}

.booking label {
    display: block;
    margin: 15px 0 7px;
}

.booking select,
.booking input {
    width: 100%;
    padding: 12px;
    border-radius: 6px;
    border: none;
    background: #eee;
    color: #111;
}

.screen {
    background: white;
    color: #111;
    text-align: center;
    padding: 9px;
    margin: 25px auto;
    width: 80%;
    border-radius: 50% 50% 5px 5px;
    font-weight: bold;
    letter-spacing: 3px;
}

.seats {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    gap: 12px;
    max-width: 350px;
    margin: auto;
}

.seat {
    background: #777;
    padding: 12px 4px;
    border-radius: 6px;
    text-align: center;
    cursor: pointer;
    font-size: 13px;
}

.seat.selected {
    background: #2ecc71;
    color: black;
}

.seat.booked {
    background: #ff4757;
    cursor: not-allowed;
}

.legend {
    display: flex;
    justify-content: center;
    gap: 20px;
    margin: 20px 0;
    flex-wrap: wrap;
    font-size: 13px;
}

.legend span {
    display: flex;
    align-items: center;
    gap: 6px;
}

.dot {
    width: 13px;
    height: 13px;
    display: inline-block;
    border-radius: 3px;
}

.summary {
    margin: 22px 0;
    line-height: 2;
}

#confirmation {
    display: none;
    background: #174d35;
    padding: 20px;
    margin-top: 20px;
    border-radius: 8px;
    line-height: 1.8;
}

footer {
    background: #1c1c29;
    text-align: center;
    padding: 20px;
    color: #bbb;
    margin-top: 40px;
}

@media(max-width: 600px) {
    header {
        justify-content: center;
    }
    nav a {
        margin: 0 7px;
    }
    .hero h1 {
        font-size: 27px;
    }
}
</style>
</head>

<body>

<header>
    <h2>🎬 MovieBook</h2>
    <nav>
        <a href="#home">Home</a>
        <a href="#movies">Movies</a>
        <a href="#booking">Book Tickets</a>
    </nav>
</header>

<section class="hero" id="home">
    <h1>Welcome to MovieBook</h1>
    <p>Book your favourite movie tickets easily and quickly!</p>
</section>

<section class="section" id="movies">
    <h2>Now Showing</h2>

    <div class="movies">

        <div class="movie">
            <img src="https://images.unsplash.com/photo-1478720568477-152d9b164e26?w=500" alt="Action movie">
            <h3>Action Adventure</h3>
            <p>Action | ₹150 per ticket</p>
            <button onclick="chooseMovie('Action Adventure',150)">Book Now</button>
        </div>

        <div class="movie">
            <img src="https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?w=500" alt="Drama movie">
            <h3>Dream Story</h3>
            <p>Drama | ₹120 per ticket</p>
            <button onclick="chooseMovie('Dream Story',120)">Book Now</button>
        </div>

        <div class="movie">
            <img src="https://images.unsplash.com/photo-1440404653325-ab127d49abc1?w=500" alt="Mystery movie">
            <h3>Mystery World</h3>
            <p>Thriller | ₹180 per ticket</p>
            <button onclick="chooseMovie('Mystery World',180)">Book Now</button>
        </div>

        <div class="movie">
            <img src="https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?w=500" alt="Cinema">
            <h3>Love Forever</h3>
            <p>Romance | ₹100 per ticket</p>
            <button onclick="chooseMovie('Love Forever',100)">Book Now</button>
        </div>

    </div>
</section>

<section class="section" id="booking">
<div class="booking">

    <h2>Book Your Movie Tickets</h2>

    <label>Customer Name</label>
    <input type="text" id="customer" placeholder="Enter your name">

    <label>Select Movie</label>
    <select id="movie" onchange="updatePrice()">
        <option value="Action Adventure" data-price="150">Action Adventure - ₹150</option>
        <option value="Dream Story" data-price="120">Dream Story - ₹120</option>
        <option value="Mystery World" data-price="180">Mystery World - ₹180</option>
        <option value="Love Forever" data-price="100">Love Forever - ₹100</option>
    </select>

    <label>Select Date</label>
    <input type="date" id="date">

    <label>Select Show Time</label>
    <select id="time">
        <option>10:00 AM</option>
        <option>1:00 PM</option>
        <option>4:00 PM</option>
        <option>7:00 PM</option>
    </select>

    <div class="screen">SCREEN THIS WAY</div>

    <p style="text-align:center;margin-bottom:15px">
        Select your seats
    </p>

    <div class="seats" id="seats"></div>

    <div class="legend">
        <span><i class="dot" style="background:#777"></i> Available</span>
        <span><i class="dot" style="background:#2ecc71"></i> Selected</span>
        <span><i class="dot" style="background:#ff4757"></i> Booked</span>
    </div>

    <div class="summary">
        <p>Ticket Price: ₹<span id="price">150</span></p>
        <p>Selected Seats: <span id="count">0</span></p>
        <h3>Total Amount: ₹<span id="total">0</span></h3>
    </div>

    <button onclick="bookTickets()">Confirm Booking</button>

    <div id="confirmation"></div>

</div>
</section>

<footer>
    <p>© 2026 MovieBook | Online Movie Ticket Booking Management System</p>
    <p>Mini Project - Frontend Development</p>
</footer>

<script>
const seatContainer = document.getElementById("seats");
const movieSelect = document.getElementById("movie");

let selectedSeats = [];

const bookedSeats = ["A3", "B4", "C2", "D5"];

function createSeats() {
    seatContainer.innerHTML = "";

    const rows = ["A", "B", "C", "D"];

    rows.forEach(row => {
        for (let i = 1; i <= 6; i++) {
            const seatNumber = row + i;
            const seat = document.createElement("div");

            seat.className = "seat";
            seat.textContent = seatNumber;

            if (bookedSeats.includes(seatNumber)) {
                seat.classList.add("booked");
            } else {
                seat.addEventListener("click", function() {
                    toggleSeat(seatNumber, seat);
                });
            }

            seatContainer.appendChild(seat);
        }
    });
}

function toggleSeat(number, element) {
    if (selectedSeats.includes(number)) {
        selectedSeats = selectedSeats.filter(
            seat => seat !== number
        );
        element.classList.remove("selected");
    } else {
        selectedSeats.push(number);
        element.classList.add("selected");
    }

    updateSummary();
}

function updatePrice() {
    const price = Number(
        movieSelect.options[movieSelect.selectedIndex].dataset.price
    );

    document.getElementById("price").textContent = price;
    updateSummary();
}

function updateSummary() {
    const price = Number(
        movieSelect.options[movieSelect.selectedIndex].dataset.price
    );

    document.getElementById("count").textContent =
        selectedSeats.length;

    document.getElementById("total").textContent =
        selectedSeats.length * price;
}

function chooseMovie(name, price) {
    movieSelect.value = name;
    updatePrice();
    document.getElementById("booking").scrollIntoView({
        behavior: "smooth"
    });
}

function bookTickets() {
    const name = document.getElementById("customer").value.trim();
    const movie = movieSelect.value;
    const date = document.getElementById("date").value;
    const time = document.getElementById("time").value;

    if (!name || !date || selectedSeats.length === 0) {
        alert("Please enter your name, select a date and choose at least one seat.");
        return;
    }

    const selectedDate = new Date(date + "T00:00:00");
    const today = new Date();
    today.setHours(0, 0, 0, 0);

    if (selectedDate < today) {
        alert("Please select today or a future date.");
        return;
    }

    const price = Number(
        movieSelect.options[movieSelect.selectedIndex].dataset.price
    );

    const total = price * selectedSeats.length;
    const confirmation = document.getElementById("confirmation");

    confirmation.style.display = "block";

    confirmation.innerHTML = `
        <h3>🎉 Booking Confirmed!</h3>
        <p>Customer: ${escapeHTML(name)}</p>
        <p>Movie: ${escapeHTML(movie)}</p>
        <p>Date: ${escapeHTML(date)}</p>
        <p>Show Time: ${escapeHTML(time)}</p>
        <p>Seats: ${selectedSeats.join(", ")}</p>
        <p>Total Amount: ₹${total}</p>
        <p>Booking ID: MB${Date.now().toString().slice(-8)}</p>
        <p>Thank you for booking with MovieBook!</p>
    `;

    selectedSeats.forEach(seat => bookedSeats.push(seat));
    selectedSeats = [];
    createSeats();
    updateSummary();

    confirmation.scrollIntoView({behavior: "smooth"});
}

function escapeHTML(value) {
    return value.replace(/[&<>"']/g, char => ({
        "&": "&amp;",
        "<": "&lt;",
        ">": "&gt;",
        '"': "&quot;",
        "'": "&#39;"
    })[char]);
}

document.getElementById("date").min =
    new Date().toLocaleDateString("en-CA");

createSeats();
updatePrice();
</script>

</body>
</html>
