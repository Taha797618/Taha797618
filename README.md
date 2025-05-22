// Move enemy cars
new Timer().scheduleAtFixedRate(new TimerTask() {
    @Override
    public void run() {
        runOnUiThread(() -> {
            moveEnemies();
            checkCollision();
            updateScore();
        });
    }
}, 0, 30); // Refresh every 30ms
leftButton.setOnClickListener(v -> {
    player.setX(player.getX() - 30); // Move left
});

rightButton.setOnClickListener(v -> {
    player.setX(player.getX() + 30); // Move right
});private void moveEnemies() {
    enemy1.setY(enemy1.getY() + 10);
    enemy2.setY(enemy2.getY() + 10);

    // Reset position if off screen
    if (enemy1.getY() > screenHeight) {
        enemy1.setY(0);
        enemy1.setX(randomX());
    }

    if (enemy2.getY() > screenHeight) {
        enemy2.setY(0);
        enemy2.setX(randomX());
    }
}

private float randomX() {
    return (float) (Math.random() * (screenWidth - enemy1.getWidth()));
}

private void checkCollision() {
    if (Rect.intersects(player.getHitRect(), enemy1.getHitRect()) || 
        Rect.intersects(player.getHitRect(), enemy2.getHitRect())) {
        Toast.makeText(getApplicationContext(), "Game Over", Toast.LENGTH_SHORT).show();
        finish(); // Ends the activity
    }
}int score = 0;

private void updateScore() {
    score += 1;
    scoreText.setText("Score: " + score);
}
<!---
Taha797618/Taha797618 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
