## How to run the scenario
Clone the repository:
```
git clone add_link
cd folder
```
Build the image
```
docker compose build basestation
```
RUn the container
```
docker compose up -d basestation
```
## Starting VS Code into the Container
Install the extension [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers), and after installed access it in VS Code bar and select the option `Dev Containers` in the Remote Explorer. Your container will be shown in the list, so you just have to open it into another window.

## Debugging using VS Code into the container
Once you are using the VS Code inside the container, you can press F5 to start the debug process. You can take a look at `.vscode/launch.json` for more debugger configurations. If you set a breakpoint in the basestation code (in a code that executes without a UE connected), you will able to see the break point.

It is important to emphasize that the communication usually has 2 or more elements (1 BS and multiple UEs), so in this case we are debugging only the basestation. After pressing F5 the terminal will show the basestation log.

In case you want to connect a UE to the basestation, you can open another terminal into the docker container and execute the following code into `/home/openairinterface5g`

`./cmake_targets/ran_build/build/nr-uesoftmodem -r 106 --numerology 1 --band 78 -C 3619200000 --rfsim --sa --uicc0.imsi 001010000000001 --rfsimulator.serveraddr 127.0.0.1`
