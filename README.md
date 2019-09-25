# Responsive-Navbar
Html CSS no JS

HTML 

      <header>
            <h1 class="logo">Logo</h1>
            <input type="checkbox" id="nav-toggle" class="nav-toggle">
            <nav>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">About</a></li>
                    <li><a href="#">Blog</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </nav>
            <!-- for="nav-toggle" will look for an ID -->
            <label for="nav-toggle" class="nav-toggle-label">
                <span></span>
            </label>
        </header>
    
        <div class="content">
            <h2>Your content would go here</h2>
        </div>

CSS

@import url('https://fonts.googleapis.com/css?family=Work+Sans:300,600');

:root {
    --background: rgba(0,214, 170, .85);
}

*, *::before, *::after {
    box-sizing: border-box;
}

body {
    margin: 0;
    background: #222;
    font-family: 'Work Sans', sans-serif;
    font-weight: 400;
}

.content {
    height: 200vh;
    background-image: url(//unsplash.it/1000/1000);
    background-color: #333;
    background-blend-mode: multiply;
    background-size: cover;
    display: grid;
    place-items: center;
}

/* Navigation Style */

header {
    background: var(--background);
    text-align: center;
    position: fixed;
    z-index: 999;  /* because its position fixed */
    width: 100%;
}

.nav-toggle {
    display: none;  /* hides the checkbox */
}

.nav-toggle-label {
    position: absolute; /* to reposition */
    top: 0;
    right: 0; /* i change to right */
    margin-right: 1em;
    /* centers vertically */
    height: 100%;
    display: flex;
    align-items: center;
}

/* Creating a hamburger menu */
.nav-toggle-label span,
.nav-toggle-label span::before,
.nav-toggle-label span::after {
    display: block;
    background: white;
    height: 2px;
    width: 2em;
    border-radius: 2px;
    position: relative;
}

.nav-toggle-label span::before,
.nav-toggle-label span::after {
    content: '';
    position: absolute;
}

.nav-toggle-label span::before {
    bottom: 7px;
}

.nav-toggle-label span::after {
    top: 7px;
}


nav {
    position: absolute;
    text-align: center;
    top: 100%;
    left: 0;
    background: var(--background);
    width: 100%;
    transform: scale(1,0);
    transform-origin: top;
    transition: transform 400ms ease-in-out;
}

nav ul {
    margin: 0;
    padding : 0;
    list-style: none; /* Removes thw bullets */
}

nav li {
    margin-bottom: 1em;
    /* margin-left: 1em; */
}

nav a {
    color: white;
    text-decoration: none; /* remove the underline */
    font-size: 1.2rem;
    text-transform: uppercase; /* capitalize */
    opacity: 0;
    transition: opacity 150ms ease-in-out;
    /* border-bottom: 1px solid white; */

}

nav a:hover {
    color: black;
}

/* ~ looks for any preceding sibling */
/* if theres a nav right after */
.nav-toggle:checked ~ nav {
    transform: scale(1,1);
}

.nav-toggle:checked ~ nav a {
    opacity: 1;
    transition: opacity 250ms ease-in-out 250ms;

}

@media screen and (min-width: 800px) {
    .nav-toggle-label{
        display: none;
    }
    header {
        display: grid;
        grid-template-columns: 1fr auto minmax(600px,3fr) 1fr;
    }
    .logo {
        grid-column: 2 / 3;
    }
    nav {
        all: unset; /* taking off all the things up before on the nav */
        grid-column: 3/4;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }
    nav ul {
        display: flex;
    }
    nav li {
        margin-left: 3em;
        margin-bottom: 0;
    }
    nav a {
        opacity: 1;
        position: relative;
    }
    nav a::before{
        content: ' ';
        display: block;
        height: 5px;
        background: black;
        position: absolute;
        top: -.75em;
        left: 0;
        right: 0;
        transform: scale(0,1);
        transition: transform ease-in-out 250ms;
    }
    nav a:hover::before {
        transform: scale(1,1);

    }
}