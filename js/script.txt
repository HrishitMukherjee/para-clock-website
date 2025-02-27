function updateClock() {
    const now = new Date();

    const hours = now.getHours();
    const minutes = now.getMinutes();
    const seconds = now.getSeconds();

    const hourDeg = (hours % 12) * 30 + minutes * 0.5;
    const minuteDeg = minutes * 6;
    const secondDeg = seconds * 6;

    document.querySelector('.hour-hand').style.transform = `translate(-50%, 0) rotate(${hourDeg}deg)`;
    document.querySelector('.minute-hand').style.transform = `translate(-50%, 0) rotate(${minuteDeg}deg)`;
    document.querySelector('.second-hand').style.transform = `translate(-50%, 0) rotate(${secondDeg}deg)`;

    const formattedHours = hours.toString().padStart(2, '0');
    const formattedMinutes = minutes.toString().padStart(2, '0');
    const formattedSeconds = seconds.toString().padStart(2, '0');

    document.querySelector('.digital-time').textContent = `${formattedHours}:${formattedMinutes}:${formattedSeconds}`;

    const day = now.getDate();
    const monthNames = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
    const month = monthNames[now.getMonth()];
    const year = now.getFullYear();

    document.querySelector('.current-date').textContent = `${day} ${month} ${year}`;

    // NEW CODE - Add day of the week
    const dayNames = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
    const weekday = dayNames[now.getDay()];
    document.querySelector('.current-day').textContent = weekday;
}

// Light mode toggle (keep existing)
function toggleLightMode() {
    document.body.classList.toggle('light-mode');
}

// Call updateClock every second
setInterval(updateClock, 1000);
updateClock(); // Initial call to set clock immediately
