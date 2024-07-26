<!-- ---
name: Workshop - Build an AI Chatbot
description: Deploy a Flask app on App Service using Azure Developer CLI.
languages:
- python
- azdeveloper
products:
- azure-app-service
- azure
page_type: sample
urlFragment: simple-flask-server-appservice
--- -->

# Build an AI Chatbot workshops

This workshop will take us through how to use Azure OpenAI in Python. Then we'll progress to deploying a web app (more instructions on how to deploy a web app are below). 

## How to use this workshop
- Click the "Use Template" button to get your own copy of this repository.
- Use a GitHub Codespace, that will automatically set up your dev environment.
- In your Codespace navigate to the **python_rag_session1.ipynb file**, where you will get further instructions and will complete part of the activity.
- On **day two of the workshop use python_rag_session2.ipynb**. 

This repo has been cloned from a Simple Flask App repo so that all of the devops stuff is already set up, if you want to deploy it. (more instructions on how to deploy a web app are below). 


# About the Flask app template and deploying it

This AI workshop is created using the template found on [Awesome AZD](https://azure.github.io/awesome-azd/). 

If you want to base your own web app on the same template you can use the [Simple Flask AZD template](https://azure.github.io/awesome-azd/?name=simple+flask+azd) using the command listed in this search, or [see the repo here](https://github.com/tonybaloney/simple-flask-azd). 

The following is the README contents from the template repo that will help you to deploy your app. 

### Simple Flask App on Azure App Service

This repository includes a very simple Python Flask web site, made for demonstration purposes only.

#### Opening the project

This project has [Dev Container support](https://code.visualstudio.com/docs/devcontainers/containers), so it will be be setup automatically if you open it in Github Codespaces or in local VS Code with the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers).

If you're not using one of those options for opening the project, then you'll need to:

1. Create a [Python virtual environment](https://docs.python.org/3/tutorial/venv.html#creating-virtual-environments) and activate it.

2. Install requirements:

    ```shell
    python3 -m pip install -r requirements.txt
    ```

#### Local development

1. Run the server:

    ```console
    python3 -m flask run --port 50505 --debug
    ```

2. Click 'http://127.0.0.1:50505' in the terminal, which should open the website in a new tab.
3. Try the index page, try '/hello?name=yourname', and try other paths.

---

#### Deployment

This repo is set up for deployment on Azure App Service using the configuration files in the `infra` folder.

Steps for deployment:

1. Sign up for a [free Azure account](https://azure.microsoft.com/free/)
2. Install the [Azure Dev CLI](https://learn.microsoft.com/azure/developer/azure-developer-cli/install-azd). (If you opened this repository in a devcontainer, that part will be done for you.)
3. Login to your Azure account:

    ```shell
    azd auth login
    ```

4. Provision and deploy all the resources:

    ```shell
    azd up
    ```

    It will prompt you to login and to provide a name (like "flask-app") and location (like "eastus"). Then it will provision the resources in your account and deploy the latest code.

5. When `azd` has finished deploying, you'll see an endpoint URI in the command output. Visit that URI, and you should see the front page of the app! 🎉 If you see an error, open the Azure Portal from the URL in the command output, navigate to the App Service, select Logstream, and check the logs for any errors.

6. When you've made any changes to the app code, you can just run:

    ```shell
    azd deploy
    ```

##### Costs

By default, this project is set up to deploy to the *free* plan of Azure App Service.
The free plan is intended for trials, experimentation, and learning the service. There is no SLA for free plan and it is metered on a per app basis. Use of free plan for production workloads is not supported.

If you would like to deploy to a paid plan, you can set the `AZURE_APP_SERVICE_SKU` environment variable to `B1` or other SKU before running `azd up`:

```shell
azd env set AZURE_APP_SERVICE_SKU B1
```

Learn more about [App Service pricing](https://azure.microsoft.com/pricing/details/app-service/linux/).

⚠️ To reduce unnecessary costs, remember to take down your app if it's no longer in use,
either by deleting the resource group in the Portal or running `azd down`.
