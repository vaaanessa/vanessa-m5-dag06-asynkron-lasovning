# Tidslinje: rita vad som händer

Välj snutt 5 och snutt 10. Fyll i tabellerna steg för steg. Skriv vad som ligger i varje del **efter** varje steg.

Förklaring:

- **Anropsstacken** är den kod som körs just nu.
- **Microtask-kön** är promise-callbacks som väntar på att få köra.
- **Task-kön** är timer-callbacks och liknande som väntar på att få köra.
- Regel: när stacken är tom körs först ALLA microtasks, sedan EN task, sedan tomma microtasks igen, och så vidare.

## Snutt 5

| Steg | Vad händer                          | Stacken    | Microtask-kön | Task-kön      | Utskrift hittills      |
| ---- | ----------------------------------- | ---------- | ------------- | ------------- | ---------------------- |
| 1    | setTimeout anropas                  | Vanlig kod | Tom           | timer timeout | Ingen                  |
| 2    | Promise.resolve().then(...) anropas | Vanlig kod | promise       | timer timeout | Ingen                  |
| 3    | console.log("sync")                 | Tom        | promise       | timer timeout | sync                   |
| 4    | Stacken tom: vad körs först?        | Tom        | Tom           | timer timeout | sync, promise          |
| 5    | Nästa                               | Tom        | Tom           | Tom           | sync, promise, timeout |

## Snutt 10

| Steg | Vad händer                       | Stacken    | Microtask-kön | Task-kön        | Utskrift hittills |
| ---- | -------------------------------- | ---------- | ------------- | --------------- | ----------------- |
| 1    | console.log("1")                 | Vanlig kod | Tom           | Tom             | 1                 |
| 2    | första setTimeout                | Vanlig kod | Tom           | timer 2         | 1                 |
| 3    | Promise.resolve().then(3)        | Vanlig kod | promise 3     | timer 2         | 1                 |
| 4    | andra setTimeout                 | Vanlig kod | promise 3     | timer2, timer 4 | 1                 |
| 5    | console.log("6")                 | Tom        | promise 3     | timer2, timer 4 | 1,6               |
| 6    | stacken tom, microtask-kön först | Tom        | Tom           | timer2, timer 4 | 1,6,3             |
| 7    | första tasken                    | Tom        | Tom           | timer 4         | 1,6,3,2           |
| 8    | andra tasken                     | Tom        | promise 5     | Tom             | 1,6,3,2,4         |
| 9    | microtask 5                      | Tom        | Tom           | Tom             | 1,6,3,2,4,5       |

## Min förklaring i en mening

Varför kommer en promise-callback före en timer med 0 ms?
När den vanliga koden är klar körs promise-funktionerna i microtask-kön före timerfunktionerna i task-kön, även om timern har tiden 0 ms.
