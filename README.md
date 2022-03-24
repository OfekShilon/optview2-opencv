# optview2-opencv
Results of OptView2 analysis over OpenCV


The exact bash commands used to generate (full build instructions are [here](https://linuxize.com/post/how-to-install-opencv-on-ubuntu-18-04/#install-opencv-from-the-ubuntu-repository)):

```bash
$ git clone git@github.com:opencv/opencv.git
$ git clone git@github.com:OfekShilon/optview2.git
$ # If you don't have ssh configured on github, replace `git@` with `https://`
$ cd opencv
$ export CXX=clang++
$ export CXXLD=clang++
$ export CMAKE_C_COMPILER=clang
$ export CMAKE_CXX_COMPILER=clang++
$ export CXXFLAGS="-fsave-optimization-record"
$ mkdir build 
$ cd build
$ cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D INSTALL_C_EXAMPLES=OFF -D INSTALL_PYTHON_EXAMPLES=OFF -D OPENCV_GENERATE_PKGCONFIG=OFF -D BUILD_EXAMPLES=OFF ..
$ make -j10
$ # optionally: make test

$ # Analyze only the 'modules' subdirectory, and split it to subfolders to make memory requirements feasible:
$ ../../optview2/opt-viewer.py -j10 --split-top-folders --output-dir ~/html/opencv99 --source-dir .. ./modules
```
