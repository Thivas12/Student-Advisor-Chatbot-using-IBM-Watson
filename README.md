# Student-Advisor-Chatbot-using-IBM-Watson
In this project, I developed a chatbot using IBM Watson services. I did this as a final project for the professional certificate. I created a Coursera Student Advisor chatbot that can answer both "short tail" and "long tail" questions students might have about Coursera and its learning programs. We will use several Watson AI APIs, including Assistant to hold an interactive dialog, and Discovery to answer the "long tail" of questions and to recommand learning resources.

# COMPLETE OVERVIEW AND DESCRIPTION
**CREATE A WATSON DISCOVERY SERVICE** :
After login to the IBM Cloud account, create an instance of Watson Discovery **Note : If you created a Watson Discovery in the past using the Lite plan, you won't be allowed to create a second instance. You can use the instance you already created.**

![image](https://user-images.githubusercontent.com/86511074/169664529-6e427795-1af6-4e46-a4ee-0d942b1ef194.png)

**CREATE A WATSON ASSISTANT SERVICE**:
From the catalog page that loads, Click on the services, select the AI category and then select the Watson Assistant service from the list. In the Watson Assistant setup page, choose a region depending on where you are located. For example, here we have chosen Dallas. Once the service is created you will see the below page, from where you can launch Watson Assistant. Click on the **Launch Watson Assistant** button to access the web application that will allow you to create chatbots.

![image](https://user-images.githubusercontent.com/86511074/169664677-90d62538-11af-4439-894f-d1bc04d925cc.png)

**CREATE A DISCOVERY COLLECTION**:
From Dashboard, we can access Discovery service.

![image](https://user-images.githubusercontent.com/86511074/170094612-4f5b949f-eb70-449f-800e-5e9c76f2c7de.png)

Now Launch Watson Discovery.

![image](https://user-images.githubusercontent.com/86511074/170094741-cae70ada-d770-48db-a997-eb76f57d1207.png)

Now creating a barebone student advisor chatbot for Coursera. But the problem with the traditional approach of hardcoding courses in the node responses within Watson Assistant is that Coursera has thousands of courses. It's just not feasible to manually add all of them to a dialog. So, instead, we'll leverage Discovery and connect it to Watson Assistant. But before we can do all that, we'll need to have a Coursera course collection uploaded within Discovery (**which I attached in the repo as .zip file**) 

**There are two main ways to upload data to Discovery:** uploading documents and connecting to a data source. If we head over to the Manage Data section of your Discovery instance, we'll see the two corresponding buttons.

![image](https://user-images.githubusercontent.com/86511074/170096136-20dfa9ce-d3b6-45a5-804a-f6512ee3c5b7.png)

If we click on **Connect a data source** button we can see a list of sources/services to connect 

![image](https://user-images.githubusercontent.com/86511074/170096509-8ce23278-18bc-49e9-adc3-658528ee4307.png)

The most relevant source here would be **Web Crawl**, which allows us to specify a URL and the collection will store each page connected to that URL as a document. We can even specify how deep the crawler should go(e.g., how many links it should follow before stopping).

For the sake of showing how to import documents, and to spare Coursera's servers from thousands of people all crawling their course catalog, I prepared a collection of 500 courses of theirs. The reason why I limited it is that your Lite free account is limited to 1000 documents a month, and you'll need more documents for a second collection.

**UPLOAD COURSERA COURSE DOCUMENTS**:
From the Manage Data section of your Discovery instance, **select Upload your own data.** You'll be asked to give a name to your collection. Call it Coursera Courses or something similar and click Create

![image](https://user-images.githubusercontent.com/86511074/170098126-bd8b628c-6d78-4de3-bc9a-60e41f7cf636.png)

You'll be prompted to upload documents. **Click on the upload icon and add the files you extracted**. You can use CMD+a or CTRL+a to select all of them at once in the upload dialog. Alternatively, you can simply drag and drop the files on the page.

![image](https://user-images.githubusercontent.com/86511074/170098737-dab60d0e-eb3a-4a75-acc7-1f9009524b8b.png)

The most important fields are name, slug, and description. Name is the title of the course, slug the path to the course that we'll append to https://www.coursera.org/learn/
