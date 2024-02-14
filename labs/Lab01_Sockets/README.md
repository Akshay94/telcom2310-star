# Lab 1: Introduction to Client-Server Applications and Wide-Area Networks

## Objectives

In this lab, you will:

- Review and understand the code for simple client-server applications using TCP and UDP
- Run client-server applications over a wide-area network using the Fabric testbed
- Examine performance characteristics using an application-level “Ping” test program
<!--- Bonus: modify TCP “Ping” program to compare non-persistent vs persistent connections--->

## Prerequisites

You must have your Fabric account and JupyterHub environment setup. Please see the [Fabric Setup](https://github.com/Akshay94/telcom2310-star/blob/main/Fabric_Setup.md) for instructions.

## Running the Lab

- The lab has two Jupyter notebooks and one folder:
    - **CreateSlice.ipynb**: Creates the FABRIC slice/topology needed for this tutorial
    - **SocketLab.ipynb**: Gets slice info, uploads test programs to nodes, and contains instructions for running the lab

- To run the lab:
   - Login to the FABRIC Portal and JupyterHub
    	- Login to the [FABRIC Portal](https://portal.fabric-testbed.net/)
    	- Login/connect to the [FABRIC JupyterHub](https://learn.fabric-testbed.net/knowledge-base/creating-your-first-experiment-in-jupyter-hub/)
   - Delete the old tutorials and Download the latest copy from GitHub
    	- Open a terminal in JupyterHub by clicking the "Terminal" tile under "Other" in the Launcher tab
        - Delete the old copy of tutorials using command
            ```
            cd ~/work
            rm -rf telcom2310
            rm -rf telcom2310-star
            ```
    	- In the terminal window, type the following command to download (pull) the latest version of the set of tutorials from Github:
            ```
            git clone https://github.com/Akshay94/telcom2310-star.git
            ```

   - Run the lab notebooks
    	- In the left-hand column of JupyterHub, **navigate to the folder `telcom2310-star > Lab01_Sockets`**
    	- **Open and Execute the CreateSlice.ipynb** notebook (Just click `Run All Cells` option in menu bar)
        - If CreateSlice.ipynb does not work and gives error, **please execute the following code**, **reopen JupyterHub**, and do the previous step again:
          ```
          mv ~/work/fabric_config/requirements.txt ~/work/fabric_config/backup.requirements.txt
          touch ~/work/fabric_config/requirements.txt
          ```
        - Open and Execute the **SocketLab.ipynb**
        - Download and **fill out the Lab1.docx** worksheet as you go.
