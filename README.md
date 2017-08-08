# Initialize a new GCE machine for data science use
This script automates installation and set-up of a GCE VM, installs a GUI desktop and Rstudio server. The script is designed to be compatible with users on remote ChromeOS systems, so inital authentication involves a guided interactive auth login step. All other GCE, desktop and Rstudio setup is automated.

Google Cloud Platform is a very flexible computing platform. However, automating start-up of a Google Compute Engine instance, set up credentials and make various services (i.e. Google Storage or BigQuery) coordinate properly can be time consuming. These tasks can also have a steep learning curve and be difficult for beginners to learn. This script aims to simplify instanstiation of GCE VMs and set-up of related services. It creates necessary firewall rules, installs Rstudio, and creates a buckets for general storage and R based data science projects. Additionally, as learning to use commands in a bash terminal can have a steep learning curve, it also installs one of several GUI desktops (i.e. a light xfce or a heavier gnome version) to interact with the VM remotely.

# GCE Set-Up and Running Initialization Script
Start up a GCE VM as described on GCP instructions.

Completing the following options, leave everything else default. Other options might be compatible with the script, but have not been validated. Complete the following:
* Instance Name: your choice
* Zone: your choice
* Boot disk image=Ubuntu 16.04 LTS
* Access scopes=Allow full access to all Cloud APIs

After VN is running, click "connect SSH" button. In the window that pops up type:

git clone https://github.com/ctrhodes/gce-initialize.git

mkdir -p $HOME/run
mv gce-initialize/initialize_gce.sh $HOME/run
echo 'export PATH=$PATH:$HOME/run' >> ~/.bashrc
chmod 755 $HOME/run/initialize_gce.sh
initialize_gce.sh

This script was designed ot be compatable with ChromeOS which has limited SSH capabilities. As such, the easiest way to initialize Oauth with **gcloud init** is to use interactive set-up. When running gcloud init, choose something similar to the examples below:

* account: xxxxx-compute@developer.gserviceaccount.com
* project: hadoop-000
* zone: us-central1-a

