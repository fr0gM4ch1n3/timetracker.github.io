
# Typescript-Tutorial: Variablen verstehen und anwenden

Willkommen zu deinem TypeScript-Tutorial! Ziel dieses Tutorials ist es, Variablen in TypeScript zu verstehen und zu lernen, wie man sie einsetzt. Am Ende solltest du in der Lage sein, Funktionen einer Bibliothek zu nutzen, indem du die Funktionssignaturen interpretierst und entsprechend Variablen bereitstellst.

### Aufgabe 1: Eine Variable deklarieren und verwenden

Deklariere eine Variable und gib ihren Wert in der Konsole aus.

// Beispiel:
```typescript
let name: string = "Max";
console.log(name);
```

**Aufgabe:**

1.  Erstelle eine Variable `alter` mit dem Wert 25 (Typ: number).
2.  Erstelle eine Variable `istStudent` mit dem Wert true (Typ: boolean).
3.  Gib beide Variablen in der Konsole aus.
    

### Aufgabe 2: Konstanten verwenden

Verwende `const`, um eine Konstante zu deklarieren.

// Beispiel:
```typescript
const pi: number = 3.14159;
console.log(pi);
```

**Aufgabe:**

1.  Deklariere eine Konstante `maxPunkte` mit dem Wert 100.
2.  Versuche, den Wert von `maxPunkte` zu ändern, und beobachte, was passiert.
    

### Aufgabe 3: Variablen an Funktionen übergeben

Lerne, wie Variablen an Funktionen übergeben werden.

// Beispiel:
```typescript
function begruessung(name: string): string {
	return `Hallo, ${name}!`;
}

const meinName: string = "Anna";
console.log(begruessung(meinName));
```

**Aufgabe:**

1.  Erstelle eine Funktion `quadriere`, die eine Zahl entgegennimmt und das Quadrat dieser Zahl zurückgibt.
2.  Deklariere eine Variable `zahl` mit dem Wert 5 und übergib sie an die Funktion `quadriere`.
3.  Gib das Ergebnis in der Konsole aus.
    

### Aufgabe 4: Funktionen mit mehreren Parametern

Arbeite mit Funktionen, die mehrere Parameter verwenden.

// Beispiel:
```typescript
function addiere(a: number, b: number): number {
	return a + b;
}

const ergebnis: number = addiere(3, 7);
console.log(ergebnis);
```

**Aufgabe:**

1.  Erstelle eine Funktion `berechne`, die zwei Zahlen und einen Operator (`+`, `-`, `*`, `/`) als String entgegennimmt.
2.  Führe die entsprechende Operation durch und gib das Ergebnis zurück.
3.  Teste die Funktion mit verschiedenen Eingaben.

### Aufgabe 5: Typen explizit angeben

Verwende explizite Typen, um Variablen und Parameter zu deklarieren.

// Beispiel:

```typescript
let stadt: string = "Berlin";
let einwohner: number = 3769000;
let istHauptstadt: boolean = true;

function beschreibung(stadt: string, einwohner: number): string {
	return `${stadt} hat ${einwohner} Einwohner.`;
}

console.log(beschreibung(stadt, einwohner));
```

**Aufgabe:**

1.  Erstelle eine Variable `land` mit dem Typ string und einem Wert deiner Wahl.
2.  Erstelle eine Funktion `landInfo`, die `land` und `einwohner` als Parameter verwendet und eine Beschreibung zurückgibt.
    

### Aufgabe 6: Typen aus Bibliotheks-Funktionssignaturen lesen

Nehmen wir an, du arbeitest mit folgender Funktionssignatur aus einer Bibliothek:
function rechneMitDaten(daten: number\[\], faktor: number): number\[\];

**Aufgabe:**

1.  Erstelle ein Array `zahlen` mit den Werten \[2, 4, 6\].    
2.  Rufe `rechneMitDaten` mit `zahlen` und einem Faktor deiner Wahl auf.
3.  Implementiere `rechneMitDaten`, sodass jede Zahl im Array mit dem Faktor multipliziert wird.
    


### Aufgabe 7: Einfache API simulieren

Simuliere eine einfache API-Funktion mit einer Typdefinition.

// Beispiel:
```typescript
function sendeNachricht(empfaenger: string, nachricht: string): boolean {
	console.log(`Nachricht an ${empfaenger}: ${nachricht}`);
	return true;
}

sendeNachricht("Lisa", "Hallo, wie geht's?");
```

**Aufgabe:**

1.  Erstelle eine Funktion `holeDaten`, die einen URL-String als Parameter verwendet und ein Objekt zurückgibt (z. B. `{status: 200, daten: "Erfolg"}`).
2.  Teste die Funktion mit verschiedenen URL-Strings.
    
- - -

Mit diesen Aufgaben solltest du ein solides Verständnis von Variablen und deren Verwendung in TypeScript erlangen. Viel Erfolg und viel Spaß beim Programmieren!
