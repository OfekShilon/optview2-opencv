# optview2-opencv
Results of OptView2 analysis over OpenCV. The c++ compiler used was clang12, the OpenCV repo was cloned on March 27 2022.


The exact bash commands used to generate on Ubuntu20 (full build instructions are [here](https://linuxize.com/post/how-to-install-opencv-on-ubuntu-18-04/#install-opencv-from-the-ubuntu-repository)):

```bash
$ git clone git@github.com:opencv/opencv.git
$ git clone git@github.com:OfekShilon/optview2.git
$ # If you don't have ssh configured on github, replace `git@` with `https://`
$ cd opencv
$ export CXX=clang++-12
$ export CXXLD=clang++-12
$ export CMAKE_C_COMPILER=clang-12
$ export CMAKE_CXX_COMPILER=clang++-12
$ export CXXFLAGS="-fsave-optimization-record"
$ mkdir build 
$ cd build
$ cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D INSTALL_C_EXAMPLES=OFF -D INSTALL_PYTHON_EXAMPLES=OFF -D OPENCV_GENERATE_PKGCONFIG=OFF -D BUILD_EXAMPLES=OFF ..
$ make -j10
$ # optionally: make test

$ # Analyze only the 'modules' subdirectory, and split it to subfolders to make memory requirements feasible:
$ ../../optview2/opt-viewer.py -j10 --split-top-folders --output-dir ~/html/opencv99 --source-dir .. ./modules
```

OpenCV is a large project, so to avoid overburdening both the generation script and the displaying browsers - the html generation was limited to `modules` (that's where the meat is anyway) and separated by subfolders.  This creates some duplicity (common headers' source is rendered into html multiple times) but makes the load bearable.

Links to the separate folder index.html as github-pages:

- [https://ofekshilon.github.io/optview2-opencv/calib3d/](https://ofekshilon.github.io/optview2-opencv/calib3d/)
- [https://ofekshilon.github.io/optview2-opencv/core/](https://ofekshilon.github.io/optview2-opencv/core/)
- [https://ofekshilon.github.io/optview2-opencv/dnn/](https://ofekshilon.github.io/optview2-opencv/dnn/)
- [https://ofekshilon.github.io/optview2-opencv/features2d/](https://ofekshilon.github.io/optview2-opencv/features2d/)
- [https://ofekshilon.github.io/optview2-opencv/flann/](https://ofekshilon.github.io/optview2-opencv/flann/)
- [https://ofekshilon.github.io/optview2-opencv/gapi/](https://ofekshilon.github.io/optview2-opencv/gapi/)
- [https://ofekshilon.github.io/optview2-opencv/highgui/](https://ofekshilon.github.io/optview2-opencv/highgui/)
- [https://ofekshilon.github.io/optview2-opencv/imgcodecs/](https://ofekshilon.github.io/optview2-opencv/imgcodecs/)
- [https://ofekshilon.github.io/optview2-opencv/imgproc/](https://ofekshilon.github.io/optview2-opencv/imgproc/)
- [https://ofekshilon.github.io/optview2-opencv/ml/](https://ofekshilon.github.io/optview2-opencv/ml/)
- [https://ofekshilon.github.io/optview2-opencv/objdetect/](https://ofekshilon.github.io/optview2-opencv/objdetect/)
- [https://ofekshilon.github.io/optview2-opencv/photo/](https://ofekshilon.github.io/optview2-opencv/photo/)
- [https://ofekshilon.github.io/optview2-opencv/stitching/](https://ofekshilon.github.io/optview2-opencv/stitching/)
- [https://ofekshilon.github.io/optview2-opencv/ts/](https://ofekshilon.github.io/optview2-opencv/ts/)
- [https://ofekshilon.github.io/optview2-opencv/video/](https://ofekshilon.github.io/optview2-opencv/video/)
- [https://ofekshilon.github.io/optview2-opencv/videoio/](https://ofekshilon.github.io/optview2-opencv/videoio/)
