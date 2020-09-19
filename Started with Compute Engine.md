# LAB1: Google Cloud Fundamentals: Getting Started with Compute Engine
### OBJECTIVES:
1.  Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

2. Create a Compute Engine virtual machine using the gcloud command-line interface.

3. Connect between the two instances.

### STEPS:
1. Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

        gcloud compute instances create my-vm-1 --zone=us-central1-a --machine-type="n1-standard-1" --image-project=debian-cloud --subnet=default --tags=http --image=debian-9-stretch-v20200902 

        gcloud compute firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server


2. Create a Compute Engine virtual machine using the gcloud command-line interface.
- Change the default zone
        gcloud config set compute/zone us-central1-b

- Create a second VM Instance 'my-vm-2' in the new zone
        gcloud compute instances create "my-vm-2" --machine-type="n1-standard-1" --image-project="debian-cloud" --image="debian-9-stretch-v20190213" --subnet "default"

3. Connect between the two instances.
-  Use the ping command to confirm that my-vm-2 can reach my-vm-1 over the network
- - SSH into my-vm-2
         gcloud compute ssh my-vm-2
- - Ping my-vm-1 from my-vm-2
         ping -c 4 my-vm-1    # this will ping the VM instance only 4 times and exit
- Use the ssh command to open a command prompt on my-vm-1:
         ssh my-vm-1   # If you are prompted about whether you want to continue connecting to a host with unknown authenticity, enter yes to confirm that you do.

- At the command prompt on my-vm-1, install the Nginx web server:
         sudo apt-get install nginx-light -y   
- Use the nano text editor to add a custom message to the home page of the web server:
         sudo nano /var/www/html/index.nginx-debian.html   
- Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this, and replace YOUR_NAME with your name or any other name or message you would like to show:
         Hi from YOUR_NAME
- - Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the nano text editor.
- Confirm that the web server is serving your new page. At the command prompt on my-vm-1, execute this command:
         curl http://localhost/
- - The response
##### The response will be the HTML source of the web server's home page, including your line of custom text. 
- Exit my-vm-1 and return to the command prompt on my-vm-2 by typing the command:
         exit
- To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, execute this command:
         curl http://my-vm-1/
- - The response 
##### The response will again be the HTML source of the web server's home page, including your line of custom text.
- Get the external IP of the my-vm-1 instance using this  command:
         gcloud compute instances list --zone uscentral1-a
- Finally, Paste the external IP address copied in a new browser and send
- - You will see a web server's home page showing your custom text
    