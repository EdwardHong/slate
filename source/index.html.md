---
title: MeTS Java Coding Standards

toc_footers:
  - <a href='https://github.bamtech.co/kfuhrman/coding-standards'>View on Github!</a>
  - <a href='https://github.com/lord/slate'>Powered by Slate</a>

search: true
---

# MeTS Java Coding Standards

Test content

TODO:// fill with content

# Formatting

## Imports

> Example Imports

```java
import com.bamtech.mm.mets.sfc.type.exception.FatalException;
import com.bamtech.mm.mets.sfc.type.type.ExecutionContext;
import com.dss.mm.mets.sfc.base.lambda.BaseLambda;
import com.dss.mm.vpo.type.v2.packaging.BaseMediaData;
import com.dss.mm.vpo.type.v2.preset.Preset;

import java.util.Arrays;
import java.util.HashMap;
import java.util.StringJoiner;
import java.util.stream.Collectors;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
```

In order to clearly see imports, they should be listed alphabetically with a newline between each base package name.

We should avoid wildcard imports, as they not only clutter the classpath but they can also cause confusion when reading code.

Static imports should also be avoided in production code, as they can also obfuscate code making it harder to determine where the implementation is located.

# Prefer Immutability

When things objects are immutable, it is typically easier to reason about concurrency and expected behavior. While there may be some overhead to keeping things immutable, the benefits while writing and debugging code far out weigh them.

## Final

Wherever possible fields should be declared as final to show clear design and intent. Fields which are not final should be assumed to be mutable and potentially uninitialized.

Methods and Classes should not be final with good reason, as it limits extensibility.

## Immutable classes

```java

public TestClass {

	private final String data;

	public TestClass( final String data ) {
		this.data;
	}

	public getData() {
		return data;
	}

}

```

While not always possible, it's ideal for classes to be immutable. Immutable classes tend to make design easier to understand by clearly showing intent, as well as making concurreny easier to reason about.

