# Collision Verification Method

The lab verified the collision using multiple independent checks.

## 1. Same MD5 Digest

```bash
md5sum alka1.bin alka2.bin
```

Expected property:

```text
MD5(alka1.bin) = MD5(alka2.bin)
```

## 2. Different File Content

```bash
cmp alka1.bin alka2.bin
diff alka1.bin alka2.bin
```

Expected property:

```text
alka1.bin ≠ alka2.bin
```

## 3. Shared Prefix

```bash
strings alka1.bin | grep Khaled
strings alka2.bin | grep Khaled
```

Both generated files preserve the chosen prefix.

## 4. Binary Inspection

```bash
xxd alka1.bin > alka1.hex
xxd alka2.bin > alka2.hex
diff alka1.hex alka2.hex
```

This makes the differing binary regions inspectable.

## Verification Logic

```text
Same hash
   +
Different binary content
   =
Confirmed collision
```

A matching digest without proving different inputs would not demonstrate a collision.
