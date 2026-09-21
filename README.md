<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>The Guess Who? | Mystery Celebrity</title>

<style>

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
    background-color: #f5c542;
    background-image:
        radial-gradient(#111 2px, transparent 2px);
    background-size: 18px 18px;
    color: #111;
}

/* =========================================
   MAIN
========================================= */

.page {
    min-height: 100vh;
    padding: 25px 15px 60px;
}

.container {
    width: 100%;
    max-width: 900px;
    margin: auto;
}

.card {
    background: #fff;
    border: 6px solid #111;
    box-shadow: 12px 12px 0 #111;
    padding: 25px;
    position: relative;
    overflow: hidden;
}

/* =========================================
   HEADER
========================================= */

.header {
    text-align: center;
    position: relative;
    padding: 10px 0 25px;
}

.tag {
    display: inline-block;
    background: #ef476f;
    color: #fff;
    border: 4px solid #111;
    padding: 8px 16px;
    font-weight: 900;
    transform: rotate(-2deg);
    letter-spacing: 1px;
}

h1 {
    font-size: clamp(48px, 10vw, 90px);
    line-height: .85;
    margin: 20px 0 12px;
    letter-spacing: -5px;
    text-transform: uppercase;
    font-weight: 1000;
    text-shadow: 5px 5px 0 #ef476f;
}

.subtitle {
    font-size: 18px;
    font-weight: 700;
    max-width: 600px;
    margin: auto;
}

/* =========================================
   COMIC BURSTS
========================================= */

.burst {
    position: absolute;
    border: 5px solid #111;
    background: #54c2b2;
    padding: 14px;
    font-size: 18px;
    font-weight: 1000;
    z-index: 10;
}

.burst-one {
    right: 0;
    top: 0;
    transform: rotate(9deg);
}

.burst-two {
    left: -5px;
    bottom: 5px;
    background: #ef476f;
    color: #fff;
    transform: rotate(-8deg);
}

/* =========================================
   MYSTERY IMAGE
========================================= */

.image-frame {
    position: relative;
    width: 100%;
    height: 390px;
    background: #111;
    border: 5px solid #111;
    overflow: hidden;
    margin: 20px 0;
}

.image-frame img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
}

/* =========================================
   IMAGE STATES
========================================= */

.placeholder {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: #fff;
    font-size: 70px;
    background:
        linear-gradient(
            135deg,
            #111 25%,
            #222 25%,
            #222 50%,
            #111 50%,
            #111 75%,
            #222 75%
        );
    background-size: 40px 40px;
}

.placeholder-text {
    position: absolute;
    bottom: 15px;
    left: 50%;
    transform: translateX(-50%);
    background: #f5c542;
    color: #111;
    border: 4px solid #111;
    padding: 8px 15px;
    font-weight: 1000;
    z-index: 5;
    white-space: nowrap;
}

/* =========================================
   PROGRESS
========================================= */

.progress-title {
    font-size: 14px;
    font-weight: 1000;
    margin-bottom: 7px;
}

.progress {
    width: 100%;
    height: 18px;
    border: 4px solid #111;
    background: white;
    margin-bottom: 25px;
}

.progress-bar {
    height: 100%;
    width: 25%;
    background: #ef476f;
    transition: width .5s ease;
}

/* =========================================
   CLUE
========================================= */

.clue-number {
    display: inline-block;
    background: #111;
    color: white;
    padding: 8px 14px;
    font-weight: 1000;
    transform: rotate(-2deg);
}

.clue {
    background: #54c2b2;
    border: 5px solid #111;
    padding: 22px;
    margin-top: 12px;
    font-size: 21px;
    line-height: 1.45;
    font-weight: 800;
    box-shadow: 7px 7px 0 #111;
}

.button-area {
    text-align: center;
    margin-top: 30px;
}

button {
    border: 4px solid #111;
    background: white;
    padding: 14px 20px;
    font-family: inherit;
    font-size: 17px;
    font-weight: 1000;
    cursor: pointer;
    transition: .15s;
}

button:hover {
    transform: translate(-3px, -3px);
    box-shadow: 6px 6px 0 #111;
}

button:active {
    transform: translate(0,0);
    box-shadow: none;
}

.next-button {
    background: #ef476f;
    color: white;
}

/* =========================================
   VOTING
========================================= */

.vote {
    text-align: center;
}

.vote h2 {
    font-size: clamp(32px, 7vw, 58px);
    line-height: .95;
    margin: 10px 0;
    text-transform: uppercase;
    text-shadow: 4px 4px 0 #f5c542;
}

