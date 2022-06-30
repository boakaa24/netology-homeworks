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
```
package main

import "fmt"

func main() {
	x := []int{48, 96, 86, 68, 57, 82, 63, 70, 37, 34, 83, 27, 19, 97, 9, 17}
	zero := 0
	for i, less := range x {
		if i == 0 {
			zero = less
		} else {
			if less < zero {
				zero = less
			}
		}
	}
	fmt.Println("Min integer: ", zero)
}
```
```
root@ubuntu-home:~# go run test2.go
Min integer:  9
```
