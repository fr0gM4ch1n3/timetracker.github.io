# Unit-Test-Tutorial mit Karma und NX Angular

Dieses Tutorial erklärt, wie du Unit-Tests in einem NX Angular-Projekt mit Karma verwendest. Es umfasst praktische Beispiele und Aufgaben, um sicherzustellen, dass du das Gelernte direkt anwenden kannst.

---

## Abschnitt 1: Einführung in Unit-Tests

Unit-Tests sind automatisierte Tests, die einzelne Einheiten einer Anwendung – wie Funktionen, Methoden oder Klassen – isoliert prüfen. Ziel ist es, sicherzustellen, dass diese Einheiten korrekt funktionieren.

**Warum Unit-Tests?**
- Verbesserte Code-Qualität.
- Schnelleres Finden von Fehlern.
- Dokumentation des erwarteten Verhaltens.
- Einfachere Wartung und Refaktorierung.

### Aufgabe 1: Erste Schritte mit Unit-Tests

1. Lies die Dokumentation zu Karma und Jasmine.
2. Überlege dir, welche Teile deiner Anwendung besonders wichtig für Tests sind.
3. Erstelle eine Liste mit Funktionen oder Komponenten, die du testen möchtest.

---

## Abschnitt 2: Grundlagen von Unit-Tests

Unit-Tests überprüfen einzelne Funktionen oder Komponenten unabhängig von ihrer Umgebung.

### Beispiel: Einfache Komponententests

Die Datei `app.component.spec.ts` könnte so aussehen:

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { AppComponent } from './app.component';

describe('AppComponent', () => {
  let component: AppComponent;
  let fixture: ComponentFixture<AppComponent>;

  beforeEach(async () => {
    await TestBed.configureTestingModule({
      declarations: [AppComponent],
    }).compileComponents();

    fixture = TestBed.createComponent(AppComponent);
    component = fixture.componentInstance;
  });

  it('should create the component', () => {
    expect(component).toBeTruthy();
  });

  it('should have title "my-app"', () => {
    expect(component.title).toBe('my-app');
  });
});
```

### Aufgabe 2: Test hinzufügen

Erweitere den obigen Test, um sicherzustellen, dass der Titel in der DOM korrekt gerendert wird.

**Hinweis:** Nutze `fixture.nativeElement.querySelector`.

---

## Abschnitt 3: Mocking von Services

Oft benötigen Komponenten externe Services. Diese sollten im Unit-Test gemockt werden.

### Beispiel:

```typescript
import { TestBed } from '@angular/core/testing';
import { MyService } from './my.service';
import { MyComponent } from './my.component';

class MockMyService {
  getValue() {
    return 'mock value';
  }
}

describe('MyComponent', () => {
  let component: MyComponent;

  beforeEach(() => {
    TestBed.configureTestingModule({
      declarations: [MyComponent],
      providers: [
        { provide: MyService, useClass: MockMyService },
      ],
    });
    component = TestBed.createComponent(MyComponent).componentInstance;
  });

  it('should use the mocked service', () => {
    expect(component.getValue()).toBe('mock value');
  });
});
```

### Aufgabe 3: Mock hinzufügen

Erstelle eine Komponente mit einem Service, der eine HTTP-Anfrage ausführt. Mocke den Service im Test und stelle sicher, dass die Komponente den Mockwert verwendet.

---

## Abschnitt 4: Arbeiten mit asynchronen Tests

Asynchrone Funktionen wie HTTP-Aufrufe oder Timers benötigen spezielle Behandlung im Test.

### Beispiel:

```typescript
import { fakeAsync, tick } from '@angular/core/testing';

describe('AsyncFunction', () => {
  it('should resolve after a delay', fakeAsync(() => {
    let value = false;

    setTimeout(() => {
      value = true;
    }, 1000);

    tick(1000);
    expect(value).toBeTrue();
  }));
});
```

### Aufgabe 4: Test für asynchrone Funktion

Schreibe eine Funktion, die einen Promise zurückgibt, und teste sie mit `async/await` und `fakeAsync`.

---

## Abschnitt 5: Herausforderung - Komplexe Komponententests

### Aufgabe 5: Komplexe Interaktionen testen

1. Erstelle eine Komponente mit einem Formular (z. B. ein Login-Formular).
2. Implementiere Tests, um sicherzustellen, dass:
   - Die Eingaben validiert werden.
   - Eine Erfolgs- oder Fehlermeldung angezeigt wird.

**Hinweis:** Nutze `spyOn` für Mocking und Überprüfung von Methoden.

---

## Abschnitt 6: RxJS Pipes testen

RxJS wird oft verwendet, um asynchrone Datenströme zu verarbeiten. Pipes können individuell getestet werden, um sicherzustellen, dass sie korrekt funktionieren.

### Beispiel:

```typescript
import { of } from 'rxjs';
import { map } from 'rxjs/operators';

describe('RxJS Pipe', () => {
  it('should map values correctly', (done) => {
    const source$ = of(1, 2, 3);
    const result$ = source$.pipe(map((value) => value * 2));

    result$.subscribe({
      next: (value) => {
        expect([2, 4, 6]).toContain(value);
      },
      complete: done,
    });
  });
});
```

### Aufgabe 6: Eigene Pipe testen

1. Schreibe eine RxJS-Pipe, die alle ungeraden Zahlen filtert und die verbleibenden quadriert.
2. Schreibe einen Test, der überprüft, ob die Pipe korrekt funktioniert.

---

## Abschnitt 7: Angular Signals testen

Angular Signals bieten eine reaktive Möglichkeit, Datenänderungen zu verfolgen. Sie können mit Unit-Tests überprüft werden.

### Beispiel:

```typescript
import { signal } from '@angular/core';

describe('Angular Signals', () => {
  it('should react to changes', () => {
    const count = signal(0);

    count.set(5);
    expect(count()).toBe(5);

    count.update((value) => value + 1);
    expect(count()).toBe(6);
  });
});
```

### Aufgabe 7: Signal-Test

1. Implementiere ein Signal, das einen Zähler darstellt.
2. Schreibe Tests, um sicherzustellen, dass:
   - Der Zähler initial den Wert 0 hat.
   - Der Wert bei einem Update korrekt erhöht wird.
