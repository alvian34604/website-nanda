<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>💖 Cinta Kita 💖</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&display=swap');

body {
    margin: 0;
    padding: 0;
    min-height: 100vh;
    background: linear-gradient(to bottom right, #fde2e4, #fbcfe8);
    font-family: 'Arial', sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    color: #333;
}

/* Kontainer utama */
.container {
    background: white;
    border-radius: 20px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.1);
    padding: 40px;
    max-width: 420px;
    width: 90%;
    text-align: center;
    opacity: 0;
    transform: translateY(50px);
    animation: fadeUp 1s ease forwards;
    animation-delay: 0.5s;
}

/* Gambar di awal */
.profile-img {
    width: 150px;
    height: 150px;
    border-radius: 50%;
    object-fit: cover;
    border: 4px solid #ec4899;
    margin-bottom: 16px;
    opacity: 0;
    animation: fadeIn 1s ease forwards;
    animation-delay: 0.8s;
}

/* Animasi masuk */
@keyframes fadeUp {
    from { opacity: 0; transform: translateY(50px); }
    to { opacity: 1; transform: translateY(0); }
}
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

/* Form muncul setelah semuanya */
#nameForm {
    opacity: 0;
    animation: fadeIn 1s ease forwards;
    animation-delay: 2s;
}

h1 {
    font-family: 'Dancing Script', cursive;
    font-size: 2.7rem;
    color: #ec4899;
    margin-bottom: 10px;
    opacity: 0;
    animation: fadeIn 1s ease forwards;
    animation-delay: 1.4s;
}

.subtitle {
    color: #6b7280;
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeIn 1s ease forwards;
    animation-delay: 1.8s;
}

label {
    display: block;
    font-weight: 500;
    color: #374151;
    margin-bottom: 8px;
    text-align: left;
}

input[type="text"] {
    width: 100%;
    padding: 12px 16px;
    border: 2px solid #f3e8ff;
    border-radius: 10px;
    font-size: 1rem;
    transition: 0.3s;
}

input[type="text"]:focus {
    outline: none;
    border-color: #ec4899;
    box-shadow: 0 0 8px rgba(236, 72, 153, 0.3);
}

.question {
    font-size: 1.25rem;
    color: #1f2937;
    margin: 24px 0;
    min-height: 60px;
}

.buttons {
    display: flex;
    gap: 16px;
    justify-content: center;
    margin-top: 16px;
}

button {
    padding: 12px 24px;
    border: none;
    border-radius: 10px;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s ease;
}

.btn-yes {
    background: #ec4899;
    color: white;
}
.btn-yes:hover {
    background: #db2777;
    transform: scale(1.05);
}

.btn-no {
    background: #d1d5db;
    color: #374151;
}
.btn-no:hover {
    background: #9ca3af;
    transform: scale(1.05);
}

/* POPUP */
.popup-overlay {
    position: fixed;
    top: 0; left: 0;
    width: 100vw; height: 100vh;
    background: rgba(0,0,0,0.4);
    display: none;
    align-items: center;
    justify-content: center;
    z-index: 999;
}

.popup {
    background: white;
    border-radius: 20px;
    padding: 30px;
    max-width: 320px;
    text-align: center;
    box-shadow: 0 10px 25px rgba(0,0,0,0.2);
    animation: popUp 0.4s ease;
}

.popup h2 {
    font-family: 'Dancing Script', cursive;
    color: #ec4899;
    margin-bottom: 10px;
}

.popup p {
    color: #4b5563;
    margin-bottom: 20px;
}

.popup .emoji {
    font-size: 3rem;
    margin-bottom: 10px;
}

.popup button {
    background: #ec4899;
    color: white;
    border: none;
    border-radius: 8px;
    padding: 10px 20px;
    cursor: pointer;
    transition: background 0.3s;
}
.popup button:hover {
    background: #db2777;
}

@keyframes popUp {
    0% { transform: scale(0.7); opacity: 0; }
    100% { transform: scale(1); opacity: 1; }
}

@media (max-width: 480px) {
    .container {
        padding: 28px;
    }
    h1 { font-size: 2.2rem; }
    .buttons { flex-direction: column; }
}
</style>
</head>
<body>
    <div class="container" id="container">
        <!-- Tambahkan foto kamu di sini -->
        <img src="https://i.ibb.co/V0jLJQRg/Whats-App-Image-2025-09-27-at-16-41-24-d15f8e09.jpg" alt="Foto Kamu" class="profile-img">

        <h1>💖 Selamat Datang 💖</h1>
        <p class="subtitle">Isi namamu dan jawab dengan jujur ya!</p>

        <form id="nameForm">
            <label for="name">Siapa namamu?</label>
            <input type="text" id="name" placeholder="Masukkan nama kamu..." required>

            <div id="questionSection" style="display:none;">
                <p class="question" id="question"></p>
                <div class="buttons">
                    <button type="button" class="btn-yes" onclick="handleAnswer('yes')">💖 YES!</button>
                    <button type="button" class="btn-no" onclick="handleAnswer('no')">No 😢</button>
                </div>
            </div>
        </form>
    </div>

    <!-- POP-UP -->
    <div class="popup-overlay" id="popupOverlay">
        <div class="popup" id="popupBox">
            <div class="emoji">💖</div>
            <h2 id="popupTitle">Yay!</h2>
            <p id="popupMessage">Kita resmi jadi pasangan!</p>
            <button onclick="closePopup()">Tutup</button>
        </div>
    </div>

<script>
const nameInput = document.getElementById('name');
const questionSection = document.getElementById('questionSection');
const questionText = document.getElementById('question');
const popupOverlay = document.getElementById('popupOverlay');
const popupTitle = document.getElementById('popupTitle');
const popupMessage = document.getElementById('popupMessage');
const popupEmoji = document.querySelector('.emoji');

nameInput.addEventListener('input', function() {
    if (this.value.trim() !== '') {
        questionSection.style.display = 'block';
        questionText.innerHTML = `Hai ${this.value}, mau ga jadi pacarku? 💕`;
    } else {
        questionSection.style.display = 'none';
    }
});

function handleAnswer(response) {
    const name = nameInput.value.trim();

    if (response === 'yes') {
        popupEmoji.textContent = '🎉';
        popupTitle.textContent = `Yay! ${name} Mau! 💖`;
        popupMessage.textContent = 'Kita resmi jadi pasangan! 💞';
    } else {
        popupEmoji.textContent = '😢';
        popupTitle.textContent = `Oke ${name}...`;
        popupMessage.textContent = 'Gapapa, mungkin belum waktunya 😔';
    }

    popupOverlay.style.display = 'flex';
}

function closePopup() {
    popupOverlay.style.display = 'none';
    nameInput.value = '';
    questionSection.style.display = 'none';
}
</script>
</body>
</html>
