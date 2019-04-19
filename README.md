statuses
========
The `Status` class represents the status of some event. It is one of
either:

- `Failed`
- `NotStarted`
- `InProgress(progress)`
- `Succeeded`

Installation
============
```bash
$ pip install statuses
```

Example
=======
```python
from typing import Iterable

from status import InProgress, Failed, NotStarted, Succeeded

class Report:
    def __init__(self: "Report"):
        self.status = NotStarted()

    def run(self: "Report", foo: str, bar: Iterable[int]):
        if foo == "badstring":
            self.status = Failed()

        for i, b in enumerate(bar):
            self.status = InProgress(i / len(bar) * 100)
            print(self.status)

        self.status = Succeeded()

r = Report()
print(r.status)
r.run("goodstring", range(10))
print(r.status)
```

Documentation
=============
Ugly looking documentation can be located at
[docs/index.html](docs/index.html).
