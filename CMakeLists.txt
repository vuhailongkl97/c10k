cmake_minimum_required(VERSION 3.11)
project(dtl)

add_executable(server epoll-example.c)

#find_package(Libevent CONFIG REQUIRED)
add_executable(test-c10k c10k-test-client.c)
target_link_libraries(test-c10k event)

