

## Make jar file for module course
Compile
```bash
javac -d mods/course \
course/src/module-info.java \
course/src/com/enthu/course/Course.java
```

Make jar in mlib
```bash
mkdir -p mlib
jar -c -f mlib/course.jar -C mods/course .
```



## Make jar file for module training
Compile
```bash
javac -d mods/training \
--module-path mods/course \
training/src/module-info.java \
training/src/com/enthu/training/StartGui.java
```

Make jar in mlib
```bash
jar -c -f mlib/training.jar \
    -C mods/training .
```

How to run
```bash
java --module-path mlib/course.jar:mlib/training.jar --module enthu.training/com.enthu.training.StartGui
```