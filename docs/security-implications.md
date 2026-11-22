# Security Implications

## What the Lab Proves

The lab demonstrates a collision property:

```text
Input A ≠ Input B
but
MD5(Input A) = MD5(Input B)
```

This violates the collision-resistance property expected from a modern cryptographic hash function.

## Why Collision Resistance Matters

Collision resistance is important when a digest is expected to uniquely bind data to a fingerprint.

Examples of systems that may depend on strong collision resistance include:

- integrity verification;
- signed data structures;
- certificate-related designs;
- artifact identification;
- software distribution workflows.

The actual risk depends on the protocol and how the digest is used.

## What the Lab Does Not Prove

This experiment does not mean:

- every MD5 use automatically creates the same exploit path;
- a hash collision is the same thing as recovering a password;
- MD5 is encryption;
- collision generation automatically allows arbitrary control over both files.

Those are separate concepts.

## Practical Security Lesson

When designing a modern security control that depends on collision resistance, use a contemporary cryptographic hash appropriate for that purpose rather than MD5.

The lab is useful because it turns an abstract cryptographic weakness into a directly observable result.
