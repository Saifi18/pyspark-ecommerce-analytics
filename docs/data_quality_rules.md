| Issue                      | Example                  | Action                            | Layer  |
| -------------------------- | ------------------------ | --------------------------------- | ------ |
| Null customer ID           | `NULL`                   | Reject/quarantine                 | Silver |
| Blank customer ID          | `"   "`                  | Standardize → NULL, then validate | Silver |
| `UNKNOWN` ID               | `"UNKNOWN"`              | Standardize → NULL, then validate | Silver |
| Duplicate customer ID      | Same ID in multiple rows | Investigate/deduplicate           | Silver |
| Negative product price     | `-100`                   | Reject/quarantine                 | Silver |
| Negative stock             | `-5`                     | Reject/quarantine                 | Silver |
| Invalid customer reference | Customer doesn't exist   | Reject/quarantine                 | Silver |
| Invalid product reference  | Product doesn't exist    | Reject/quarantine                 | Silver |
| Invalid order reference    | Order doesn't exist      | Reject/quarantine                 | Silver |
| Zero quantity              | `0`                      | Reject/quarantine                 | Silver |
| Negative quantity          | `-2`                     | Reject/quarantine                 | Silver |
| Invalid status             | Unknown status           | Reject/quarantine                 | Silver |
| Missing optional coupon    | `NULL`                   | Accept                            | Silver |
