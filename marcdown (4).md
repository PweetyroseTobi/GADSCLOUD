## LAB2
## Google Cloud Fundamentals: Getting Started with App Engine
### OBJECTIVES
In this lab, you learn how to perform the following tasks:

1. Initialize App Engine.

2. Preview an App Engine application running locally in Cloud Shell.

3. Deploy an App Engine application, so that others can reach it.

4. Disable an App Engine application, when you no longer want it to be visible.

### STEPS
1. Initialize App Engine using gcloud command-line tool (gcloud is the command-line tool for Google Cloud Platform. It comes pre-installed on Cloud Shell and supports tab-completion.) .
- -  List the active account name with this command:
          gcloud auth list
     output:
          Credentialed accounts:
        <myaccount>@<mydomain>.com (active) eg Credentialed accounts:
 google1623327_student@qwiklabs.net
- - List the project ID with this command:
          gcloud config list project
- - Initialize your App Engine app with your project and choose its region:
          gcloud app create --project=$DEVSHELL_PROJECT_ID
- - Clone the source code repository for a sample application in the hello_world directory:
          git clone https://github.com/GoogleCloudPlatform/python-docs-samples
- - Navigate to the source directory:
          cd python-docs-samples/appengine/standard_python3/hello_world

2. Run Hello World application locally
- Ensure that you are at the Cloud Shell command prompt.

- - Execute the following command to download and update the packages list.
           sudo apt-get update
- - Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system.
           sudo apt-get install virtualenv
      ######    If prompted [Y/n], press Y and then Enter.
           virtualenv -p python3 venv
- - Activate the virtual environment.
           source venv/bin/activate
- - Navigate to your project directory and install dependencies.
           pip install  -r requirements.txt
- - Run the application:
           python main.py
     ###### Please ignore the warning if any.
- - In Cloud Shell, click Web preview (Web Preview) > Preview on port 8080 to preview the application.
- - To end the test, return to Cloud Shell and press Ctrl+C to abort the deployed service.

- - Using the Cloud Console, verify that the app is not deployed. In the Cloud Console, on the Navigation menu (Navigation menu), click App Engine > Dashboard.
###### Notice that no resources are deployed.

3. Deploy and run Hello World on App Engine
- To deploy your application to the App Engine Standard environment:
- - Navigate to the source directory:
          cd ~/python-docs-samples/appengine/standard_python3/hello_world
- - Deploy your Hello World application:
          gcloud app deploy
###### If prompted "Do you want to continue (Y/n)?", press Y and then Enter.
###### This app deploy command uses the app.yaml file to identify project configuration.

- - Launch your browser to view the app at 
          http://YOUR_PROJECT_ID.appspot.com
          gcloud app browse
- - Copy and paste the URL into a new browser window.
 ###### RESULT = HELLO WORLD!
