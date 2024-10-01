var lives, score;
whenFireballHitSpaceship = function whenFireballHitSpaceship() {
    Hatch.playSound('Hit spaceship');
    lives = (typeof lives == 'number' ? lives : 0) + -1;
    if (lives == 0) {
        Hatch.playSound('Game over');
        gameOver();
    }
}

function onGreenPlayButtonClicked() {
    Hatch.setBackgroundSound('zelda theme');
    score = 0;
    lives = 3;
}

whenLasersHitEnemies = function whenLasersHitEnemies() {
    Hatch.playSound('Hit alien');
    destroyEnemy();
    score = score + 1;
}
whileGameIsRunning = function whileGameIsRunning() {
    enemiesThrowFireballs();
}
Hatch.onKeyDown(function(event) {
    if (event.code === 'Space') {
        fireLaser();
    }
});

Hatch.onKeyDown(function(event) {
    if (event.code === 'ArrowLeft' || event.code === 'KeyA') {
        shipMoveLeft();
    }
});

Hatch.onKeyDown(function(event) {
    if (event.code === 'ArrowRight' || event.code === 'KeyD') {
        shipMoveRight();
    }
});
