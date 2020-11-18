
## Files

```
src/main/groovy/org/gradle/GroovyPerson.groovy
src/main/groovy/org/gradle/JavaPerson.java
src/main/groovy/org/gradle/PersonList.groovy
src/main/java/org/gradle/Person.java
src/test/groovy/org/gradle/PersonTest.groovy
```

## Contents

```java
==> src/main/groovy/org/gradle/GroovyPerson.groovy <==
package org.gradle

class GroovyPerson implements Person {
    def String name
}

==> src/main/groovy/org/gradle/JavaPerson.java <==
package org.gradle;

public class JavaPerson extends GroovyPerson {
    public JavaPerson(String name) {
        setName(name);
    }
}

==> src/main/groovy/org/gradle/PersonList.groovy <==
package org.gradle

class PersonList {
    def find(String name) {
        new JavaPerson(name)
    }
}

==> src/main/java/org/gradle/Person.java <==
package org.gradle;

public interface Person {
    String getName();
}

==> src/test/groovy/org/gradle/PersonTest.groovy <==
package org.gradle

import org.junit.Test
import static org.junit.Assert.*

class PersonTest {
    @Test public void canConstructAJavaPerson() {
        Person p = new JavaPerson('name')
        assertEquals('name', p.name)
    }

    @Test public void canConstructAGroovyPerson() {
        Person p = new GroovyPerson(name: 'name')
        assertEquals('name', p.name)
    }
}
```
