# syncmap2yyle

Generics sync map

泛型的 sync map

Sync map generics

Sync map 范型版

This toolkit provides a comprehensive encapsulation of the methods in sync.Map, ensuring that both the parameters and return values remain unchanged. As a result, these methods can be seamlessly substituted and utilized. Moreover, the presence of generics in this toolkit eliminates the need for any conversions to interface{}, enhancing its efficiency and convenience.

该工具包100%封装sync.Map的方法且方法的参数和返回值都不变，因此可以直接替换使用，但由于具有泛型而能避免interface{}的转换

Due to the lengthy name of this account and the cumbersome package name, the code has been migrated to a new location. Going forward, the focus will be on maintaining the new package:

由于该github的名字冗长且该工具包名也冗长，因此已经将代码转移到新的地方，以后优先维护新包：
```
go get github.com/yyle88/syncmap
```
Despite the migration of the code to a new repository, it's worth noting that the old repository is still functional and available for use. While the focus will be on maintaining the new package, the option to continue using the old repository remains open:


当然旧的依然可以使用：
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

