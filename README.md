# Requirements
+ [x] Dont use thirparty libraries.  
+ [x] Handle 10k connection.   
+ [ ] Support 100k request/second.  
+ [ ] Support GET/POST method (for testing only).  
+ [ ] Support multipart data in file uploading.  

# Structure

epoll_example.c -> main program (updating)  
c10k-test-client.c -> test 10k concurrency connection (updating)  

# Build
```
mkdir build && cd build
```

# How to test

## 1. Before run test

Need to setup maximum file descriptor which the program can use in both server and client side  
``` ulimit -n 10000 ``` 
## 2. Run server
```cmake ..; ./server ```
## 3. Run test
on other terminal or other computer (in same LAN with computer which run as the server) 

### For localhost itself
```
./c10k-test
```

### For other computer in same LAN
```
./c10k-test <peer-ip>
```

# Solution for each Requirements
+ Handle 10k Connection use *epoll*  
+ Support 100k request/second use Threadpool to improve performance when server response client.
+ Handle request body to handle GET/POST from client

