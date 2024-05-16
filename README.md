## Assignmnt-1 : Overview
Simulate the mining process of a block by validating and including transactions from a given set of JSON files in the `mempool` folder.

## Objective
Your goal is to write a script that:
1. Reads and validates transactions from JSON files in the `mempool` folder.
2. Constructs a block by including only valid transactions.
3. Mines the block by finding a valid hash that meets a specified difficulty target.
4. Outputs the block details to a file named `output.txt`.

## Requirements
### Input
- A folder named `mempool` containing JSON files, each representing a transaction.

### Output
- `output.txt` file with:
  - First line: Block header.
  - Second line: Serialized coinbase transaction.
  - Following lines: Transaction IDs (txids) of the mined transactions, starting with the coinbase transaction.

### Block Header Format
- **Version:** Fixed value (e.g., 1).
- **Previous Block Hash:** Use a fixed dummy value (e.g., "0000000000000000000000000000000000000000000000000000000000000000").
- **Merkle Root:** Hash of all txids concatenated.
- **Timestamp:** Current Unix timestamp.
- **Difficulty Target:** "0000ffff00000000000000000000000000000000000000000000000000000000".
- **Nonce:** Start with 0 and increment until a valid hash is found.

### Coinbase Transaction
- Use a fixed coinbase transaction with a predefined reward (e.g., 50 BTC).

### Transaction Validation
- Ensure the `value` in `prevout` is greater than the `value` in `vout`.
- Check for non-empty `txid`.

### Difficulty Target
- The block hash must be less than `0000ffff00000000000000000000000000000000000000000000000000000000`.

## Execution
- Create `run.sh` to execute your script (e.g., `python main.py`).

## Evaluation Criteria
- **Score**: Based on fees collected and block space utilized. Minimum 60 points to pass.
- **Correctness**: Properly formatted `output.txt`.
- **Code Quality**: Well-organized, commented, and follows best practices.
- **Efficiency**: Efficient processing and mining.

## Documentation
Publish a `SOLUTION.md` file with:
- **Design Approach:** Describe your block construction program approach.
- **Implementation Details:** Pseudo code, sequence of logic, algorithms, variables used.
- **Results and Performance:** Solution results and efficiency analysis.
- **Conclusion:** Insights, future improvements, and references.

## Restrictions
- **Permissible Libraries:** Use standard cryptographic and hashing libraries (e.g., secp256k1, SHA-256).

## Simplified Details

### Transaction Validation
- Validate the transactions based on simpler criteria:
  - Ensure the `value` in `prevout` is greater than the `value` in `vout`.
  - Check for non-empty `txid`.

### Block Construction
- Use a fixed coinbase transaction with a predefined reward.
- Simplify the block header to include only basic information:
  - Version
  - Previous block hash (use a fixed dummy value)
  - Merkle root (hash of all txids concatenated)
  - Timestamp
  - Difficulty target
  - Nonce (start with 0 and increment until a valid hash is found)

### Output
- Format `output.txt` to include:
  - A simple block header format.
  - A predefined coinbase transaction.
  - List of valid transaction IDs.

### Mining Algorithm
- Use a basic mining algorithm:
  - Concatenate the block header fields and transactions.
  - Hash the concatenated string.
  - Increment the nonce until the hash meets the difficulty target.

## Plagiarism Policy
- Private solutions only. No sharing with peers.
- Plagiarism results in disqualification for all involved.

## AI Usage
- Use AI tools for is stickly not allowed. We are smart enough to know who used AI tools or not.
- Use AI tools results in disqualification for all involved.

## Purpose
Gain hands-on experience with Bitcoin technicals, focusing on transaction validation and block mining. Demonstrate problem-solving skills and algorithm implementation from scratch.

## Example Transaction File
Filename: `02a1ccdb3ad68f93ebfb4edaa7822878ac3d5a1a3280e9bacd8f30190638f589.json`
```json
{
  "version": 2,
  "locktime": 0,
  "vin": [
    {
      "txid": "c10e48caeee8756d57fbce0e4f26c1d08bb9f0d4a35c2d26269682da8df04dac",
      "vout": 29,
      "prevout": {
        "scriptpubkey": "51202219ab3fa8a1d392f883d388d504e62e450e1f442fd1e61558b008fbf36f01a2",
        "value": 3618
      },
      "scriptsig": "",
      "witness": ["..."],
      "is_coinbase": false,
      "sequence": 4294967295
    }
  ],
  "vout": [
    {
      "scriptpubkey": "5120046684fb809c12ba877ea0f45803bffbf01bac6643a1c16f266d3f1096344eb6",
      "value": 546
    }
  ]
}