.vote p {
    font-size: 18px;
    font-weight: 600;
}

.choices {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 15px;
    margin-top: 25px;
}

.choice {
    min-height: 75px;
    background: #fff;
    box-shadow: 5px 5px 0 #111;
}

.choice:hover {
    background: #54c2b2;
}

/* =========================================
   REVEAL
========================================= */

.reveal {
    background: #111;
    color: white;
    border: 5px solid #111;
    padding: 30px 20px;
    text-align: center;
    animation: reveal .8s ease;
}

@keyframes reveal {

    0% {
        opacity: 0;
        transform: scale(.5) rotate(-8deg);
    }

    60% {
        transform: scale(1.05) rotate(2deg);
    }

    100% {
        opacity: 1;
        transform: scale(1) rotate(0);
    }
}

.answer-label {
    color: #f5c542;
    font-size: 25px;
    font-weight: 1000;
}

.answer {
    color: #ef476f;
    font-size: clamp(38px, 9vw, 75px);
    line-height: .9;
    font-weight: 1000;
    margin: 15px 0 25px;
}

.final-image {
    width: 100%;
    max-width: 500px;
    height: 420px;
    object-fit: cover;
    border: 6px solid white;
    margin: auto;
    display: block;
}

.description {
    max-width: 650px;
    margin: 25px auto 0;
    font-size: 18px;
    line-height: 1.6;
}

.fun-fact {
    max-width: 600px;
    margin: 25px auto;
    background: #f5c542;
    color: #111;
    border: 4px solid #111;
    padding: 17px;
    font-weight: 800;
}

.play-again {
    background: #54c2b2;
}

/* =========================================
   HIDDEN
========================================= */

.hidden {
    display: none !important;
}

/* =========================================
   FOOTER
========================================= */

.footer {
    text-align: center;
    font-size: 13px;
    font-weight: 700;
    margin-top: 30px;
}

/* =========================================
   MOBILE
========================================= */

@media(max-width:600px) {

    .page {
        padding: 15px 10px 40px;
    }

    .card {
        border-width: 4px;
        box-shadow: 7px 7px 0 #111;
        padding: 17px;
    }

    .burst {
        display: none;
    }

    .image-frame {
        height: 270px;
    }

    .clue {
        font-size: 18px;
    }

    .choices {
        grid-template-columns: 1fr;
    }

    .final-image {
        height: 300px;
    }
}

</style>
</head>


<body>

<div class="page">

<div class="container">

<div class="card">


<!-- =====================================
     HEADER
====================================== -->

<div class="header">

    <div class="burst burst-one">
        WOW!
    </div>

    <div class="burst burst-two">
        WHO IS IT?
    </div>

    <span class="tag">
        THE GUESS WHO?
    </span>

    <h1>
        WHO AM I?
    </h1>

    <p class="subtitle">
        Look at the clues. Discover the details.
        Then make your guess!
    </p>

</div>


<!-- =====================================
     MYSTERY IMAGE
====================================== -->

<div class="image-frame" id="mysteryImage">

    <div class="placeholder" id="placeholder">

        🕺

        <div class="placeholder-text">
            MYSTERY PERSON
        </div>

    </div>

    <img
        id="clueImage"
        src=""
        alt="Mystery clue"
        style="display:none;"
    >

</div>


<!-- =====================================
     PROGRESS
====================================== -->

<div class="progress-title">
    CLUES DISCOVERED
</div>

<div class="progress">

    <div
        class="progress-bar"
        id="progressBar">
    </div>

</div>


<!-- =====================================
     CLUE GAME
====================================== -->

<div id="game">

    <div
        class="clue-number"
        id="clueNumber">

        CLUE #1

    </div>


    <div
        class="clue"
        id="clueText">

        I popularized complex dance moves,
        including the gravity-defying lean.

    </div>


    <div class="button-area">

        <button
            class="next-button"
            id="nextButton">

            NEXT CLUE →

        </button>

    </div>

</div>


<!-- =====================================
     VOTING
====================================== -->

<div
    id="voting"
    class="vote hidden">

    <h2>
        WHO DO YOU THINK I AM?
    </h2>

    <p>
        You've seen all the clues.
        <br>
        Now make your guess!
    </p>


    <div class="choices">

        <button class="choice">
            Michael Jackson
        </button>

        <button class="choice">
            Elvis Presley
        </button>

        <button class="choice">
            Bruno Mars
        </button>

        <button class="choice">
            Usher
        </button>

    </div>

