# mango-cobra

cobra adapter for [mango](https://github.com/muesli/mango).

## Example

```go
import (
	"fmt"

	mcobra "github.com/muesli/mango-cobra"
	"github.com/muesli/roff"
	"github.com/spf13/cobra"
)

var (
    rootCmd = &cobra.Command{
        Use:   "mango",
        Short: "A man-page generator",
    }
)

func main() {
    manPage, err := mcobra.NewManPage(1, rootCmd)
    if err != nil {
        panic(err)
    }

    manPage = manPage.WithSection("Copyright", "(C) 2022 Christian Muehlhaeuser.\n"+
        "Released under MIT license.")

    fmt.Println(manPage.Build(roff.NewDocument()))
}
```
