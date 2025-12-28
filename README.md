# LuxFHE Python SDK

**FHE for Python - Machine Learning on Encrypted Data**

[![PyPI](https://img.shields.io/pypi/v/luxfhe.svg)](https://pypi.org/project/luxfhe/)
[![License](https://img.shields.io/badge/license-Lux%20Research-blue.svg)](LICENSE)

---

## ⚠️ Important IP Notice

**This SDK uses Lux's independent FHE implementation:**

- ✅ Python bindings to `github.com/luxfi/tfhe` (our Go TFHE)
- ✅ NO Zama Concrete, concrete-ml, or tfhe-rs dependencies
- ✅ Protected by Lux Industries patent portfolio

---

## Overview

LuxFHE Python SDK enables:
- FHE operations in Python
- Machine learning on encrypted data
- Integration with NumPy and PyTorch

## Installation

```bash
pip install luxfhe
# or
uv add luxfhe
```

## Quick Start

```python
from luxfhe import LuxFHE, FheUint32

# Initialize
fhe = LuxFHE(network="testnet")

# Encrypt
secret = fhe.encrypt_uint32(42)

# Operations on encrypted data
result = fhe.add(secret, fhe.encrypt_uint32(8))

# Decrypt (requires key)
plaintext = fhe.decrypt_uint32(result)
print(f"42 + 8 = {plaintext}")  # 50
```

## ML on Encrypted Data

```python
from luxfhe.ml import EncryptedModel

# Train model on plaintext
model = train_my_model(X_train, y_train)

# Convert to FHE model
encrypted_model = EncryptedModel(model)

# Inference on encrypted input
encrypted_input = fhe.encrypt_array(X_test)
encrypted_prediction = encrypted_model.predict(encrypted_input)

# Decrypt result
prediction = fhe.decrypt_array(encrypted_prediction)
```

## Supported Operations

| Category | Operations |
|----------|------------|
| Arithmetic | add, sub, mul, div |
| Comparison | eq, lt, gt, le, ge |
| Bitwise | and, or, xor, not |
| Arrays | encrypt_array, decrypt_array |
| ML | predict, forward |

## Requirements

- Python 3.10+
- Go 1.21+ (for building bindings)

## License

**Lux Research License** - Free on Lux Network.

---

© 2020-2025 Lux Industries Inc. All rights reserved.
