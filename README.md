# IntelliJ / ErrorProne Bug Repro

Env:

- OS X Monterey 12.3.1 (21E258)
- JDK 11 with mvn.compiler.release=8
- ErrorProne 2.13.1 (earlier versions were also affected)
- IntelliJ IDEA 2022.1 (Ultimate Edition)
  ```
  Build #IU-221.5080.210, built on April 12, 2022
  [...]
  Runtime version: 11.0.14.1+1-b2043.25 x86_64
  VM: OpenJDK 64-Bit Server VM by JetBrains s.r.o.
  macOS 12.3.1
  GC: G1 Young Generation, G1 Old Generation
  Memory: 6144M
  Cores: 12
  Non-Bundled Plugins:
  google-java-format (1.15.0.0)
  com.deadsilly.blackbird.theme (0.3.3)
  org.asciidoctor.intellij.asciidoc (0.37.17)
  org.sonarlint.idea (6.7.0.45926)
  Kotlin: 221-1.6.20-release-285-IJ5080.210
  ```


## Steps to Reproduce

- Import project
- Use JDK 11 (maven.compiler.release is 8)
- Hit Build -> Rebuild -> ❌
    ```
    /Users/ra/scratch/intellij-errorprone/src/main/java/com/example/demo/Animal.java:6:2
    java: [UnicodeInCode] Avoid using non-ASCII Unicode character (\u001a) outside of comments and literals, as they can be confusing.
    (see https://errorprone.info/bugpattern/UnicodeInCode)
    ```
- Build with JDK 11 (mvn clean install) -> ✅
