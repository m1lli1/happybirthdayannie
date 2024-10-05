document.addEventListener('DOMContentLoaded', () => {
    const greeting = document.getElementById('greeting');
    const bouquet = document.getElementById('bouquet');
    const envelope = document.getElementById('envelope');
    const note = document.getElementById('note');
    const flowerContainer = document.getElementById('flowerContainer');

    let clickCount = 0;

    // Function to change the greeting text
    const changeGreeting = () => {
        greeting.textContent = "Oh my god, it's, yeah, I know who it is, it's the birthday girl, of course. It's Daddy Annie!";
    };

    // Function to start adding flowers
    const startFlowers = () => {
        setInterval(() => {
            const flower = document.createElement('img');
            flower.src = 'https://i.imgur.com/your-flower-image.png'; // Replace with your flower image URL
            flower.classList.add('flower');
            flower.style.left = Math.random() * 100 + 'vw';
            flower.style.animationDuration = 5 + Math.random() * 5 + 's';
            flowerContainer.appendChild(flower);

            // Remove flower after animation
            flower.addEventListener('animationend', () => {
                flower.remove();
            });
        }, 500);
    };

    // Initial delay to change greeting
    setTimeout(changeGreeting, 5000); // Changed to 5 seconds for demo purposes

    // Further delay to start flowers
    setTimeout(startFlowers, 10000); // Changed to 10 seconds for demo purposes

    // Click event to handle text change and envelope interaction
    greeting.addEventListener('click', () => {
        clickCount++;
        if (clickCount === 1) {
            changeGreeting();
            setTimeout(startFlowers, 5000); // Further delay after first click
        }
    });

    bouquet.addEventListener('click', () => {
        envelope.classList.toggle('open');
        if (note.style.display === 'block') {
            note.style.display = 'none';
        } else {
            note.style.display = 'block';
        }
    });

    envelope.addEventListener('click', () => {
        envelope.classList.toggle('open');
        if (note.style.display === 'block') {
            note.style.display = 'none';
        } else {
            note.style.display = 'block';
        }
    });

    // Optional: Add flowers continuously after a certain time
    // startFlowers();
});
