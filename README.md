# syncmap2yyle

Generics sync map
泛型的 sync map
Sync map generics
Sync map 范型版

```
go get github.com/yangyile1990/syncmap2yyle
```

demo:
```
package main

import (
	"fmt"

	"github.com/yangyile1990/syncmap2yyle"
)

func main() {
	mp := syncmap2yyle.NewMap[int, string]()

	mp.Store(1, "a")
	mp.Store(2, "b")
	mp.Store(3, "c")

	mp.Range(func(key int, value string) bool {
		fmt.Println(key, value)
		return true
	})
}
```
