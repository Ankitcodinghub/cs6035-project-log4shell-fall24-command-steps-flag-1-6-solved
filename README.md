# cs6035-project-log4shell-fall24-command-steps-flag-1-6-solved



**<span style='color:red'>TO GET THIS SOLUTION VISIT:</span>** https://www.ankitcodinghub.com/product/cs6035-project-log4shell-fall24-command-steps-flag-1-6-solved/

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;125826&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS6035  Project Log4Shell Fall24 Command\/Steps Flag 1-6 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">
            
<div class="kksr-stars">
    
<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
    
<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>
                

<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
<h3><strong>SPRING2025 SOLUTION<a href="https://www.ankitcodinghub.com/product/cs6035-log4shell-2025-spring-solved/"><span style="color: #0000ff;"> VIEW HERE</span></a></strong></h3>
<u>Pro</u>j<u>ects </u>/ <u>Lo</u>g<u>4Shell </u>/ Intro Flag Intro Flag

Now that we are set up, let’s do a quick rundown of Log4j, how it works at a high level, and test that we are able to successfully call and exploit the application.

As you should know from the background and resource’s section, Log4j is an application logging library that outputs user defined program information. An example log statement would look like the following:

static Logger log = LogManager.getLogger(RestServlet.class.getName()); log.debug(“ApplicationId: {}”, applicationId);

The log statement above as you can see, defines the class, log level of the message and the actual message. Notice that we are injecting user input into the log message. This is where our vulnerability is.

To be more specific, here is what the output of the message actually will look like:

Now we can map the code above to the logged message. The date/time is defined in configuration files which are out of the scope of this project. Next is where our code starts to map. We have [Classname.java:LineNumber]. This is helpful to know exactly what part of your code is executing and where.

Next, we see DEBUG. This is what is called the log level. Log levels are used for the amount of output you want your application to log, or even to classify errors different from informative messages. The typical log levels are DEBUG, INFO, WARN, ERROR, FATAL. To further explain, if a log level is set to say ERROR, your application will not log anything on WARN, INFO, or DEBUG level. This application is set to DEBUG.

Finally, we get to the actual logged message. As you can see, we log the constant text as well as the injected variable applicationId, which is our applicationId. This is the most important part you will want to pay attention to. Throughout this project, you will try to find messages that log user defined input and inject your malicious string into it.

Now, let’s have some fun and get familiar with the application. To do so, we will call the application normally and then lookup the java version on the application server.

To start we can run a simple inquiry to the services /isAlive endpoint and see what we get back from the logs and see if we can find anything that is exploitable.

GATECH_ID IS A REQUIRED HEADER Open a new terminal and run: curl ‘http://localhost:8080/rest/products/isAlive’ -H ‘GATECH_ID:123456789’ -H ‘Accept:application/json

You should see your logs log some messages in the log tailing terminal window. Let’s inspect it.

Go back to the terminal window you are tailing the logs in. When the server intercepts a request, it logs “Request intercepted” to alert the user where the request starts. As we can see, there is not much going on in terms of useful information, but we can see the service did log a message that could be exploitable.

Voila! In the highlighted message, we see that it is logging the Method Type: GET, the URL: /rest/ products/isAlive, and some headers that are being logged. This is a good indicator that we can exploit this service by sending lookups through a header.

Let’s call one more endpoint to see how headers work and what the application does when we request user data.

In your curl terminal, run the following command: curl ‘http://localhost:8080/rest/products/productlist’ -H ‘GATECH_ID:123456789’ -H ‘Accept:application/

Your output should be similar to:

**Note: You can zoom in by using ctrl + scroll

Take some time to inspect the logged messages and try to understand what the program is doing and the flow of it.

Lets try to get the java version on the server now.

The checked headers for this application are content-type, accept, and X-NetworkUserId, although not all are always checked/exploitable.

Construct a malicious payload using one of the logged headers that will return the java version of the host of the web application. You should see something like the screenshot below if successful:

**Note: You might need to scroll up to see this output.

Do you see the same output? LIGHTWEIGHT BABY! Muahaha! If not, try to research the log4shell exploit more and learn how to exploit the lookup.

Our hunch was correct and we have successfully exploited the vulnerability. You can play around with this if you like and see what other lookups you can perform. It is possible to lookup system settings, environment variables and much more just with this.

Be sure to save your work outside of the VM in case the VM crashes or some other unforeseen issue arises. This will ensure you are not losing your work.

Flag 1: Environment Echo | CS 6035&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; https://github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Proj…

<h1>CS 6035</h1>
<u>Pro</u>j<u>ects </u>/ <u>Lo</u>g<u>4Shell </u>/ Flag 1: Environment Echo Flag 1: Environment Echo (5 pts)

