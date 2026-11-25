# Förutsägelser: asynkron kod

Regler:

1. Titta på snutten i `snuttar/sNN.js` (eller på sidan `index.html`). **Kör den inte än.**
2. Skriv din gissning i tabellen: utskrifterna i den ordning du tror att de kommer, separerade med `|`.
3. Kör snutten (knappen _Kör_). Skriv vad som faktiskt skrevs ut.
4. Hade du rätt? Skriv en regel med egna ord för varje snutt du gissade fel på.

| Snutt | Min gissning (i ordning)                        | Faktisk utskrift                                | Rätt? | Min regel om jag hade fel                                                                                                        |
| ----- | ----------------------------------------------- | ----------------------------------------------- | ----- | -------------------------------------------------------------------------------------------------------------------------------- |
| 1     | 1,2,3                                           | 1,2,3                                           | Ja    |
| 2     | A,C,B                                           | A,C,B                                           | Ja    |                                                                                                                                  |
| 3     | noll,kort,lång                                  | noll,kort,lång                                  | Ja    |                                                                                                                                  |
| 4     | inuti promise, then:klart, efter                | inuti promise, efter, then: klart               | nej   | Koden inuti new Promise körs direkt, men funktionen i then väntar tills den vanliga koden är färdig                              |
| 5     | promise, sync, timeout                          | sync, promise, timeout                          | nej   | Först körs vanlig kod, sedan promise-funktionen och sist timeout-funktionen, även när tiden är 0.                                |
| 6     | först?, 6, 7                                    | först? 6, 7                                     | ja    |                                                                                                                                  |
| 7     | förstod inte                                    | fel: slut på mjölk, städar                      | nej   | ”När en promise misslyckas hoppas then över och felet tas om hand i catch. finally körs oavsett om det lyckas eller misslyckas.” |
| 8     | beställer, sätter mig, bullen klar, kaffet klar | beställer, sätter mig, bullen klar, kaffet klar | ja    |                                                                                                                                  |
| 9     |                                                 |                                                 |       |                                                                                                                                  |
| 10    |                                                 |                                                 |       |                                                                                                                                  |
| 11    |                                                 |                                                 |       |                                                                                                                                  |

## Tre meningar med egna ord

1. JavaScript väntar inte på `setTimeout`, utan ...
2. En promise har tre tillstånd: ...
3. `then` körs alltid ...