</div>


<!-- =====================================
     REVEAL
====================================== -->

<div
    id="reveal"
    class="hidden">

    <div class="reveal">

        <div class="answer-label">
            THE ANSWER IS...
        </div>


        <div class="answer">
            MICHAEL JACKSON
        </div>


        <img
            src="images/michael-full.jpg"
            alt="Michael Jackson"
            class="final-image"
            onerror="this.style.display='none';"
        >


        <div class="description">

            <p>
                Michael Jackson was an American singer,
                songwriter and dancer.
            </p>

            <p>
                He began his career as a child star,
                performing alongside his brothers in
                the Jackson 5.
            </p>

            <p>
                He later became one of the most
                recognizable performers in the world.
            </p>

        </div>


        <div class="fun-fact">

            ⭐ FUN FACT ⭐

            <br><br>

            Michael Jackson's 1982 album
            <i>Thriller</i> became the best-selling
            album in recorded music history.

        </div>


        <button
            class="play-again"
            onclick="restartGame()">

            ↻ PLAY AGAIN

        </button>

    </div>

</div>


</div>


<div class="footer">

    ✦ Made for English learning ✦
    The Guess Who?

</div>


</div>

</div>


<script>

/* =========================================
   CLUES
========================================= */

const clues = [

    {
        text:
        "I popularized complex dance moves, including the gravity-defying lean.",

        image:
        "images/michael-dance.jpg"
    },

    {
        text:
        "My 1982 album became and still remains the best-selling album of all time.",

        image:
        "images/michael-thriller.jpg"
    },

    {
        text:
        "I began my career as a child star, performing alongside my brothers.",

        image:
        "images/michael-young.jpg"
    },

    {
        text:
        "My iconic fashion choices included a single white rhinestone glove and a black fedora hat.",

        image:
        "images/michael-glove.jpg"
    }

];


let currentClue = 0;


/* =========================================
   ELEMENTS
========================================= */

const clueText =
    document.getElementById("clueText");

const clueNumber =
    document.getElementById("clueNumber");

const progressBar =
    document.getElementById("progressBar");

const nextButton =
    document.getElementById("nextButton");

const game =
    document.getElementById("game");

const voting =
    document.getElementById("voting");

const reveal =
    document.getElementById("reveal");

const clueImage =
    document.getElementById("clueImage");

const placeholder =
    document.getElementById("placeholder");


/* =========================================
   SHOW CLUE
========================================= */

function showClue() {

    const clue =
        clues[currentClue];

    clueText.textContent =
        clue.text;

    clueNumber.textContent =
        "CLUE #" + (currentClue + 1);


    const percentage =
        ((currentClue + 1) / clues.length) * 100;

    progressBar.style.width =
        percentage + "%";


    /*
      Try to load the image.
      If the image doesn't exist,
      the placeholder remains visible.
    */

    clueImage.style.display = "none";

    clueImage.onload = function() {

        clueImage.style.display = "block";

        placeholder.style.display = "none";

    };

    clueImage.onerror = function() {

        clueImage.style.display = "none";

        placeholder.style.display = "flex";

    };

    clueImage.src =
        clue.image;

}


/* =========================================
   NEXT BUTTON
========================================= */

nextButton.addEventListener(
    "click",
    function() {

        currentClue++;


        if (currentClue < clues.length) {

            showClue();

        }

        else {

            game.classList.add("hidden");

            voting.classList.remove("hidden");

            progressBar.style.width =
                "100%";

            /*
             * NO AUTOMATIC SCROLL
             *
             * The page stays exactly
             * where the user is.
             */

        }

    }
);


/* =========================================
   VOTING
========================================= */

document
    .querySelectorAll(".choice")
    .forEach(function(choice) {

        choice.addEventListener(
            "click",
            function() {

                voting.classList.add("hidden");

                reveal.classList.remove("hidden");

                /*
                 * NO AUTOMATIC SCROLL
                 *
                 * The page stays exactly
                 * where the user is.
                 */

            }
        );

    });


/* =========================================
   RESTART
========================================= */

function restartGame() {

    currentClue = 0;

    reveal.classList.add("hidden");

    voting.classList.add("hidden");

    game.classList.remove("hidden");

    progressBar.style.width =
        "25%";

    showClue();

    /*
     * NO AUTOMATIC SCROLL
     *
     * The page stays exactly
     * where the user is.
     */

}


/* =========================================
   START
========================================= */

showClue();

</script>

</body>
</html>