Make sure you have gone through the <u>Setup</u> and <u>Intro</u> sections.

If you haven’t already, run the start script in the home directory of log4j user, start the container with the start script:

./StartContainer.sh

The endpoint for this exploit can be called and inspected via:

curl ‘http://localhost:8080/rest/products/isAlive’ -H ‘GATECH_ID:123456789’ -H ‘Accept:application/json

Add this flag (Congratulations! Your flag1 is: ____) to your project_log4shell.json file.

NOTE: You do not need to use Java code, ldap, python server, etc to get this flag.

<ul>
<li>of 2 9/24/2024, 12:58 PM Flag 1: Environment Echo | CS 6035&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; https://github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Proj…</li>
</ul>
CS 6035

<u>Pro</u>j<u>ects </u>/ <u>Lo</u>g<u>4Shell </u>/ Flag 2: Get a Shell Flag 2: Get a Shell (5 pts)

Make sure you have gone through the <u>Setup</u> and <u>Intro</u> sections.

If you haven’t already, run the start script in the home directory of log4j user, start the container with the start script:

./StartContainer.sh

The endpoint for this exploit can be called and inspected via: curl ‘http://localhost:8080/rest/products/isAlive’ -H ‘GATECH_ID:123456789’ -H ‘Accept:application/json

Now that we have proven this service is vulnerable and that we can exploit it in at least one place, let’s try to do more damage and do something more malicious. If you have not already, you NEED to read through the suggested readings and learn how/why it is possible to send jndi lookups.

Open the “Exploit.java” file and construct a malicious payload to execute such that when the jndi/ ldap lookup happens, it gives you root access on the vulnerable application server.

You should have a total of 4 terminal windows open which are the 3 from the SETUP section and one terminal window to run your curl command.

Once you are ready to run the exploit, ensure that the java version you are running the command is “java version 1.8.0_20” by running: java -version

To compile your .java file into a class file, move to the directory the .java file is stored in and run: javac Exploit.java

NOTE: THIS PROJECT IS WRITTEN USING THE VULNERABLE VERSION OF 1.8.0_20. NOT ALL

VERSIONS OF JAVA ALLOW LOOKUPS AND YOU COULD SPIN YOUR WHEELS FOR AWHILE

NOT KNOWING WHY YOUR EXPLOIT IS NOT RUNNING IF YOU DO NOT FOLLOW THIS DIRECTION.

We have added the ability to log from your Exploit.java file so that you can log useful debugging information while you are developing your exploit. To log messages from your Java class, tail the ~/Desktop/log4shell/logs/console.log file and add System.out.println statements to your Exploit.java.

This should create Exploit.class. Run your “python3 -m http.server 4242” command in this directory.

Hint: Pay close attention to the ports you are using in this exercise.

If successful, you should see similar console output as the screenshot below:

With success, you should see this in the console output of the nc command. Now type “whoami” and you should see “root”.

Did you get the screenshot above? Congratulations!

If not, keep trying and ensure all of your hosts/ports match. Analyze the screenshots and make sure yours matches. If you are not getting the ldap/python server output, you likely did not set up your hosts/ports correctly OR your Exploit.java file isn’t correct.

You now have root access to the vulnerable application’s server. YIKES! This is a great example why this exploit is so dangerous. You can perform any task on this server now. For now, go back 2 directories using “cd ..” and then run “java -jar Flag2.jar” to get your flag and add it to the json under “Flag2”.

Flag 3: Config.Properties Surprise | CS 6035&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; https://github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Proj…

<h1>CS 6035</h1>
<u>Pro</u>j<u>ects </u>/ <u>Lo</u>g<u>4Shell </u>/ Flag 3: Config.Properties Surprise FLAG 3: Config.Properties Surprise (25 pts)

Make sure you have gone through the <u>Setup</u> and <u>Intro</u> sections.

If you haven’t already, run the start script in the home directory of log4j user, start the container with the start script:

./StartContainer.sh

For this flag we will use the /products/ resource. There are 4 total endpoints for this resource.

Only the following 2 are relevant for this flag.

Call the following endpoint to fetch all the records. Save one of the ids.

GET All – Fetch all product records: curl ‘http://localhost:8080/rest/products/productlist’ -H ‘GATECH_ID:123456789’

Call the following endpoint to GET by ID and inspect the logged output.

GET By ID – Fetch a single product record by ID: curl ‘http://localhost:8080/rest/products/product/&lt;id&gt;’ -H ‘GATECH_ID:123456789’

You have caught wind that there is a properties file that this application uses to inject configurable data during runtime.

For this exploit, you will use the log4j exploit to update the “config.properties” file saved in the root directory of the application. This properties file contains a property that will set the customer service email for all of the products.

