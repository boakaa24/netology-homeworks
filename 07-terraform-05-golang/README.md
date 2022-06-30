1.
```
root@ubuntu-home:~# go version
go version go1.18.1 linux/amd64
```
3.
```
package main
  import "fmt"
  func main() {
    var foot float64
      fmt.Print("Type foot: ")
      fmt.Scanf("%f", &foot)           
      result := foot * 0.3048 
      fmt.Println("Meters:", result )
        }
```
```
root@ubuntu-home:~# go run test1.go
Type foot: 50
Meters: 15.24
```
4.
