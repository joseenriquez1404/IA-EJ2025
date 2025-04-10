# Character Encodings

```python
# modules we'll use
import pandas as pd
import numpy as np

# helpful character encoding module
import charset_normalizer

# set seed for reproducibility
np.random.seed(0)
```

```python
# start with a string
before = "This is the euro symbol: €"

# check to see what datatype it is
type(before)
```

```python
# encode it to a different encoding, replacing characters that raise errors
after = before.encode("utf-8", errors="replace")

# check the type
type(after)
```