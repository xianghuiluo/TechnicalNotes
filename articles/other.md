# Misc



* Python pkgs
> sudo apt install python3-all-dev\
> sudo apt install python3-pip\
> pip3 install numpy scipy matplotlib scikit-learn scikit-image jupyterlab\
> pip3 install virtualenv virtualenvwrapper\
> pip3 install testresources\
> To fix pip: sudo python3 -m pip uninstall pip


* 
```python
mat = np.loadtxt(filename, dtype=float, delimiter=',')
np.savetxt("data.csv", A, delimiter=',')
```

* 
```
g++ -ggdb test-opencv.cpp `pkg-config --cflags --libs opencv`
```

* 
```C++
cv_mat.at<cv::Vec<float, 3>>(row, col);

cv::Rect ROI(col, row, width, height);
cv::Mat ROI_img = image(ROI);
```

* disk devices info
```bash
sudo fdisk -l
```

* Installation and use of LabelMe
```bash
sudo apt install python3-pyqt5
pip3 install labelme
labelme image.jpg --nodata
```

* 
> stdbuf -o 0 [command] | tee log.txt\
> stdbuf -o 0 [command] >  >(tee -a log.txt) 2>  >(tee -a log.txt >& 2)

* 
```C++
std::string::size_type idx;
idx = s.find("substring");
if (idx == std::string::npos) { ... }
```


* Install shared library
> ldconfig [path]

* ffmpeg
> ffmpeg -framerate 5 -pattern_type glob -i "obstacle*.png" -vcodec mpeg4 output.mp4\
> ffmpeg -i a.mp4 -r 25 -vf scale=512:-1 -ss 00:00:00 -to 00:00:05 b.gif

* Install TensorFlow
> python3 -m pip install -U pip\
> python3 -m pip install -U tensorflow

* OpenCV mat to and from csv files
```C++
std::ofstream outfile("a.csv")
outfile << cv::format(mat, cv::Formatter::FMT_CSV);
outfile.close();
```
```C++
cv::Ptr<cv::ml::TrainData> raw_data = cv::ml::TrainData::loadFromCSV("a.csv", 0, -2, 0);
cv::Mat mat = raw_data->getSamples();
```

* C++ random number
```C++
#include <random>
std::default_random_engine RandomEngine;
std::uniform_int_distribution<int> UniformIntDistribution(0,10);
int random_number = UniformIntDistribution(RandomEngine);
```

* C++ unix time
```C++
double now = std::chrono::duration_cast<std::chrono::milliseconds>(std::chrono::system_clock::now().time_since_epoch()).count()/1000.0;
```

* C timing
```C
#include <time.h>
clock_t begin = clock();
...
...
...
clock_t end = clock();
double duration = (double)((end - begin)/CLOCKS_PER_SEC);
```


* Mbps test
> iperf -s\
> iperf -c <IP> -t 60

* Configure IP
> sudo ifconfig enp0s 192.168.1.100

* Ubuntu Pkg management
> sudo dpkg --list \*imager\*\
> sudo apt remove rpi-imager

* cp with progress
> rsync -r --progress src dest\
> rsync -r --info=progress2 src dest

* combine files
> cat a.zip.* > a.zip

* zip
> zip zipname file1 file2 ... fileN\
> unzip zipname -d dir

* tcpdump
> tcpdump src \<IP> -w file.pcap
  
* grep
> grep pattern file\
> grep -lr pattern dir

* md5
> md5sum \<file>

* Rotation
```C++
#include <Eigen/Geometry>

double RotationAngle = M_PI/2;
Eigen::Vector3d RotationAxis(0, 1, 0);
Eigen::AngleAxisd Rotation(RotationAngle, RotationAxis);
Eigen::Quaterniond RotationQuaternion{Rotation};
Eigen::Matrix3d RotationMatrix = RotationQuaternion.normalized().toRotationMatrix();

std::cout << "Rotation Matrix: " << std::endl << RotationMatrix << std::endl;

Eigen::Quaterniond RotationQuaternion2{Eigen::AngleAxisd(M_PI/2, Eigen::Vector3d{1,0,0})};
RotationQuaternion = RotationQuaternion * RotationQuaternion2;
RotationMatrix = RotationQuaternion.normalized().toRotationMatrix();

std::cout << "Rotation Matrix: " << std::endl << RotationMatrix << std::endl;

Eigen::Vector3d A(0,0,1);
Eigen::Vector3d B(-1,0,0);
RotationQuaternion.setFromTwoVectors(B, A);
RotationMatrix = RotationQuaternion.normalized().toRotationMatrix();

std::cout << "Rotation Matrix: " << std::endl << RotationMatrix << std::endl;
```
  
* File transfer with netcat
> Receiver side: netcat -l 4444 > myfile.txt\
> Sender side: netcat \<receiver IP> 4444 < thefile.txt

[Back to Contents](../README.md)
