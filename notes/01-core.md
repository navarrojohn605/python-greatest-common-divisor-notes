# Compute a greatest common divisor: implementation

## What the example does

gcd returns a nonnegative result even for negative inputs. gcd(0, 0) is defined as zero in Python.

The public function is `solve(value)`. The JSON input contract can be seen in this concrete example:

```json
[
  48,
  18
]
```

Expected result:

```json
6
```

Run `python3 example.py` for the Python representation of the result. `solution.py` contains the full implementation and can also be imported by another script.

## Scope

The function implements exactly the behavior described above. It does not perform network or filesystem access. Python exceptions indicate unsupported input; the next lesson turns them into a command-line error response. Review the limitations before reusing it in an application.
