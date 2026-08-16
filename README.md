<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cozy Corner Cafe</title>
<style>
    *{margin:0; padding:0; box-sizing:border-box; font-family: 'Segoe UI', sans-serif;}
    
    body{
        background: linear-gradient(135deg, #ffeaa7, #fab1a0, #ff7675);
        color:#2d3436;
    }

    header{
        background: linear-gradient(90deg, #e17055, #d63031);
        color:white;
        text-align:center;
        padding:30px 10px;
        box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }
    header h1{
        font-size:3em;
        letter-spacing:2px;
        text-shadow: 2px 2px 4px #00050;
    }
    header p{font-size:1.2em; margin-top:5px;}

    nav{
        background:#2d3436;
        padding:12px;
        text-align:center;
        position:sticky;
        top:0;
    }
    nav a{
        color:white; text-decoration:none; margin:0 15px; font-weight:bold;
        padding:8px 15px; border-radius:20px; transition:0.3s;
    }
    nav a:hover{background:#e17055;}

    .container{max-width:1200px; margin:30px auto; padding:20px;}

    h2{
        text-align:center; font-size:2.2em; color:#d63031; margin:30px 0;
        border-bottom:3px dashed #e17055; padding-bottom:10px;
    }

    .menu-grid{
        display:grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap:25px;
    }

    .card{
        background:white;
        border-radius:15px;
        padding:20px;
        text-align:center;
        box-shadow:0 6px 15px rgba(0,0,0,0.15);
        transition:0.3s;
        border-top:5px solid #e17055;
    }
    .card:hover{
        transform: translateY(-8px);
        box-shadow:0 12px 25px rgba(0,0,0,0.25);
    }
    .card img{
        width:100px; height:100px; object-fit:cover; border-radius:50%;
        margin-bottom:10px;
        background:#ffeaa7;
        padding:10px;
    }
    .card h3{color:#d63031; margin-bottom:8px; font-size:1.4em;}
    .card p{color:#636e72; font-size:0.9em; margin-bottom:10px;}
    .price{
        font-size:1.3em; font-weight:bold; color:#00b894;
        background:#dfe6e9; padding:8px; border-radius:10px; display:inline-block;
    }

    footer{
        background:#