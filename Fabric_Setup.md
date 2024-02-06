# Fabric Setup

Labs for Telcom 2310  will use the Fabric testbed:
[https://portal.fabric-testbed.net/](https://portal.fabric-testbed.net/)

## Registering

**Important:** Accounts must be approved by a Fabric admin, which can
take a day or two. Please register **as soon as possible** to ensure
your account is ready before the first lab.

Follow the instructions here:
[https://learn.fabric-testbed.net/knowledge-base/signing-up-for-a-fabric-account/](https://learn.fabric-testbed.net/knowledge-base/signing-up-for-a-fabric-account/)

You should use your Pitt institutional login to register your account.

## Generating SSH Keys

To access Fabric VMs, you will need to generate two SSH keypairs: a
bastion key and a sliver key.

You can do this as follows:

1\. Go to
[https://portal.fabric-testbed.net/experiments#sshKeys](https://portal.fabric-testbed.net/experiments#sshKeys)

2\. Select the \"Bastion\" tab

3\. Under \"Name\" enter \"bastion_key\" (without quotes).

4\. Under \"Description\" enter a description of the key's purpose. It is fine to just enter \"bastion_key\" here again.

5\. Click the \"Generate\" button

6\. Download **both** the public and private keys. The private key will
be named \"bastion_key\", and the corresponding public key will be named
\"bastion_key.pub\". Be sure to save these somewhere on your computer
that you will be able to find them again.

7\. (**If you are using a Windows machine, you can skip this step, it will be covered in step 4-6 of next Section**)

Set the file permissions so that the private key is only readable by your user. You can do this with the command: `chmod 0600 <path-to-bastion-key>/bastion_key`. 
For example if you saved it in a telcom2310 directory on your Desktop then the command will look like: `chmod 0600 ~/Desktop/telcom2310/bastion_key`

8\. Repeat the above steps to generate the sliver key. Select the \"Sliver\" tab instead of \"Bastion\" and name the key \"fabric_sliver_key\".

## Configure Your JupyterHub Environment (configure.ipynb)

We will use Fabric\'s JupyterHub environment to reserve virtual
machines. To get to JupyterHub from the Fabric portal, you can click the
\"JupyterHub\" link. Or, you can directly go to:
[https://jupyter.fabric-testbed.net/](https://jupyter.fabric-testbed.net/)

See instructions here:
[https://learn.fabric-testbed.net/knowledge-base/creating-your-first-experiment-in-jupyter-hub/](https://learn.fabric-testbed.net/knowledge-base/creating-your-first-experiment-in-jupyter-hub/) for more details.

1\. In the file browser on the left side of the screen, you should see a
list of folders. Double-click to open the \"jupyter-examples-rel1.5.3\"
folder.

2\. Double-click on \"start-here.ipynb\"

3\. Click the \"Configure Environment\" link in the notebook (under
\"Setup Environment\")

4\. Open a new Terminal using File > New > Terminal. Create a directory called `fabric_config` using the command `mkdir ~/work/fabric_config`. Do not panic if it gives you the error "Cannot create directory: File exists", just proceed forward. 

5\. Upload the public and private bastion and fabric_sliver keys you just downloaded to the fabric_config folder. You can drag and drop or use the upload button on the left side.

6\. Change the permissions of the key files in this terminal if not done on your local computer before. Go to the already open terminal (from Step 4), navigate to fabric_config folder `cd ~/work/fabric_config`, and change the permission of private keys here - `chmod 0600 ~/work/fabric_config/bastion_key` and `chmod 0600 ~/work/fabric_config/fabric_sliver_key`

7\. Follow the instructions in the notebook, edit the specified variables and run each cell to set up your environment. Important variables to edit are - 

FABRIC_BASTION_USERNAME (use the screenshot below to find)\
FABRIC_PROJECT_ID (use the screenshot below to find)\
FABRIC_BASTION_PRIVATE_KEY_LOCATION=${HOME}/work/fabric_config/bastion_key\
FABRIC_BASTION_SSH_CONFIG_FILE=${HOME}'/work/fabric_config/ssh_config'\
FABRIC_RC_FILE=${HOME}'/work/fabric_config/fabric_rc'\
FABRIC_SLICE_PRIVATE_KEY_FILE=${HOME}/work/fabric_config/slice_key

### To find Your Username (FABRIC_BASTION_USERNAME) (Do not use the one in the image)
<img src="https://github.com/Akshay94/telcom2310-star/assets/8385908/ca982216-3c6f-4e69-a2e1-d7f944192041" alt="drawing" width="600"/>
<!-- ![user-login](https://github.com/Akshay94/telcom2310-star/assets/8385908/ca982216-3c6f-4e69-a2e1-d7f944192041)-->

### To find Project ID (FABRIC_PROJECT_ID) (Do not use the one in the image)
<img src="https://github.com/Akshay94/telcom2310-star/assets/8385908/130fc6a3-2f84-4a0a-9051-9c9bc5f1253b" alt="drawing" width="600"/>
<img src="https://github.com/Akshay94/telcom2310-star/assets/8385908/ded67914-eaf2-4d6c-bd67-bf010456d770" alt="drawing" width="600"/>


<!-- ![project-id-1](https://github.com/Akshay94/telcom2310-star/assets/8385908/130fc6a3-2f84-4a0a-9051-9c9bc5f1253b)-->
<!-- ![project-id-2](https://github.com/Akshay94/telcom2310-star/assets/8385908/ded67914-eaf2-4d6c-bd67-bf010456d770)-->


**Note:** The final cell "﻿﻿Create a Downloadable Package that Deploys SSH Tunnels" is not needed. You can skip that cell. If you do run it, you will likely get an error `cp: cannot stat ‘fabric_ssh_tunnel_tools.zip’: No such file or directory`. You may safely ignore this error; your environment is already set up.

## (Optional) Finish Configuring Your Local SSH Environment

The above instructions will allow you to reserve and SSH into Fabric VMs
from the JupyterHub. If you would like to SSH into your VMs using your
local SSH client, one more step is needed.

The \"Configure Environment\" notebook you used above will create a file
\"ssh_config\" in your JupyterHub. Download this file and save it in a
known location on your local computer. I recommend using the same
directory where you saved your SSH keys (I\'ve saved mine as
\~/.ssh/fabric_config).
