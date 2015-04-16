test_speed:
	g++ main.cpp database.cpp -lyaml-cpp -ldl -o test_speed --std=c++11 -lpthread -O2\
		-I/usr/local/Cellar/yaml-cpp/0.5.1/include/ \
		-I/usr/local/Cellar/boost/1.56.0/include/ \
		-L/usr/local/Cellar/yaml-cpp/0.5.1/lib/ \
		-L/usr/local/Cellar/boost/1.56.0/lib/

test_uni:
	@echo "Testing uniform"
	rm -rf ./mydbpath
	./test_speed ../workloads/workload.uni
	diff ../workloads/workload.uni.out ../workloads/workload.uni.out.yours

test_old:
	@echo "Testing oldest"
	rm -rf ./mydbpath
	./test_speed ../workloads/workload.old
	diff ../workloads/workload.old.out ../workloads/workload.old.out.yours

test_lat:
	@echo "Testing latest"
	rm -rf ./mydbpath
	./test_speed ../workloads/workload.lat
	diff ../workloads/workload.lat.out ../workloads/workload.lat.out.yours

test_rwd:
	@echo "Testing delete"
	rm -rf ./mydbpath
	./test_speed ../workloads/rwd-workloads
	diff ../workloads/rwd-workloads.out ../workloads/rwd-workloads.out.yours

clean:
	rm test_speed
	rm -f ../workloads/*.out.yours

test1: test_speed test_uni
test2: test1 test_old
test3: test2 test_lat

test: test3 test_rwd
all: test_speed

.PHONY: test_uni test_old test_lat test_rwd test1 test2 test3 test4 clean
