CC=g++
AR=ar
ARFLAGS= rcs
OSTYPE := $(shell uname)

ifeq ($(OSTYPE),Linux)
	CFLAGS=-c -Wall -std=c++17 -Wunreachable-code -fopenmp
	LFLAGS=-lglfw -lGLEW -lGL -L../Utils -lutils -fopenmp
	LIBS=
	INCLUDES=-I. -I../Utils 
else
	CFLAGS=-c -Wall -std=c++17 -Wunreachable-code -Xclang -fopenmp
	LFLAGS=-lglfw -lGLEW -framework OpenGL -L../Utils -lutils
	LIBS=-lomp -L ../../openmp/lib -L /opt/homebrew/lib
	INCLUDES=-I. -I../Utils -I ../../openmp/include -I /opt/homebrew/include
endif

SRC = Image.cpp Mat3.cpp GLApp.cpp ArcBall.cpp GLTexture3D.cpp GLDebug.cpp GLFramebuffer.cpp GLDepthBuffer.cpp Grid2D.cpp GLTexture1D.cpp Vec4.cpp FontRenderer.cpp bmp.cpp PrecomputedParticleSystem.cpp PlanarMirror.cpp FresnelVisualizer.cpp GLArray.cpp ParticleSystem.cpp AbstractParticleSystem.cpp GLTexture2D.cpp Tesselation.cpp GLBuffer.cpp GLEnv.cpp GLProgram.cpp Mat4.cpp Vec3.cpp Rand.cpp OBJFile.cpp
OBJ = $(SRC:.cpp=.o)
TARGET = libutils.a

all: $(TARGET)

release: CFLAGS += -O3 -DNDEBUG
release: $(TARGET)

$(TARGET): $(OBJ)
	$(AR) $(ARFLAGS) $@ $^

%.o: %.cpp
	$(CC) $(CFLAGS) $(INCLUDES) $^ -o $@

clean:
	-rm -rf $(OBJ) $(TARGET) core

