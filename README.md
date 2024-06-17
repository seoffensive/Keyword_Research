**With the Keyword Research script, you can discover all keywords related to the main keyword in groups. This includes latent semantic indexing and long tail keywords. In this way, you can get all related keywords in bulk without doing manual keyword research for hundreds of keywords. 
This script takes data from the Google Ads API, Google automatic word complement suggestions, and the Gemini 1.5 Flash model to ensure that any related words are not overlooked.**


# How to install?


1. Create a new project in Google Cloud. Then go to APIs & services > Credentials, click on Create Credentials and create an Oauth client ID.

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/db957365-00e9-4612-b82d-60931f1635c9)

2. When you are generating your OAuth client ID, select in the application type Desktop App and click on Create.
   
![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/d1a10bc2-cf22-47e1-8b7a-2474ecf292d2)

3.  After creating the OAuth ID, you should be able to see this

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/4b0dd384-e846-48a7-8840-0f9f37a356ec)

4. After creating the OAuth client ID, download the JSON file. This JSON file and some of their variables will be used to create the YAML file that we will use to authenticate in Google Ads API.
Finally, you will have to go to the OAuth consent screen section and add your email address as a test user so that you will be able to use your email address to give consent in the OAuth screen:

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/b899f26c-56a5-45a5-ac5f-69b510995685)

*Don't forget to click the **"publish"** button on the Google Cloud OAuth permission screen.*

5. One of the most important pieces of data we need to get to configure the python file is the developer token. The developer token allows us to access the Google Ads API so we can retrieve relevant keyword data.
In order to obtain a developer token, you will need to have a Google Ads Manager account. If you don’t have one, you can create one here (https://ads.google.com/home/tools/manager-accounts/)

6. Create the account, Sign In, click on tools, then click on API center, and you’ll see the developer token there.

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/762e2626-003e-4ff6-9186-abe586650719)

7. Next, we will need to get a customer ID, as it is also needed to configure the file. The customer ID is a unique number used to identify your Google Ads account and is required for authentication.
First, you need to create a Google Ads Test Account to use the associated customer ID for testing purposes. You can create a Google Ads test account by clicking here. (https://ads.google.com/nav/selectaccount?sf=mt&hl=en)

8. Once you have created your test account, you can find the customer ID in the top right corner of your Google Ads admin account dashboard, as shown below:

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/580b6943-b73d-44f1-9b9b-1c3fe11e91ed)

*You will not add this to the yaml file. You will enter the area shown in the image below without -.*

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/d4519d6b-68a8-4a83-8e2f-4e084865a4ee)


9. Afterwards, make a google-ads.yaml file in the same folder as the python file and copy the following code into it. Make sure to add your developer token, client id, and client secret into it: (You can also access the sample yaml file from the repo.)

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/117ee5e8-295e-4c1a-84f2-f42dbb341a3a)

10. The client_secret, client_id and developer_token is already obtained, so the last thing that we need to obtain to create the YAML file is the refresh token. To get this token you must first download created_user_credentials.py from the repo. Then run the following command in your terminal to use the secrets.json file you downloaded earlier to generate the authentication and renewal token:

**python generate_user_credentials.py --client_secrets_path=secrets.json**

*If the secrets.json and generate_user_credentials.py files are in the same directory, you can run this command directly from the terminal. If the file paths are different, do not forget to specify this.*

*NOTE: the client secrets is the JSON file that we have downloaded previously when we set up the project on Google Cloud Platform.*

11. This command will generate an URL that you will need to open in your browser with a code. You will have to authenticate this app using a google account you’ve added to the Test Users in OAuth Consent screen earlier.

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/2886bbec-16d0-418f-9a62-f133fa29258b)

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/6d2deca7-0861-4433-98fe-6240a27e71ee)

12. After authenticating, the terminal will display a refresh token. Copy and paste this refresh token into the YAML file and your YAML file will be complete!

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/53312958-b688-4a97-aa73-3f1ec5e993b4)

13. Now you can open the keyword_research.ipynb file from your Jupyter Notebook and start executing all the lines one by one. You will specify the name of your keyword file in this line:

![image](https://github.com/seoffensive/Keyword_Research/assets/173078980/3bcc7bd3-3d98-4e70-a5e7-f54da3f6a2d9)

*There are also helpful instructions in the keyword_research.ipynb file.*    
