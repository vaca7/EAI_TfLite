CC := g++
CFLAGS := -std=c++11 $(shell pkg-config --cflags opencv4)
LDFLAGS := $(shell pkg-config --libs opencv4) -pthread -ltensorflow-lite -lflatbuffers -l:libedgetpu.so.1.0 -ldl
INCLUDEPATHS := -I${HOME}/tensorflow -I${HOME}/EAI_TfLite_1 
					 
LDPATH := -L${HOME}/tensorflow/tensorflow/lite/tools/make/gen/bbb_armv7l/lib\
	  -L${HOME}/tensorflow/tensorflow/lite/tools/make/downloads/flatbuffers/build\
		-L${HOME}/EAI_TfLite_1/libs/armv7a

SRCS := tpu_latency.cc
OBJS := $(SRCS:.cc=.o)
EXEC := tpu_latency

all: $(EXEC)

$(EXEC): $(OBJS)
	$(CC) $(CFLAGS) $(INCLUDEPATHS) -o $@ $^ $(LDPATH) $(LDFLAGS)  

%.o: %.cc
	$(CC) $(CFLAGS) $(INCLUDEPATHS) -c $< -o $@   

clean : 
	rm -f $(OBJS) $(EXEC)	
