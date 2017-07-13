#

### Java: signed long to unsigned long string
#### 1
``` 
/** the constant 2^64 */
private static final BigInteger TWO_64 = BigInteger.ONE.shiftLeft(64);

public String asUnsignedDecimalString(long l) {
   BigInteger b = BigInteger.valueOf(l);
   if(b.signum() < 0) {
      b = b.add(TWO_64);
   }
   return b.toString();
}
```

#### 2
```
public static String convert(long x) {
    return new BigInteger(1, new byte[] { (byte) (x >> 56),
        (byte) (x >> 48), (byte) (x >> 40), (byte) (x >> 32),
        (byte) (x >> 24), (byte) (x >> 16), (byte) (x >> 8),
        (byte) (x >> 0) }).toString();
}
```

### problem infomation
“Undefined reference: .. ConcurrentHashMap.keySet()” when building in Java 8

### reason
