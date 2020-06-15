# Zadatak: Igra pogađanja brojeva

Nakon što smo prošli osnove JavaScripta, vrijeme je da stečeno znanje iskoristimo za rješavanje jednog zadatka. Konkretno, vaš zadatak će biti da napravite web stranicu na kojoj će posjetitelj moći odigrati **igru pogađanja brojeva**.

## Opis zadatka
* Napraviti web stranicu, u kojoj je cilj da korisnik pogodi neki zamišljeni broj između 1 i 100 u 10 pokušaja. 
* Nakon svakog pokušaja, posjetitelju morate reći da li je broj pogođen, ili je veći ili manji od zamišljenog. 
* Tijekom igre, posjetitelj mora vidjeti koje je sve brojeve iskoristio. 
* Igra završava kad posjetitelj pogodi točan broj ili ostane bez pokušaja. 
* Kad igra završi, posjetitelj mora moći ponovo pokrenuti igru.

## Primjer 
Vaša stranica bi trebala raditi otprilike ovako:
<hr>
<div class="form">
<label for="guessField">Upišite broj: </label><input type="text" id="guessField" class="guessField">
<input type="submit" value="Pogodi" class="guessSubmit">
</div>

<div class="resultParas">
<p class="guesses"></p>
<p class="lastResult"></p>
<p class="lowOrHi"></p>
</div>
<script>
    let randomNumber = Math.floor(Math.random() * 100) + 1;
    const guesses = document.querySelector('.guesses');
    const lastResult = document.querySelector('.lastResult');
    const lowOrHi = document.querySelector('.lowOrHi');
    const guessSubmit = document.querySelector('.guessSubmit');
    const guessField = document.querySelector('.guessField');
    let guessCount = 1;
    let resetButton;

    function checkGuess() {
    let userGuess = Number(guessField.value);
    if (guessCount === 1) {
        guesses.textContent = 'Previous guesses: ';
    }

    guesses.textContent += userGuess + ' ';

    if (userGuess === randomNumber) {
        lastResult.textContent = 'Congratulations! You got it right!';
        lastResult.style.backgroundColor = 'green';
        lowOrHi.textContent = '';
        setGameOver();
    } else if (guessCount === 10) {
        lastResult.textContent = '!!!GAME OVER!!!';
        lowOrHi.textContent = '';
        setGameOver();
    } else {
        lastResult.textContent = 'Wrong!';
        lastResult.style.backgroundColor = 'red';
        if(userGuess < randomNumber) {
        lowOrHi.textContent = 'Last guess was too low!' ;
        } else if(userGuess > randomNumber) {
        lowOrHi.textContent = 'Last guess was too high!';
        }
    }

    guessCount++;
    guessField.value = '';
    guessField.focus();
    }

    guessSubmit.addEventListener('click', checkGuess);

    function setGameOver() {
    guessField.disabled = true;
    guessSubmit.disabled = true;
    resetButton = document.createElement('button');
    resetButton.textContent = 'Start new game';
    document.body.appendChild(resetButton);
    resetButton.addEventListener('click', resetGame);
    }

    function resetGame() {
    guessCount = 1;
    const resetParas = document.querySelectorAll('.resultParas p');
    for(let i = 0 ; i < resetParas.length ; i++) {
        resetParas[i].textContent = '';
    }

    resetButton.parentNode.removeChild(resetButton);
    guessField.disabled = false;
    guessSubmit.disabled = false;
    guessField.value = '';
    guessField.focus();
    lastResult.style.backgroundColor = 'white';
    randomNumber = Math.floor(Math.random() * 100) + 1;
    }
</script>
<hr>

## Pomoć
Konkretni koraci u zadatku bi bili otprilike slijedeći:
* Generiraj slučajan broj
* Postavi broj pokušaja. Na početku je 1
* Dati mogućnost igraču da upiše broj za pogađanje
* Spremi upisani broj da se može i kasnije vidjeti
* Provjeri da li je upisani broj točan ili ne
* Ako je točan:
  * Ispiši poruku, zaustavi igru, daj mogućnost nove igre
* Ako broj nije točan i igrač ima još pokušaja:
  * Ispiši poruku, dozvoli novo pogađanje, povećaj broj pokušaja za 1
* Ako broj nije točan i igrač više nema pokušaja:
  * Ispiši poruku da je igra gotova, zaustavi igru, daj mogućnost nove igre
* Kad se igra ponovo pokrene, postavi sve na početak i kreni od prvog koraka
