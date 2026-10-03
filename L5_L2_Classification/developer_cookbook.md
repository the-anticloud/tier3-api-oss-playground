# Developer Cookbook — api-oss-playground
**Stack:** Python 3.11, FastAPI, HTMX, PAX 27B, AIOSS_FORMAT
**Domain:** Interactive sovereign playground: test PAX 27B queries in a local web UI
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```bash
# Start playground
python -m api_oss_playground --model ./pax-27b-q4.gguf --port 8082 --aioss ./playground.aioss
# Open http://localhost:8082
# Test clinical query: 'What drug interactions should I check for metformin?'
# PAX responds with HIPAA-safe clinical reasoning
# Chain hash displayed in UI: 8b4a8a4f...
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every api-oss-playground output:
chain_hash = aioss_append("./api_oss_playground.aioss",
                           result_bytes, "api-oss-playground")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all api-oss-playground operations are logged to api-oss-logging and audited by api-oss-compliance.
