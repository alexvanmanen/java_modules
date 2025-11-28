# Java Modules Project

# Java Modules Oefenproject

Dit project demonstreert de basisprincipes van het Java Module System (JPMS). Het is opgezet als een praktische oefening om te leren hoe je modules definieert, compileert, verpakt en uitvoert.

Dit project is specifiek nuttig voor:
*   Ontwikkelaars die de basis van `module-info.java` willen begrijpen.
*   Kandidaten die zich voorbereiden op het **Java OCP-examen**.
*   Het bestuderen van de werking achter module-dependencies (requires/exports).

*De code is een uitwerking van vraag **2.3022** uit het Enthuware examensysteem.*

## Projectstructuur

Het project bestaat uit twee afzonderlijke modules:

1.  **`course`**: Een bibliotheek-module die de domeinklasse `Course` bevat en exporteert.
2.  **`training`**: De applicatie-module die afhankelijk is van `course`. Deze bevat de `StartGui` klasse om de applicatie te starten.

---

# Instructies

## 1. Maak de module course

### 1.1 Compileer de java code voor de course module
```bash
javac -d mods/course \
course/src/module-info.java \
course/src/com/enthu/course/Course.java
```

### 1.2 Maak een jar file en zet het in de map mlib
```bash
mkdir -p mlib
jar -c -f mlib/course.jar -C mods/course .
```



## 2 Maak de module training

### 2.1 Compileer de java code voor de training module
```bash
javac -d mods/training \
--module-path mods/course \
training/src/module-info.java \
training/src/com/enthu/training/StartGui.java
```

### 2.2 Maak een jar file en zet het in de map mlib
```bash
jar -c -f mlib/training.jar \
    -C mods/training .
```

## 3. Voer de applicatie uit

## 3.1 Voer de applicatie uit met de volgende opdrachten
Linux/MacOSX
```bash
java --module-path mlib/course.jar:mlib/training.jar --module enthu.training/com.enthu.training.StartGui
```

Windows
```bash
java --module-path mlib/course.jar:mlib/training.jar --module enthu.training/com.enthu.training.StartGui
```
