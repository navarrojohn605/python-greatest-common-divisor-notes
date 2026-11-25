# Ordered batch processing for Compute a greatest common divisor

`batch.py` accepts an outer JSON array containing separate inputs. This is an extra level of nesting when `solve` itself accepts a list. It produces one result envelope per item, preserving input order and zero-based position.

```sh
python3 batch.py < samples/batch.json
```

The batch covers these three input/output pairs:

## Case 1

Input:
```json
[
  48,
  18
]
```

Result:
```json
6
```

## Case 2

Input:
```json
[
  -12,
  8
]
```

Result:
```json
4
```

## Case 3

Input:
```json
[
  0,
  0
]
```

Result:
```json
0
```

## Partial failures

Each successful item has `ok: true` and `result`. A failed item has `ok: false` and an exception type; later items still run. Exit status 1 means at least one item failed, while status 2 means the batch envelope itself was invalid. An empty outer array is a valid empty batch.

gcd returns a nonnegative result even for negative inputs. gcd(0, 0) is defined as zero in Python.

The implementation processes sequentially, avoiding shared-state concurrency and keeping output order predictable. Input is limited to one MiB and 1000 items; this version materializes all results in memory. The next lesson removes that whole-batch memory requirement with line-oriented processing.
