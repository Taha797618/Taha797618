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
