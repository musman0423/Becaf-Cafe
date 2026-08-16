<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Welcome to BeCaf Cafe</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: Arial, sans-serif; }
    body { background: #fdf8f3; color: #333; }
    header {
      background: #6b3e26; color: white; text-align: center; padding: 30px 10px;
    }
    header h1 { font-size: 2.5rem; letter-spacing: 2px; }
    nav { background: #a05a36; padding: 10px; text-align: center; }
    nav a { color: white; margin: 0 15px; text-decoration: none; font-weight: bold; }
    section { padding: 40px 20px; max-width: 1200px; margin: auto; }
    h2 { text-align: center; margin-bottom: 25px; color: #6b3e26; font-size: 2rem; }
    .menu-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px;
    }
    .card {
      background: white; border-radius: 12px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      overflow: hidden; text-align: center; transition: transform 0.2s;
    }
    .card:hover { transform: scale(1.03); }
    .card img { width: 100%; height: 180px; object-fit: cover; }
    .card h3 { margin: 12px 0 5px; color: #a05a36;