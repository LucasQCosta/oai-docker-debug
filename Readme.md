# How to run the environment
## Build the image and run container
Clone the repository:
```
git clone https://github.com/LucasQCosta/oai-docker-debug.git
cd oai-docker-debug 
```
Build the image (This step may take some time)
```
docker compose build basestation
```
Run the container
```
docker compose up -d basestation
```
## Starting VS Code into the Container
Install the extension [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers), and after installed access it in VS Code bar and select the option `Dev Containers` in the Remote Explorer. Your container will be shown in the list, so you just have to open it into another window.

## Install extensions inside the container
After entering the container, if not already installing within the container's VSCode, install these extensions:
  - Cmake Tools
  - C/C++
  - C/C++ Extension Pack
  - C/C++ Compile Run

## Debugging using VS Code into the container
Once you are using the VS Code inside the container, you can press F5 to start the debug process. You can take a look at `.vscode/launch.json` for more debugger configurations. If you set a breakpoint in the basestation code (in a code that executes without a UE connected), you will able to see the break point.

It is important to emphasize that the communication usually has 2 or more elements (1 BS and multiple UEs), so in this case we are debugging only the basestation. After pressing F5 the terminal will show the basestation log.

In case you want to connect a UE to the basestation, you can open another terminal into the docker container and execute the following code into `/home/openairinterface5g`

```
./cmake_targets/ran_build/build/nr-uesoftmodem -r 106 --numerology 1 --band 78 -C 3619200000 --rfsim --sa --uicc0.imsi 001010000000001 --rfsimulator.serveraddr 127.0.0.1
```
