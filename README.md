Creating a demo to showcase OpenShift's capabilities, particularly focusing on easy application deployment, is a great way to illustrate the benefits to potential customers. Here's a step-by-step guide for a simple yet effective demo:

# 1. Setting Up the Environment
Ensure you have access to an OpenShift cluster. If you don't have one, you can create a trial account on Red Hat OpenShift Online.

# 2. Accessing OpenShift
Step 1: Log in to the OpenShift Console (web UI) or use the oc command-line tool.
If using the command line, run: oc login [CLUSTER_URL] -u [USERNAME] -p [PASSWORD]

# 3. Creating a New Project
Step 2: Create a new project for your demo.
In the Console, click on “Create Project” and fill in the details.
Or, use the command: oc new-project demo-project

# 4. Deploying a Sample Application
You can deploy a simple application like a Node.js or Python web app. For this demo, let's use a Node.js app.

Step 3: From the OpenShift Console, go to the Developer perspective.

Step 4: Click on “+Add” and select “From Catalog.”

Step 5: Choose a Node.js builder image and provide a Git repository with the Node.js source code. (You can use a sample app repository from GitHub).

Step 6: Follow the prompts to configure and create the application.

Alternatively, using the CLI:
'''
oc new-app nodejs~[GIT_REPO_URL] --name=my-nodejs-app
oc expose svc/my-nodejs-app
'''
This will create a new Node.js application and expose it as a service.

# 5. Monitoring the Deployment
Step 7: Watch the build process.

In the Console, go to the “Builds” section.
Using CLI: oc logs -f bc/my-nodejs-app
Step 8: Once the build is complete, the application will be deployed automatically.

# 6. Accessing the Application
Step 9: Find the external URL of the application.
In the Console, go to “Routes” in the application’s overview page.
Using CLI: oc get route my-nodejs-app -o jsonpath='{.spec.host}'

#7. Demonstrating Scaling Capabilities
Step 10: Show how easy it is to scale the application.
In the Console, adjust the number of pods.
Using CLI: oc scale --replicas=[NUMBER_OF_PODS] deployment/my-nodejs-app

# 8. Cleanup (Optional)
Step 11: Delete the project if this is a one-off demo.
oc delete project demo-project

# Additional Tips
Prepare a Sample Git Repository: Have a Git repository with a simple application ready. This makes the demo smoother.
Explain Each Step: As you go through the steps, explain what each command or action is doing and how it contributes to the ease of application deployment in OpenShift.
Highlight OpenShift Features: Talk about features like automated builds, scaling, self-healing (auto-replacement of failed pods), and integrated monitoring and logging.
