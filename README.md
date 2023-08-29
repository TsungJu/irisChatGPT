**irisChatGPT** application leverages the functionality of one of the hottest python framework [LangChain](https://python.langchain.com/docs/get_started/introduction.html) built around Large Language Models (LLMs).
LangChain is a framework that enables quick and easy development of applications that make use of Large Language Models.
Application is built by using objectscript with the help of  [intersystems Embedded Python](https://docs.intersystems.com/irisforhealthlatest/csp/docbook/DocBook.UI.Page.cls?KEY=AFL_epython) functionality. It also contains [Streamlit](https://streamlit.io/) web application which is an open-source Python app framework to create beautiful web apps for data science and machine learning.

![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/e84ecde9-24a6-475e-b598-6a7f3abe1410)


# Streamlit Web Application Layout
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/acfb914e-560f-4554-babb-1a65b1531a57)

# Features
* Built-in [Intersystems ObjectScript Reference](https://docs.intersystems.com/iris20231/csp/docbook/DocBook.UI.Page.cls?KEY=RCOS) ChatGPT
* Built-in [InterSystems Grand Prix Contest 2023](https://community.intersystems.com/post/intersystems-grand-prix-contest-2023) ChatGPT
* [INTERSYSTEMS FHIR SQL BUILDER](https://docs.intersystems.com/components/csp/docbook/DocBook.UI.Page.cls?KEY=AFSB) ChatGPT
* ChatGPT with FHIR server
* Answer questions over a Cache database by using SQLDatabaseChain
* Create your own chatGPT model by using PDF, word and text documents
* OpenAI ChatGPT
* Wikipedia Search
* Search on the internet by using DuckDuckGo (DDG) general search engine
* Generate Python code by using Python REPL LangChain functionality
* Streamlit Web application
   * Intersystems objectscript reference ChatGPT (Web interface)
   * Intersystems grand prix contest ChatGPT (Web interface)
   * Select and upload your own document for ChatGPT (Web Interface)
   * OpenAI ChatGPT (Web interface)

# How to Run

To start coding with this repo, you do the following:

1. Clone/git pull the repo into any local directory

```shell
git clone https://github.com/mwaseem75/irisChatGPT.git
```

2. Open the terminal in this directory and run:

```shell
docker-compose build
```

3. Run the IRIS container with your project:

```shell
docker-compose up -d
```

# Installation with ZPM
```
zpm "install irisChatGPT.ZPM"
```
# Getting Started 
## Get OpenAI Key
Application requires OpenAI API Key, sign up for OpenAI API on [this page](https://platform.openai.com/account/api-keys). Once you signed up and logged in, click on Personal, and select View API keys in drop-down menu. Create and copy the API Key

![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/7e7c7880-b9ac-4a60-9ec9-289dd2375a73)


#### Connect to IRIS Terminal by using below command
```
docker-compose exec iris iris session iris
```
#### Create a new instance of dc.irisChatGPT class and use SetApiKey method to set OpenAI API Key 
```
set chat = ##class(dc.irisChatGPT).%New()
```

```
do chat.SetAPIKey("Enter your Open API Key here")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/dd4303ca-6ff4-48a0-92c1-70a2ad18cdec)

## Chat with [Intersystems objectscript reference](https://docs.intersystems.com/iris20231/csp/docbook/DocBook.UI.Page.cls?KEY=RCOS)
```
write chat.irisDocs("Give me details of %$PIECE function with syntax")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/ba064270-ed6e-4c8d-b8a3-5f38fcec3007)

## Chat with [InterSystems Grand Prix Contest 2023](https://community.intersystems.com/post/intersystems-grand-prix-contest-2023)
```
write chat.irisContest("Give me Prizes and nominations")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/ae4b7f93-eac6-4af9-8494-5b7653c19bd8)

## [INTERSYSTEMS FHIR SQL BUILDER](https://docs.intersystems.com/components/csp/docbook/DocBook.UI.Page.cls?KEY=AFSB) BUILDER ChatGPT
Repository will load FHIR Resources, All you need is to configure FHIR SQL BUILDER.
For configuration, Navigate to [http://localhost:55037/csp/fhirsql/index.html](http://localhost:55037/csp/fhirsql/index.html#)
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/3a71fc32-bbd5-4b4a-b3da-f3e9f1556cb3)

For more details about configuration, please watch this [Tutorial Video](https://learning.intersystems.com/course/view.php?name=ProjectingHL7FHIRTables) and check 
[iris-fhirsqlbuilder application](https://openexchange.intersystems.com/package/iris-fhirsqlbuilder) by @Guillaume Rongier

Please note that I am using FHIR as package name

To view the specification, Navigate to [http://localhost:55037/csp/fhirsql/index.html/spec#/1](http://localhost:55037/csp/fhirsql/index.html/spec#/1) 
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/24483e3a-c8ed-4a2b-a630-2a2c7ad4937d)


After the configuration, we can do ChatGPT with FHIR SQL 

```
write chat.irisFHIRSQL("Give me total patients")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/eaa04b92-2a20-4ca0-9ef2-495735a76b28)


```
write chat.irisFHIRSQL("List down all the Male Patients")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/3637e5b2-b63c-49d0-bf51-b52203843ee6)

```
write chat.irisFHIRSQL("Give me patients where birthdate < 2000")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/bc9a9247-1153-4218-b968-ee23c66c32eb)

```
write chat.irisFHIRSQL("Give me observation details of patient 175")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/468661a6-46f1-4d13-bff5-998f16ad0f41)

```
write chat.irisFHIRSQL("Give me total encounter of 175")  
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/790c397b-4b6f-4936-915e-851a94ffc50f)

```
write chat.irisFHIRSQL("Give me goal of Patient 175")  
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/04c10a07-be90-4540-93c7-52084176ead2)

```
write chat.irisFHIRSQL("Give me details of Organization 80")  
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/314aff7a-4300-40a4-86d5-04f07b0d932f)



