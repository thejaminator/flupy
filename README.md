# Chainable

Process big data in python using method chaining built on generators.

### TL;DR
```python
from itertools import count
from chainable import chainable

# Processing an infinite sequence in constant memory
pipeline = chainable(count()) \
                .map(lambda x: x**2) \
                .filter(lambda x: x % 517 == 0) \
                .chunk(5) \
                .take(3)
          
print(next(pipeline)) # prints [0, 9, 36, 81, 144]
print(next(pipeline)) # prints [225, 324, 441, 576, 729]
print(next(pipeline)) # prints [26728900, 32341969, 38489616, 45171841, 52388644]
print(next(pipeline)) # raises StopIteration
```

## Overview
chainable implements a 'Chainable' class that enables stringing multiple methods together on a single line. All chainable methods return generators and are evaluated lazily in 'depth-first' order.

### y tho
When working with large data sets, storing intermediate results of ETL pipelines consume unnecessary memory. A depth-first generator pipline minimize the memory required to process records so the entire dataset doesn't need to fit in-memory.


## Setup

### Requirements

* Python 3.6+

### Installation

Install chainable with pip:

```sh
$ pip install git+https://github.com/olirice/chainable.git
```
