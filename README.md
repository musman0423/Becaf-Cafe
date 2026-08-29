<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bicaf-Cafe</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background: #252525;
            color: white;
            min-height: 100vh;
            transition: 0.5s;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, #202020, #5ec8f8);
            padding: 30px 20px;
            text-align: center;
            box-shadow: 0 4px 15px rgba(0,0,0,0.5);
        }

        header h1 {
            font-size: 45px;
            color: #ffffff;
            letter-spacing: 3px;
            text-shadow: 0 0 12px #5ec8f8;
        }

        header p {
            margin-top: 8px;
            color: #dff7ff;
            font-size: 18px;
        }

        /* Navigation */
        nav {
            background: #181818;
            display: flex;
            justify-content: center;
            gap: 25px;
            padding: 15px;
            position: sticky;
            top: 0;
            z-index: 10;
        }

        nav a {
            color: #69d2ff;
            text-decoration: none;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }

        nav a:hover {
            color: white;
            text-shadow: 0 0 10px #5ec8f8;
        }

        /* Main */
        main {
            width: 90%;
            max-width: 1100px;
            margin: 40px auto;
        }

        .section-title {
            text-align: center;
            color: #63d0ff;
            font-size: 32px;
            margin-bottom: 25px;
        }

        .menu-section {
            margin-bottom: 60px;
        }

        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
        }

        .menu-card {
            background: #333333;
            border: 1px solid #4fc3f7;
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: 0.4s;
            box-shadow: 0 5px 15px rgba(0,0,0,0.4);
        }

        .menu-card:hover {
            transform: translateY(-8px) scale(1.02);
            background: #3d3d3d;
            box-shadow: 0 0 20px rgba(79,195,247,0.6);
        }

        .menu-card h3 {
            color: #67d5ff;
            margin-bottom: 10px;
            font-size: 21px;
        }

        .menu-card p {
            color: #dddddd;
            line-height: 1.5;
        }

        .icon {
            font-size: 42px;
            margin-bottom: 15px;
        }

        /* Theme Button */
        .theme-button {
            display: block;
            margin: 20px auto 0;
            padding: 12px 25px;
            border: none;
            border-radius: 25px;
            background: #5ec8f8;
            color: #111;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }

        .theme-button:hover {
            background: white;
            box-shadow: 0 0 15px #5ec8f8;
        }

        /* Footer */
        footer {
            background: #151515;
            text-align: center;
            padding: 25px;
            color: #aaa;
            border-top: 1px solid #4fc3f7;
        }

        footer span {
            color: #63d0ff;
        }

        /* Light theme */
        body.light-theme {
            background: #eaf8ff;
            color: #222;
        }

        body.light-theme .menu-card {
            background: white;
            color: #222;
        }

        body.light-theme .menu-card p {
            color: #555;
        }

        body.light-theme nav {
            background: #d7f3ff;
        }

        body.light-theme footer {
            background: #ccefff;
            color: #333;
        }
    </style>
</head>

<body>

    <header>
        <h1>☕ Bicaf-Cafe</h1>
        <p>Fresh Taste • Great Food • Happy Moments</p>

        <button class="theme-button" onclick="changeTheme()">
            🌙 Change Theme
        </button>
    </header>

    <nav>
        <a href="#food">Food Menu</a>
        <a href="#drinks">Drinks Menu</a>
    </nav>

    <main>

        <!-- FIRST SECTION: FOOD -->
        <section class="menu-section" id="food">

            <h2 class="section-title">🍔 Food Menu</h2>

            <div class="menu-grid">

                <div class="menu-card">
                    <div class="icon">🍔</div>
                    <h3>Classic Burger</h3>
                    <p>Juicy burger with fresh vegetables and special sauce.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🍔</div>
                    <h3>Zinger Burger</h3>
                    <p>Crispy spicy chicken fillet with fresh salad and sauce.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🌯</div>
                    <h3>Chicken Shawarma</h3>
                    <p>Tender chicken, fresh vegetables and creamy garlic sauce.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🥪</div>
                    <h3>Chicken Sandwich</h3>
                    <p>Delicious chicken sandwich with fresh vegetables and sauce.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🍗</div>
                    <h3>Crispy Chicken</h3>
                    <p>Golden crispy chicken served with delicious seasoning.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🍚</div>
                    <h3>Chicken Rice</h3>
                    <p>Flavorful rice served with tender chicken and special spices.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🍚</div>
                    <h3>Spicy Chicken Rice</h3>
                    <p>Spicy and delicious chicken rice for a flavorful meal.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🍚</div>
                    <h3>Special Chicken Rice</h3>
                    <p>Our special rice combination with perfectly cooked chicken.</p>
                </div>

            </div>
        </section>


        <!-- SECOND SECTION: DRINKS -->
        <section class="menu-section" id="drinks">

            <h2 class="section-title">🥤 Soft Drinks & Juices</h2>

            <div class="menu-grid">

                <div class="menu-card">
                    <div class="icon">🍊</div>
                    <h3>Fresh Orange Juice</h3>
                    <p>Freshly prepared orange juice.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🍎</div>
                    <h3>Apple Juice</h3>
                    <p>Refreshing and naturally fruity apple juice.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🥭</div>
                    <h3>Mango Juice</h3>
                    <p>Sweet and refreshing mango juice.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🍍</div>
                    <h3>Pineapple Juice</h3>
                    <p>Tropical and refreshing pineapple juice.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🍉</div>
                    <h3>Watermelon Juice</h3>
                    <p>Cool and refreshing watermelon drink.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🍌</div>
                    <h3>Banana Shake</h3>
                    <p>Creamy and delicious banana shake.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🥤</div>
                    <h3>Pepsi</h3>
                    <p>Classic chilled Pepsi.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🥤</div>
                    <h3>Sprite</h3>
                    <p>Refreshing lemon-lime Sprite.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🥤</div>
                    <h3>7UP</h3>
                    <p>Cool and refreshing 7UP.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🥤</div>
                    <h3>Coke</h3>
                    <p>Classic chilled Coca-Cola.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🧊</div>
                    <h3>Cold Drink</h3>
                    <p>Choose your favorite chilled soft drink.</p>
                </div>

                <div class="menu-card">
                    <div class="icon">🍹</div>
                    <h3>Mixed Fruit Juice</h3>
                    <p>A refreshing blend of delicious seasonal fruits.</p>
                </div>

            </div>
        </section>

    </main>

    <footer>
        <p>© 2026 <span>Bicaf-Cafe</span> | Fresh Food & Refreshing Drinks</p>
    </footer>


    <script>

        // Dynamic theme changer
        function changeTheme() {
            document.body.classList.toggle("light-theme");

            const button = document.querySelector(".theme-button");

            if (document.body.classList.contains("light-theme")) {
                button.innerHTML = "☀️ Dark Theme";
            } else {
                button.innerHTML = "🌙 Light Theme";
            }
        }

        // Smooth scrolling
        document.querySelectorAll("nav a").forEach(link => {
            link.addEventListener("click", function(event) {
                event.preventDefault();

                const target = document.querySelector(this.getAttribute("href"));

                target.scrollIntoView({
                    behavior: "smooth"
                });
            });
        });

    </script>

</body>
</html>