## ChatGPT with FHIR server

We need to first set FHIR Endpoint by using SetFHIRUrl method. 
Currently, I am setting the FHIR server End point running in docker

```
do chat.SetFHIRUrl("http://localhost:52773/csp/healthshare/fhirserver/fhir/r4/")
```

Once URL is set, Now we can ask questions about Patient and Observation resources

```
write chat.irisFHIR("Give me total patients")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/e2f64db1-09d4-40a7-a643-1281b981950f)

```
write chat.irisFHIR("List down all the Male Patients")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/a7c72334-cc65-493d-9002-ff977336fbd1)

```
write chat.irisFHIR("Give me observation details of patient 175")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/cd8b8527-8baf-48a7-838c-f8642e6742b8)

```
write chat.irisFHIR("Give me procedure of patients id 1") 
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/fd0de05e-ce9b-45b8-a14e-0586156766ed)

```
write chat.irisFHIR("Give me Immunizations  of patients id 175") 
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/1e423b9e-8b26-40c1-8cbc-d11cb15133c3)

```
write chat.irisFHIR("Give me all the encounters of year 2012") 
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/449aeee9-3c1c-4616-977d-21b676ec3f0c)

```
write chat.irisFHIR("Give me condition of patient id 175")  
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/f52fe240-36ce-48f1-bfdd-0c9d2d06c441)

```
write chat.irisFHIR("Give me all female practioners")  
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/62d28bce-7c62-42aa-b2d0-78a964ebb0ef)



## Answer questions over a Cache database by using SQLDatabaseChain
```
write chat.irisDB("Give me total tables")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/adba2e12-3066-4c00-a595-0c22dcb95100)


## Create your own chatGPT model by using PDF, word and text documents
#### Use ingest function to upload the document
Copy your document to ManagerDirectory()+'pdfdata/' folder and then use the below command to ingest the data. 
(The repository already contains [Defining and Using Classes](https://docs.intersystems.com/irislatest/csp/docbook/DocBook.UI.Page.cls?KEY=GOBJ) PDF which we will upload by using the below command)

```
set doc = ##class(dc.irisChatGPT).ingest("GOBJ.pdf")
```
#### Now we will use personalGPT function to chat with our document

```
w chat.personalGPT("Give me details of objects and properties") 
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/de44febe-c028-4b57-aa47-25bcd643f9d0)

## OpenAI ChatGPT
```
w chat.openAI("Give me details of Intersystems")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/68574d29-8a8b-4c54-b3e1-569240e117af)

## Wikipedia Search
```
w chat.wikiPedia("LangChain")   
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/d272bc12-12a8-4062-a73a-bcdb75d46f8d)

## Search on the internet by using DuckDuckGo (DDG) general search engine
```
w chat.duckDuckGo("What is the Capital of USA")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/64c1c1ff-95af-44e3-9a18-5d77dcbc5fa8)

## Generate Python code by using Python REPL LangChain functionality
```
w chat.pythonREPL("Write a function to check if 11 a prime number and test it")
```
![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/f4f93837-7cf3-4410-8eb3-f974861e8925)

#
## Streamlit Web application
Navigate to [Streamlit Web Application](http://localhost:8501) or [CSP Web application](http://localhost:55037/csp/irisChatGPT/index.csp)

![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/1855dca3-b28d-43bf-aaf8-306a3d8e6f92)

![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/fbfda164-8b3a-4e96-b1d2-3ac4178a9f55)

![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/3ada6a24-de49-4101-8673-9b777ea6ccb1)

![image](https://github.com/mwaseem75/irisChatGPT/assets/18219467/452dd73e-7678-42b3-a2ae-19d0797206ae)








## Thanks
