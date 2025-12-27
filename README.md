# TpDevops2

This project was developed as part of an academic exam.
The main objective was to correctly configure testing with Spring Boot 3, JUnit 5, and Cucumber, resolve compatibility issues, and achieve 91% test coverage.


Testing Stack 
Java 21
Spring Boot 3
JUnit 5 (JUnit Platform)
Cucumber (BDD)
H2 Database (tests)
Maven
For Cucumber : 

🚧 Issues Encountered & Solutions
1️⃣ JUnit 4 Incompatibility with Spring Boot 3

The initial configuration used JUnit 4, which is no longer supported by Spring Boot 3.
Spring Boot 3 works only with JUnit 5
JUnit 4 runners (@RunWith) are deprecated
✅ Solution
All tests were migrated to JUnit 5, and JUnit 4 dependencies were removed.
Spring Boot 3 → JUnit 5

Cucumber Not Discovered by JUnit 5
Cucumber tests were not executed and produced the following error:
TestEngine with ID 'cucumber' failed to discover tests


This happened because JUnit 5 cannot run Cucumber tests without a dedicated engine.

✅ Solution
The Cucumber JUnit Platform Engine was added to the project.
This allows JUnit 5 to detect and execute .feature files correctly.

@Cucumber
public class RunCucumberTest {
}

For SonarCloud :
🚧 Issues Encountered
1️⃣ Maven Sonar Plugin Not Found

Error examples:

No plugin found for prefix 'sonar'
Could not find artifact sonar-maven-plugin

✅ Solutions Implemented
✔ Switched to Official & Supported Action
Replaced deprecated action with:
SonarSource/sonarqube-scan-action@v5.0.0


2️⃣ Deprecated SonarCloud GitHub Action
Warning:
This action is deprecated and will be removed in a future release

✅ Solutions Implemented
sonar.projectKey
sonar.organization
sonar.host.url

4️⃣ Java Binaries Not Found
Error:
Your project contains .java files, please provide compiled classes

✅ Solutions Implemented
sonar.java.binaries=target/classes



