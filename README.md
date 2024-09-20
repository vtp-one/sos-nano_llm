# sos-nano_llm

An SOS System for NanoLLM.

NanoLLM is a lightweight, optimized library for LLM inference and multimodal agents.

For more information about NanoLLM: 
 - [jetson-containers/NanoLLM](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/nano_llm)
 - [dusty-nv/NanoLLM](https://github.com/dusty-nv/NanoLLM)

The SOS System version operates as a proof-of-concept for bundling pre-existing applications. 
It doesn't include any additional models or files needed to operate, it only bundles an installation process for the system.


# Requirements
 - [SOS-Toolkit](https://github.com/vtp-one/sos-toolkit)

Follow the instructions to get a working SOS-Toolkit virtual environment. 

Installation instructions assume you already have an activated virtual environment. 

All Commands in the environment are prefaced with: `(sos)$`


# Current Release Target
```
v0.24.7
```

# Install
These steps will pull, install, and run NanoLLM. 

You should start from your SOS-Toolkit root directory: `/sos` or it's equivalent in your environment

:warning: WARNING :warning:
```
A SYSTEM CAN RUN ANY TERMINAL COMMAND AND ANY ARBITRARY PYTHON CODE INCLUDING DYNAMICALLY GENERATED CODE
DO NOT INTERACT WITH SYSTEMS THAT YOU DO NOT KNOW, TRUST, OR HAVE THE CAPABILITY TO MANUALLY VERIFY THEIR OPERATION
```

### 1. Pull the sos-nano_llm repository and enter it
```
(sos)$ sos-toolkit pull https://github.com/vtp-one/sos-nano_llm.git --remote-branch v0.24.7
(sos)$ cd sos-nano_llm
```

### 2. Setup the System
```
(sos)$ sos-toolkit setup
```

### 3. Install the System
```
(sos)$ sos-toolkit install
```

### 4. Run the System
```
(sos)$ sos-toolkit up
```

This command will output a system status message with the address NanoLLM is available at:
```
{'terminal.print_object': 'NANO LLM RUNNING ON: https://X.X.X.X:XXXX'}
```
Open the address in a web browser, be sure to notice this system uses https. 
The system automatically bundles a self-signed certificate that will need to be approved in your browser.

### 5. Shutdown the System
```
(sos)$ sos-toolkit down
```


# Develop
### 1. Start with a Clean Repository
```
(sos)$ sos-toolkit pull https://github.com/vtp-one/sos-nano_llm.git
(sos)$ cd sos-nano_llm
```

### 2. Enable Dev Mode
```
(sos)$ sos-toolkit dev
```

### 3. Build the System
```
(sos)$ sos-toolkit build
```

### 4. Run the System
```
(sos)$ sos-toolkit up
```

### 5. Develop
The NanoLLM package will be installed in the systems internal directory:
```
<system path>/internal/NanoLLM
```

This directory is used in the runtime container as a volume that the NanoLLM application will be run from.
Currently this system does not support hot-reloading for changes.

In order to see changes you will need to restart the system:
```
(sos)$ sos-toolkit restart
```

### 6. Commit Changes
Currently this system does not permit changes unless you have forked the NanoLLM repository and configured the system to use your repository.

Information on how to do that is located here: [SOS-Toolkit](https://github.com/vtp-one/sos-toolkit)

You do not need to fork the SOS-nano_llm repository, you only need to fork the [dusty-nv/NanoLLM](https://github.com/dusty-nv/NanoLLM) repository and modify the system to use it.
The simple method is that you need to add the following to an sos-local.yaml file:
```
namespace:
  nano_llm:
    git_target: <YOUR_GIT_REPOSITORY_TARGET>
    branch_target: <YOUR_GIT_BRANCH_TARGET>
```
This should be done before running the setup command or any other commands.

Advanced usage can allow you to update these values directly into an already installed system. Read the documentation for information about how to do that.

While developing you may want to change to a new branch for your changes. Currently SOS-Toolkit is unable to create new branches, so you will have to do that using some other method. The repository is located in the system's internal directory, and you can directly interact with the repository using git there. 

This workflow is convoluted currently, but will be optimized in the future.


# More Information
 - [SOS-Toolkit](https://github.com/vtp-one/sos-toolkit)
 - [SOS-Test_System](https://github.com/vtp-one/sos-test_system)



# License
LICENSE WILL CHANGE

CURRENT LICENSE: VTP-LICENSE-v0.0.1

FOR APPROVED USE: POLYFORM - STRICT
