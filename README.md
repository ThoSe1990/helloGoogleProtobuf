# Hello Protobuffer Sample

Sample project from google to run protobuf in c++ with addressbook sample. 
  
## Download And Build Google Protobuf

Download google protobuf for cpp [here](https://github.com/protocolbuffers/protobuf/releases/latest)
__Note: Downlaod the protobuf-cpp.x.x.x.zip not protobuf-all.x.x.x.zip__
  
Extract protbuf directory in the same directory as this folder is (or adjust the paths for linking libraries and include directories in CMakeList.txt)  
  
__Build Protobuf:__
````
cd ./<PROTOBUF DIR>/cmake
mkdir build
cd build
cmake .. -G "Unix Makefiles" -Dprotobuf_BUILD_TESTS=OFF
make
````

__Creating Protobuf Classes:__
````
cd ./helloprotobuffer/protobuf_files
..\..\protobuf\cmake\build\protoc.exe --proto_path=..\..\protobuf\src --proto_path=..\..\protobuf\examples addressbook.proto --cpp_out=.\
````
  
Directory with protoc.exe can also be added to `$PATH`... 
Corresponding `addressbook.pb.cc` and `addressbook.pb.h` Files in this directory are created.
  


## Build hello protobuf
Build two executables, one for reading protobuf, one for writing protobuf: 
````
cd ./helloprotobuf
mkdir build
cd build
cmake .. -G "Unix Makefiles"
make
````

__Write:__
````
.\protobuf_write.exe mySample
  
mySample: File not found.  Creating a new file.
Enter person ID number: 12
Enter name: Thomas
Enter email address (blank for none): thomas@me.com
Enter a phone number (or leave blank to finish): 123456
Is this a mobile, home, or work phone? mobile
Enter a phone number (or leave blank to finish):
````
  
__Read:__
````
.\protobuf_read.exe mySample 
  
Person ID: 12
  Name: Thomas
  E-mail address: thomas@me.com
  Mobile phone #: 123456
  Updated: 2020-04-06T14:52:49Z
````
