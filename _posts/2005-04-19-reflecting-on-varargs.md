---
id: 105
title: 'Java 1.5 Reflection: getMethod() when the method has varargs'
date: 2005-04-19T21:26:33+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=105
permalink: /reflecting-on-varargs/
categories:
  - SoftwareDev
---
**Updated May 18, 2005** Shrunk width due to narrow WP style (it's like coding in 30 columns per line)

<pre>
package assertion;

import junit.framework.TestCase;

import java.lang.reflect.Method;
import java.lang.reflect.Array;

public class ReflectionTest extends TestCase {

    private class Shop {
        public void order(String ... productIds) {}
    }

    public void testReflectingOnVarargsIs-
                            EquivalentToReflectingOn-
                            AnyArray()
                   throws NoSuchMethodException {

        Method goodMethod = Shop.class.
                  getMethod("order",
                  Array.newInstance(String.class,0).getClass());
        assertNotNull(goodMethod);

        try {
            Method badMethod = Shop.class.getMethod("order");
            fail();
        } catch (NoSuchMethodException e) {}

        try {
            Method badMethod = Shop.class.getMethod("order", String.class);
            fail();
        } catch (NoSuchMethodException e) {}

    }

}
</pre>