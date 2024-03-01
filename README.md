# syncmap2yyle

Generics sync map

泛型的 sync map

Sync map generics

Sync map 范型版

100%实现sync.Map的方法因此可以直接替换

```
go get github.com/yangyile1990/syncmap2yyle
```

demo1:
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

demo2:
```
package main

import (
	"fmt"

	"github.com/yangyile1990/syncmap2yyle"
)

type Person struct {
	Name     string
	Age      int
	HomePage string
}

func main() {
	mp := syncmap2yyle.NewMap[int, *Person]()

	mp.Store(1, &Person{
		Name:     "Kratos",
		HomePage: "https://go-kratos.dev/",
	})
	mp.Store(2, &Person{
		Name: "YangYiLe",
		Age:  18,
	})
	mp.Store(3, &Person{
		Name: "DiLiReBa",
		Age:  18,
	})

	mp.Delete(3)

	mp.Range(func(key int, value *Person) bool {
		fmt.Println(key, value.Name, value.Age, value.HomePage)
		return true
	})
}
```
