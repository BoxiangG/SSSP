exe = sssp

cc = "$(shell which g++)" 
#flags = -I. -fopenmp -march=athlon64 -O3
flags = -I. #-fopenmp -O3
#flags += -std=c++11

ifeq ($(debug), 1)
	flags+= -DDEBUG 
endif

objs = $(patsubst %.cpp,%.o,$(wildcard ../../lib/*.cpp))\
			$(patsubst %.cpp,%.o,$(wildcard *.cpp))

deps = $(wildcard ../../lib/*.h) \
				$(wildcard *.h) \
				Makefile

%.o:%.cu $(deps)
	$(cc) -c $< -o $@ $(flags)

$(exe):$(objs)
	$(cc) $(objs) -o $(exe) $(flags)

test:$(exe)
	./sssp /home/yuede/small_graph/dataset_sssp/begin.bin /home/yuede/small_graph/dataset_sssp/adjacent.bin /home/yuede/small_graph/dataset_sssp/weight.bin 218 

clean:
	rm -rf $(exe) $(objs) 