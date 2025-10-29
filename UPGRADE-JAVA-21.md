Upgrade to Java 21

This repository will target Java 21.

What I changed
- Added `maven-compiler-plugin` (release 21) to `pom.xml`.
- Added `maven-enforcer-plugin` to require Java 21 or newer.

What you should do locally
1. Install a Java 21 JDK and set JAVA_HOME.
   - Windows (PowerShell):
     ```powershell
     # Example using SDKMAN (if available) or vendor installer
     # After installer: set environment variable
     setx -m JAVA_HOME "C:\path\to\jdk-21"
     $env:JAVA_HOME = 'C:\path\to\jdk-21'
     # Verify
     & "$env:JAVA_HOME\bin\java" -version
     & mvn -v
     ```
2. Verify Maven uses JDK 21:
   - `mvn -v` should show Java 21 as the runtime.
3. Build and test the project:
   - `mvn clean verify -DskipTests=false`

Notes and caveats
- Some dependencies (older Elasticsearch 7.x, older libraries) may not be fully compatible with Java 21. If you see compilation or runtime errors, update the offending dependency to a Java 21-compatible version.
- If you use an IDE, update the project's JDK to 21 in IDE settings.

Next recommended steps
- Run a full build and tests locally: `mvn -U clean verify`.
- If you want, I can also try to automatically upgrade dependencies that are known incompatible, or run more checks (static analysis, CI updates).