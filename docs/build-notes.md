# Build Notes

## Initial Build

```bash
g++ -O2 -o fastcoll *.cpp -lboost_program_options
```

The initial build failed because the required Boost development headers were missing.

## Dependencies

```bash
sudo apt update
sudo apt install g++ libboost-all-dev
```

## Compatibility Issue

A second build problem appeared because the source expected deprecated Boost timer behavior.

The successful build used:

```bash
g++ -O2 \
  -DBOOST_TIMER_ENABLE_DEPRECATED \
  -o fastcoll *.cpp \
  -lboost_program_options \
  -lboost_filesystem
```

## Verification

```bash
./fastcoll -h
```

The help output confirmed that the binary was functional.

## Troubleshooting Lesson

The useful engineering pattern was:

```text
Read compiler error
      ↓
Identify missing dependency
      ↓
Install dependency
      ↓
Recompile
      ↓
Read new compatibility error
      ↓
Adjust build flags / linking
      ↓
Verify executable
```

The first error was not treated as a reason to switch tools. It became part of the lab.