See if you can find anything that gives you a hint about how to exploit it/what you need to do, to update the property.

This application links the properties’ customer service email address to all products in its

1 of 2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 9/24/2024, 12:59 PM Flag 3: Config.Properties Surprise | CS 6035&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; https://github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Proj…

response. You have a good friend who has been bothering you so you want to spam his email inbox with customer complaints about these products. First, you need to make sure that this is even possible.

One thing to keep in mind is that the application checks to see if this file has been tampered with. You will need to make sure you don’t overwrite the file and instead just update it.

For this flag, you will need to update the properties file so that when the application builds the product response, it sets the email address to your gatechId. *i.e. 123456789, NOT user@gatech.edu or 123456789@gatech.edu

If successful, you should get your flag in the email field of the response:

Hint: Someone might have tried to roll their own patch and tried to deny requests containing malicious string patterns.

*** **IF THIS FLAG COMES OUT BLANK, Restart container by running the stopContainer and startContainer scripts in the home directory of the log4j user. *****

Flag 4: Command and Concat | CS 6035&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; https://github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Proj…

<h1>CS 6035</h1>
<u>Pro</u>j<u>ects </u>/ <u>Lo</u>g<u>4Shell </u>/ Flag 4: Command and Concat FLAG 4: Command and Concat (25 pts)

Make sure you have gone through the <u>Setup</u> and <u>Intro</u> sections.

If you haven’t already, run the start script in the home directory of log4j user, start the container with the start script:

./StartContainer.sh

For this flag, we will exploit an endpoint that adds a new user: curl -X PUT ‘http://localhost:8080/rest/users/user’ -H ‘GATECH_ID:903449128’ -H ‘Content-Type:applicati

Take some time to inspect this output and see what you need to exploit. Yes the exception is expected, and maybe there is even a clue above it 😉

For this flag, you will construct a malicious file (Exploit.java) and compile it, so that when deserialized it will create a simple “.txt” file on the server to get the flag. Using the log4shell exploit, create a file named “Ronnie.txt” on the server and add ONE line that says

“LightWeightBaby!” (You do not need the quote). If you do not follow this exactly, you will not get this flag.

Upon success, you will see the output below. (You might have to scroll for this)

<ul>
<li>of 2 9/24/2024, 12:59 PM Flag 4: Command and Concat | CS 6035 https://github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Proj…</li>
</ul>
Hint: The name of this flag is a huge hint as to what you need to do. Pay close attention to the logged messages and their format. *** **IF THIS FLAG COMES OUT BLANK, Restart container by running the stopContainer and startContainer scripts in the home directory of the log4j user. *****

Flag 5: PubSub Override | CS 6035&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; https://github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Proj…

<h1>CS 6035</h1>
<u>Pro</u>j<u>ects </u>/ <u>Lo</u>g<u>4Shell </u>/ Flag 5: PubSub Override FLAG 5: PubSub Override (25 pts)

Make sure you have gone through the <u>Setup</u> and <u>Intro</u> sections.

If you haven’t already, run the start script in the home directory of log4j user, start the container with the start script:

./StartContainer.sh

For this flag, we will exploit a previous endpoint that publishes updates to a topic on the server: curl -X PUT ‘http://localhost:8080/rest/users/user’ -H ‘GATECH_ID:903449128’ -H ‘Content-Type:applicati

You remember that properties file? Good! We are going to play with it yet again.

For this exploit, you will use the log4j exploit to overwrite the “config.properties” file saved in the root directory of the application. This properties file contains a topic that the application will publish a message to when updateUser call is made (the application is also subscribed to this topic as you can see in the logs).

You will need to trick the application into publishing a message to a different topic with your GATECH_ID as the account number in order to generate a valid flag.

Upon success, you should see your output similar to that below:

<ul>
<li>of 2 9/24/2024, 12:59 PM Flag 5: PubSub Override | CS 6035&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; https://github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Proj…</li>
</ul>
Hint: Look through the cs6035.log to find clues about what this other topic could be. Your flag could be invalid if you have not sent your GATECH_ID appropriately in the published message. *** **IF THIS FLAG COMES OUT BLANK, Restart container by running the stopContainer and startContainer scripts in the home directory of the log4j user. *****

CS 6035

<u>Pro</u>j<u>ects </u>/ <u>Lo</u>g<u>4Shell </u>/ Flag 6: Restful FLAG 6: Restful Data (15 pts)

Make sure you have gone through the <u>Setup</u> and <u>Intro</u> sections.

If you haven’t already, run the start script in the home directory of log4j user, start the container with the start script:

./StartContainer.sh

For this flag we will use the /products/ resource. There are four endpoints for this resource:

GET All – Fetch all product records

curl ‘http://localhost:8080/rest/products/productlist’ -H ‘GATECH_ID:123456789’

GET By ID – Fetch a single product record by ID

curl ‘http://localhost:8080/rest/products/product/&lt;id&gt;’ -H ‘GATECH_ID:123456789’

GET By Email – Fetch all records associated with an email (This will require you to create a new product with an email field. The initial set of products do not have an email persisted, they return with the default email)

curl ‘http://localhost:8080/rest/products/product?email=example@example.com’ -H ‘GATECH_ID:123456789’

POST Create or Update a new record – Post a new record or update an existing record by providing the id in the request

curl -X POST ‘http://localhost:8080/rest/products/product’ \

-H ‘GATECH_ID:123456789’ \

-H ‘Content-Type: application/json’ \

-d ‘{

“make”: “Ford”,

“model”: “Mustang”,

“trim”: “GT”,

“price”: 45000.00,

“email”: “example@example.com”

}’

We’ve explored introducing malicious strings to be triggered by the application as it accepts and processes an HTTP request. For this flag we’re going to explore an often overlooked attack vector for exploits like Log4J: Data at Rest.

Data at Rest is data that has already been persisted to some data store and is sitting idle. In the case of log4shell, this could be data that is structured in such a way that when the application retrieves and attempts to use or log it, it triggers the LDAP call.

Use the product POST endpoint to persist a record to the database that, when retrieved later, will trigger the LDAP call. You will have to inspect the logs of each of the endpoints to come up with a successful attack strategy.

You will use the log4j exploit to overwrite the “config.properties” file saved in the root directory of the application similar to what you did in Flag 3 and Flag 5. You will write a new property product.id that should have the value set to the id of the malicious product record that you have created/updated.

When the application fetches the record upon calling the right GET endpoint, it will trigger the exploit and, if successful, will generate the Flag 6 message in the logs.

Note: You will have to trigger the LDAP call with the malicious record in order to generate the Flag.

Upon success, you should see your output similar to that below:

*** **IF THIS FLAG COMES OUT BLANK, Restart container by running the stopContainer and startContainer scripts in the home directory of the log4j user. *****

Flag 7: SQL | CS 6035&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; https://github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Proj…

<h1>CS 6035</h1>
<u>Pro</u>j<u>ects </u>/ <u>Lo</u>g<u>4Shell </u>/ Flag 7: SQL

FLAG 7 (Extra Credit): SQL Attack Authorization Persuasion (2 Pts)

Make sure you have gone through the <u>Setup</u> and <u>Intro</u> sections.

If you haven’t already, run the start script in the home directory of log4j user, start the container with the start script:

./StartContainer.sh

The endpoint for this exploit can be called and inspected via: curl -X “DELETE” ‘http://localhost:8080/rest/users/user/&lt;id&gt;’ -H “GATECH_ID:123” -H “X-NetworkUserId:MW

This endpoint is used to delete users from the system database. Only users with admin access (ADMIN_YN = ‘Y’) are allowed to perform this task. You can call the list of users (/users/all) to experiment with this.

In this flag, you will use what you have learned and do something much more nefarious than the previous flags. You will need to use the log4shell exploit to execute an SQL attack and insert a user into the database, such that when the application authorizes the user it returns true and allows a delete.

The userName you must use is EDBOY, you must set the userRole to

HOW_DARE_YOU_MOCK_THE_SON_OF_A_SHEPHERD and you must set adminYN to Y to achieve this flag.

Everything you need to achieve this task is logged in one of the 2 log files somewhere. Dissect the log file thoroughly as you will need to do more than just “inject” an sql string. Keep in mind that log4shell does not allow you to interact with the program’s state itself, only execute arbitrary code at the level of access the vulnerable program itself is running on. This means that this will not be a typical SQLi attack where you are exploiting the applications’ queries via injection. In fact, you will not actually interact with the applications sql queries at all. You will need to think outside of the box on how to do this .

<ul>
<li>of 2 9/24/2024, 12:59 PM Flag 7: SQL | CS 6035 https://github.gatech.edu/pages/cs6035-tools/cs6035-tools.github.io/Proj…</li>
</ul>
Upon success, you should see your output similar to that below:

Hint: Look in the logs for information on the database, the schema, and what could be useful for this attack. You will not need anything outside of the java standard library for this attack.

Hint 2: You will need to leverage one of the previous flags’ curls to get the keys to unlock this flag.

Your flag could be invalid if you have not sent your GATECH_ID appropriately in the published message. *** **IF THIS FLAG COMES OUT BLANK, Restart container by running the stopContainer and startContainer scripts in the home directory of the log4j user. *****

&nbsp;
