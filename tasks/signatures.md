
# TypeScript-Tutorial: Arbeiten mit API-Dokumentationen und Funktionssignaturen verstehen

In diesem Tutorial lernst du, wie du API-Dokumentationen liest und Funktionen basierend auf den bereitgestellten Signaturen verwendest. Ziel ist es, ein besseres Verständnis für die Arbeit mit Typdefinitionen und Bibliotheken in TypeScript zu entwickeln.


## Abschnitt 1: Was sind Funktionssignaturen?
Eine Funktionssignatur beschreibt die Parameter und den Rückgabetyp einer Funktion. Sie hilft dir zu verstehen, wie du die Funktion verwenden kannst.

### Beispiel:
```typescript
function addiere(a: number, b: number): number;
```
- **Parameter:** `a` und `b` sind vom Typ `number`.
- **Rückgabetyp:** Die Funktion gibt einen Wert vom Typ `number` zurück.

### Aufgabe 1: Signaturen analysieren
Schau dir die folgende Funktionssignatur an und beantworte die Fragen:
```typescript
function begruessung(name: string, formal: boolean): string;
```
1. Welche Parameter erwartet die Funktion?
2. Welchen Typ hat der Rückgabewert?


## Abschnitt 2: Funktionen auf Basis von Signaturen erstellen
### Aufgabe 3: Arbeiten mit optionalen Parametern
Optionalen Parameter werden mit einem `?` gekennzeichnet.
```typescript
function begruessung(name: string, formal?: boolean): string;
```
**Aufgabe:**
Implementiere die Funktion, sodass sie je nach `formal` entweder "Hallo" oder "Sehr geehrte(r)" zurückgibt.


## Abschnitt 3: Typen in API-Dokumentationen verstehen
In API-Dokumentationen findest du oft Typdefinitionen. Diese helfen dir zu verstehen, welche Daten du senden oder empfangen kannst.

### Beispiel:
```typescript
function fetchDaten(url: string): Promise<{status: number, daten: any}>;
```
- **Parameter:**
  - `url`: Eine Zeichenkette (String)
- **Rückgabetyp:**
  - Ein Promise, das ein Objekt mit den Schlüsseln `status` (Zahl) und `daten` (beliebiger Typ) zurückgibt.

### Aufgabe 4: API-Funktion verwenden
Schreibe eine Funktion, die die gegebene Signatur nutzt, um Daten von einer URL abzurufen und den Status zu prüfen.


## Abschnitt 4: Fortgeschrittene Typen und Generics
### Aufgabe 5: Generische Funktionen
Eine generische Funktion kann mit unterschiedlichen Typen arbeiten. Das wird oft bei APIs verwendet.

### Beispiel:
```typescript
function identitaet<T>(wert: T): T {
    return wert;
}
console.log(identitaet<string>("Hallo")); // "Hallo"
console.log(identitaet<number>(42)); // 42
```

**Aufgabe:**
Implementiere eine Funktion `filter`, die ein Array von Elementen und eine Filterfunktion entgegennimmt.

**Signatur:**
```typescript
function filter<T>(array: T[], kriterium: (element: T) => boolean): T[];
```


## Abschnitt 5: Herausforderung - Komplexe API-Integration
### Aufgabe 6: Arbeiten mit komplexen API-Daten
Hier ist eine Typdefinition für eine API-Antwort:
```typescript
type ApiAntwort = {
    status: number;
    daten: {
        benutzer: {
            id: number;
            name: string;
        }[];
    };
};
```
**Aufgabe:**
1. Implementiere eine Funktion `holeBenutzer`, die eine URL entgegennimmt und eine Liste von Benutzernamen zurückgibt.
2. Nutze die Typdefinition `ApiAntwort`, um den Rückgabetyp der Funktion zu definieren.


## Abschnitt 6: Arbeiten mit Union-Typen, Partial und Overloads

### Aufgabe 7: Union-Typen verwenden
Union-Typen ermöglichen es, mehrere Typen zu kombinieren.

** Beispiel:**
```typescript
const werte: (string | number)[] = ["Hallo", 12, "Welt", 4.5];
const formatiert = werte.map(formatValue);
console.log(formatiert);
// ["HALLO", "12.00", "WELT", "4.50"]
```

**Aufgabe:**
Schreibe eine Funktion `formatValue`, die entweder eine Zahl oder einen String entgegennimmt und entsprechend formatiert.


### Aufgabe 8: Partial verwenden
Mit `Partial<T>` kannst du alle Eigenschaften eines Typs optional machen.

***Beispiel:***
```typescript
const benutzerUpdates: Partial<Benutzer>[] = [
    { name: "Lisa" },
    { email: "lisa@example.com" },
    { name: "Tom", email: "tom@example.com" }
];

const aktualisierteBenutzer = benutzerUpdates.map((update, index) => updateBenutzer(index + 1, update));
console.log(aktualisierteBenutzer);
// [
//   { id: 1, name: "Lisa", email: "max@example.com" },
//   { id: 2, name: "Max Mustermann", email: "lisa@example.com" },
//   { id: 3, name: "Tom", email: "tom@example.com" }
// ];
```

**Aufgabe:**
Erstelle eine Funktion `updateBenutzer`, die ein teilweise aktualisiertes Benutzerobjekt entgegennimmt.


### Aufgabe 9: Überladene Funktionen verwenden
Mit Overloads kannst du Funktionen mit mehreren Signaturen definieren.

***Beispiel:***
```typescript
const results = [
    combine("Typ", "Script"),
    combine(5, 15)
];
console.log(results);
// ["TypScript", 20]
```

**Aufgabe:**
Schreibe eine Funktion `combine`, die:
- Zwei Strings konkatenieren kann.
- Zwei Zahlen addieren kann.


