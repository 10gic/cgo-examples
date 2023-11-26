# Examples of CGO
Examples of calling C code from Golang.

## Compile and run example
Run `make`:
```bash
$ make
make -C csrc
gcc -shared -fPIC -o libtest.so test.c
gcc -c -Wall -Werror -fPIC -o test.o test.c
ar r libtest.a test.o
ar: creating archive libtest.a
CGO_LDFLAGS='./csrc/libtest.a' go build -o main.1 main.go
CGO_LDFLAGS='-L./csrc -ltest' go build -o main.2 main.go
./main.1
add1, sum of 10 20 is 30
add2, sum of 10 20 is 30
Hello1, Gopher from 2023!
Hello2, Gopher from 2023!
10
C.low = 10
C.medium = 20
C.high = 30
1
C.LOW = 0
C.MEDIUM = 1
C.HIGH = 2
average of 10 20 is 15
average of 10 20 30 is 20
average of [1 2 3 4 5] is 3
LD_LIBRARY_PATH=./csrc DYLD_LIBRARY_PATH=./csrc ./main.2
add1, sum of 10 20 is 30
add2, sum of 10 20 is 30
Hello1, Gopher from 2023!
Hello2, Gopher from 2023!
10
C.low = 10
C.medium = 20
C.high = 30
1
C.LOW = 0
C.MEDIUM = 1
C.HIGH = 2
average of 10 20 is 15
average of 10 20 30 is 20
average of [1 2 3 4 5] is 3
```

See [Makefile](Makefile)

# Reference
https://pkg.go.dev/cmd/cgo
