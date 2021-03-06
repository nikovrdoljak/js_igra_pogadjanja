# Zadatak: Igra pogađanja brojeva

Nakon što smo prošli osnove JavaScripta, vrijeme je da stečeno znanje iskoristimo za rješavanje jednog zadatka. Konkretno, vaš zadatak će biti da napravite web stranicu na kojoj će posjetitelj moći odigrati **igru pogađanja brojeva**.

## Opis problema
* Napraviti web stranicu, u kojoj je cilj da korisnik pogodi neki zamišljeni broj između 1 i 100 u 10 pokušaja. 
* Nakon svakog pokušaja, posjetitelju morate reći da li je broj pogođen, ili je veći ili manji od zamišljenog. 
* Tijekom igre, posjetitelj mora vidjeti koje je sve brojeve iskoristio. 
* Igra završava kad posjetitelj pogodi točan broj ili ostane bez pokušaja. 
* Kad igra završi, posjetitelj mora moći ponovo pokrenuti igru.

## Vaš zadatak
* Napraviti html stranicu na kojoj se nalazi HTML i JavaScript kod koji rješavaju zadani problem.
* Primjer od kojeg možete krenuti imate na stranici [igra.html](igra.html) unutar ovog repozitorija.
* Svoj kod objavite na GitHub-u. Poželjno je da to bude preko vašeg individualiziranog linka: [https://classroom.github.com/a/9Hu1qiQi](https://classroom.github.com/a/9Hu1qiQi). Otvorite ga i prihvatite zadatak, te zatim klonirajte projekt na svom računalu, a kad završite samo napravite *commit/push*.
* Primjer kako može vaša igra izgledati:

![igra1.png](igra1.png)

## Koraci u kodu
Konkretni koraci u samom programu bi bili otprilike slijedeći:
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

## Pomoć u kodiranju
* Koristite `document.querySelector()` za reference na HTML elemente. U modulu 1, poglavlju 2, te modulu 2, poglavlju 1, imali smo primjer korištenja ove metode. `textContent` svojstvo ovako referenciranih objekata koristimo za promjenu njihovog teksta.
* Koristite `btnPogodi.addEventListener('click', provjeri);` kako biste pozvali funkciju  koja provjerava da li je posjetitelj pogodio broj. `provjeri` je funkcija koju morate napisati. Npr:
```JavaScript
function provjeri() {
    const broj = document.querySelector('#txtBroj');
    alert('Upisali ste: ' + broj);
}
``` 
* Koristite `Math.random()` i `Math.floor()` funkcije za generiranje slučajnog broja i  zaokruživanje brojeva. U modulu 2, poglavlju 8 smo koristi `random()` funkciju.
* Koristite `let btnNovaIgra = document.createElement('button')` i `document.body.appendChild(btnNovaIgra)` da biste na kraju igre stvorili novi botun za započimanje nove igre. Ne zaboravite i `btnNovaIgra.addEventListener('click', postaviNovuIgru)` kako bi posjetitelj resetirao stranicu klikom na novi botun.
* Naravno, igru možete napisati i na neki drugačiji način. Budete kreativni.
