# ush




























SE 
________________________________________
WEEK 1
SRS

Abstract
Purpose of the System
Functional Requirements (FR)
Non-Functional Requirements (NFR)
User Identification / Actors
User Workflow
Use Case Description / Use Case Table
Expected Outcome / Conclusion
________________________________________
WEEK 2
🌟 WEEK – 2 : GIT & GITHUB (PRIVATE REPOSITORY + COMMANDS)
________________________________________
🔵 Task-1: Push a multi-folder project to a Private GitHub Repository
Step-1: Create Private Repo
GitHub → New Repository → Enter name → Select Private → Create Repository
Step-2: Initialize Git in project
cd <project-folder>
git init
Step-3: Add remote
git remote add origin https://github.com/username/repo-name.git
Step-4: Stage and Commit
git add .
git commit -m "Initial commit"
Step-5: Push for the first time
⚠ Based on your default branch:
git push -u origin master
or
git push -u origin main
________________________________________
🔥 Task-3: Scenario-Based Git Questions (with answers)
WEEK 3
🌟 WEEK–3 : COLLABORATIVE CODING, CONFLICT RESOLUTION & PATCH FILE
________________________________________
🔷 (a) Collaboration through Organization
Steps:
1️⃣ GitHub → New Organization → Create free organization
2️⃣ Enter name, email → verify → next
3️⃣ Add members to organization
4️⃣ Go to:
Settings → Member privileges → Base permissions → Write
Settings → Projects base permissions → Write
5️⃣ Create a repository inside organization → make it private
📌 Now all members can push code to the same repo safely.
________________________________________
🔷 (b) Collaboration via Shared Private Repository
For Collaborator-1 (Owner)
Settings → Collaborators → Add people
Collaborator-2 receives an invitation → Accepts.
For Collaborator-2
git clone <repo-link>     # Get copy of project
git checkout -b feature/login   # Work on new branch
git add .
git commit -m "message"
git push origin feature/login
Update work from main (to avoid conflicts)
git checkout main
git pull origin main
git checkout feature/login
git merge main
________________________________________
🔵 2. RESOLVING MERGE CONFLICTS
A merge conflict occurs when two people change the same code line in the same file.
💥 How to solve conflict
git status        # shows conflicted file
Open the file → You will see markers:
<<<<<<< HEAD
Your code
=======
Other collaborator’s code
>>>>>>> feature/login
Fix by:
✔ Keeping one version
OR
✔ Combining both versions
Then remove the conflict markers.
After fixing:
git add filename
git commit
git push
Abort merge (if you want to cancel merging)
git merge --abort
________________________________________
🔵 3. PATCH FILE (very simple explanation)
📌 Patch = A file containing code difference that can be sent and applied by others.
Steps to create patch
git log        # copy commit hash
git format-patch -1 <commit-hash>
→ Creates a file like:
0001-MyChanges.patch
Steps to apply patch
git apply 0001-MyChanges.patch
or
git am 0001-MyChanges.patch
________________________________________
WEEK 4
3️⃣ Create Maven Java Project (MavenJava)
1. Start New Maven Project
1.	In Project Explorer, click Create a Maven project
or use menu: File → New → Maven Project
2.	In the first dialog:
o	Uncheck: “Create a simple project (skip archetype selection)”
o	Keep “Use default workspace location” ✔
o	Click Next
2. Select Archetype (quickstart)
1.	In the filter box type: quickstart
2.	Wait a few seconds.
3.	Select:
org.apache.maven.archetypes : maven-archetype-quickstart : 1.4
4.	Click Next
3. Enter Project Details
Fill like this:
•	Group Id: SE
•	Artifact Id: MavenJava
Click Finish
In the Console you will see a confirmation asking:
Confirm properties configuration:
...
Y:
👉 Type Y and press Enter.
Eclipse now creates the project.
4. Check Project Structure
In Project Explorer you should now see:
MavenJava
 ├─ src
 │  ├─ main
 │  │   └─ java
 │  │        └─ SE
 │  │             └─ MavenJava
 │  │                 └─ App.java
 │  └─ test
 └─ pom.xml
________________________________________
4️⃣ Run Maven Phases & Java Program
1. Open App.java
In Project Explorer:
•	Expand MavenJava → src → main → java → SE → MavenJava
•	Double-click App.java
You’ll see code like:
package SE.MavenJava;

public class App {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
2. Run Maven lifecycle (Clean → Install → Test → Build)
Right-click App.java →
1.	Run As → Maven clean
2.	Run As → Maven install
3.	Run As → Maven test
4.	Run As → Maven build…
o	In the dialog, in Goals type:
o	clean install test
o	Click Apply → Run
In the Console you should see BUILD SUCCESS.
3. Run Java program
Right-click App.java →
Run As → Java Application
In the console you get:
Hello World!
✅ Maven Java project is working.
________________________________________
5️⃣ Create Maven Web Project (MavenWeb)
1. New Maven Project
File → New → Maven Project
•	Uncheck Create a simple project (skip archetype selection)
•	Click Next
In the filter type: webapp
Select:
org.apache.maven.archetypes : maven-archetype-webapp : 1.4
Click Next
Fill:
•	Group Id: SE
•	Artifact Id: MavenWeb
Click Finish
(If console asks for Y, type Y again)
2. Open index.jsp
In Project Explorer:
MavenWeb
 └─ src
     └─ main
         └─ webapp
             └─ index.jsp
Double-click index.jsp and you’ll see HTML “Hello World”.
________________________________________
6️⃣ Add Servlet Dependency in pom.xml
1.	Open browser → https://mvnrepository.com
2.	Search → javax servlet api (or jakarta servlet, depending on Tomcat)
3.	Open latest version suited for your Tomcat (for Tomcat 9, javax 4.0.1 is fine).
4.	Copy the Maven dependency snippet.
Example:
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>4.0.1</version>
    <scope>provided</scope>
</dependency>
5.	Open MavenWeb/pom.xml in Eclipse.
6.	Inside <dependencies> tag, paste this dependency.
7.	Save (Ctrl + S).
________________________________________
7️⃣ Configure Tomcat in Eclipse
1. Show Servers view
Menu: Window → Show View → Servers
At bottom you’ll see “No servers are available.”
Click the link or right-click area → New → Server
2. Add Tomcat server
•	Select: Apache → Tomcat v9.0 (or v11 if that’s what you installed)
•	Click Next
•	Browse and select your Tomcat installation folder
•	Click Finish
3. Configure Ports
•	Double-click on the Tomcat v9.0 Server at localhost entry in Servers view.
•	In Server Locations, select:
o	Use Tomcat installation (2nd option)
•	Set ports:
o	HTTP/1.1 → 8085
o	Admin port → 0
•	Save (Ctrl + S) and close tab.
________________________________________
8️⃣ Build and Run Maven Web Project
1. Build using Maven
Right-click index.jsp:
1.	Run As → Maven clean
2.	Run As → Maven install
3.	Run As → Maven test
4.	Run As → Maven build…
o	Goals:
o	clean install test
o	Run → Check BUILD SUCCESS in console.
2. Run on Tomcat
Right-click index.jsp →
Run As → Run on Server
•	Choose Use existing server → select Tomcat v9.0
•	Click Finish
Browser tab opens with:
http://localhost:8085/MavenWeb/
and shows Hello World web page.
✅ Maven Web project is working.
________________________________________
9️⃣ Push Maven Projects from Eclipse to GitHub
We’ll push MavenJava & MavenWeb separately to two repos.
💻 A. Create GitHub Repositories
On GitHub:
1.	Click New repository
2.	For Java project:
o	Name: MavenJava_Project (or anything)
o	Keep Public/Private as required
o	Click Create repository
o	Don’t add README (optional)
3.	Repeat for Web project:
o	Name: MavenWeb_Project
You now have two empty repos with HTTPS URLs like:
https://github.com/mokshitha10/MavenJava_Project.git
https://github.com/mokshitha10/MavenWeb_Project.git
________________________________________
💻 B. Push MavenJava from Eclipse workspace
1. Open Git Bash inside project
In Eclipse:
•	Right-click MavenJava project folder in Project Explorer
•	Select: Show In → System Explorer or Show in Local Terminal → Git Bash
(if you have that option)
If you opened System Explorer:
•	In the file explorer, go to the project folder (where pom.xml is)
•	Right-click → Git Bash Here
You should be in a path like:
C:\Users\moksh\eclipse-workspace\MavenJava
2. Initialize Git & set branch
git init
git branch -M main
(Optional) set username/email once globally:
git config --global user.name "Your Name"
git config --global user.email "yourmail@gmail.com"
3. Add remote & push
git remote add origin https://github.com/mokshitha10/MavenJava_Project.git
git add .
git commit -m "Initial MavenJava project commit"
git push -u origin main
Login popup may appear → use GitHub credentials or token.
Go to GitHub → refresh → you’ll see all MavenJava files.
________________________________________
💻 C. Push MavenWeb project
Repeat same steps for MavenWeb:
1.	Right-click MavenWeb → Show in System Explorer or Git Bash Here
2.	In Git Bash:
git init
git branch -M main
git remote add origin https://github.com/mokshitha10/MavenWeb_Project.git
git add .
git commit -m "Initial MavenWeb project commit"
git push -u origin main
Refresh GitHub repo → files appear.
________________________________________
WEEK 5
Perfect, now let’s write one clean Week-5 procedure that you can follow + write in record.
I’ll include Dockerfile creation from CMD exactly like you asked.
________________________________________
🔹 PART 0 – Before Starting
1.	Start Docker Desktop (icon in taskbar).
2.	Open Command Prompt / PowerShell (you’re already using this 👍).
3.	Check Docker is working:
4.	docker version
If it prints client & server info → you’re ready.
________________________________________
🔹 PART 1 – Docker CLI with Official redis Image
Step 1: Pull Redis image
docker pull redis
Step 2: Run a Redis container
docker run --name my-redis -d redis
•	--name my-redis → container name
•	-d → runs in background (detached)
Step 3: Check running containers
docker ps
You should see my-redis in the list.
Step 4: Go inside Redis (redis-cli)
docker exec -it my-redis redis-cli
Inside redis prompt (127.0.0.1:6379>), run:
SET name "Alice"
GET name
exit
Step 5: Stop the container
docker stop my-redis
Step 6: Start it again (optional)
docker start my-redis
Step 7: Remove the container
Container must be stopped before removing.
docker stop my-redis
docker rm my-redis
Step 8: Remove the Redis image
docker rmi redis
Up to here = Part 1 of lab done ✅
________________________________________
🔹 PART 2 – Dockerfile (created from CMD)
We will:
•	Create folder C:\DockerProject\Redis
•	Create Dockerfile using CMD
•	Build custom image redisnew
•	Run container myredisnew
Step 1: Create and go to folder
In Command Prompt:
mkdir C:\DockerProject\Redis
cd C:\DockerProject\Redis
Step 2: Create Dockerfile from CMD
Run these two commands exactly:
echo FROM redis:latest > Dockerfile
echo CMD ["redis-server"] >> Dockerfile
✅ Now check file:
type Dockerfile
You should see:
FROM redis:latest
CMD ["redis-server"]
This file has no extension – it’s just Dockerfile.
Step 3: Build custom image
docker build -t redisnew .
•	-t redisnew → image name/tag
•	. → use Dockerfile in current folder
If successful, you’ll see Successfully tagged redisnew:latest.
Step 4: Run container from this image
docker run --name myredisnew -d redisnew
Step 5: Check it is running
docker ps
You should see myredisnew using image redisnew.
Step 6: Open redis-cli inside it
docker exec -it myredisnew redis-cli
Inside redis:
SET name "Abcdef"
GET name
exit
Step 7: Stop this container
docker stop myredisnew
(You can remove it later after Docker Hub part.)
________________________________________
🔹 PART 3 – Create Image from Container & Push to Docker Hub
🔐 You need a Docker Hub account first: https://hub.docker.com
Replace YOURUSERNAME everywhere with your Docker Hub username.
Step 1: Login to Docker Hub
docker login
Enter username & password.
Step 2: Get container ID of myredisnew
docker ps -a
Note the CONTAINER ID of myredisnew, e.g. 0e993d2009a1.
Step 3: Commit container as new image
docker commit 0e993d2009a1 YOURUSERNAME/redis1
(Use your actual container ID.)
Step 4: Check images
docker images
You should see YOURUSERNAME/redis1.
Step 5: Push image to Docker Hub
docker push YOURUSERNAME/redis1
✅ Now your image is public/private on Docker Hub.
Step 6: Clean up local container & image
docker rm myredisnew
docker rmi YOURUSERNAME/redis1
docker rmi redisnew
Check:
docker ps -a
docker images
________________________________________
🔹 PART 4 – Pull Your Own Image & Test Again
Step 1: Pull from Docker Hub
docker pull YOURUSERNAME/redis1
Step 2: Run container from this image
docker run --name myredis -d YOURUSERNAME/redis1
Step 3: Open redis-cli and test
docker exec -it myredis redis-cli
Inside redis:
SET name "TestName"
GET name
exit
Step 4: Stop and remove everything
docker stop myredis
docker rm myredis
docker rmi YOURUSERNAME/redis1
(Optional) log out of Docker Hub:
docker logout
________________________________________
WEEK 6 
🧾 WEEK 6 – Docker Compose (Complete Practical Steps)
📌 Before starting
Make sure:
✔ Docker Desktop is running
✔ Command Prompt / PowerShell is open
Verify Docker Compose is available:
docker compose version
If it prints version → you’re ready.
________________________________________
🔥 PART 1 — Create and run multi-container setup (Nginx + PostgreSQL)
✔ Step 1: Create project folder
mkdir C:\compose-lab
cd C:\compose-lab
✔ Step 2: Create docker-compose.yml
Run this from CMD to create the file:
notepad docker-compose.yml
Paste this inside and save:
version: "3.9"
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: demo
      POSTGRES_PASSWORD: demo
      POSTGRES_DB: demo_db
✔ Step 3: Start containers
docker compose up -d
-d = run in background
✔ Step 4: Check containers
docker compose ps
✔ Step 5: View output
Open browser:
http://localhost:8080
👉 You should see Nginx Welcome Page
PostgreSQL runs in background.
________________________________________
🔥 PART 2 — Add Redis + depends_on
✔ Step 1: Modify yaml file
Open YAML again:
notepad docker-compose.yml
Add at bottom ⬇
  redis:
    image: redis:alpine
Add depends_on to web service:
    depends_on:
      - redis
Final updated file summary:
version: "3.9"
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    depends_on:
      - redis

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: demo
      POSTGRES_PASSWORD: demo
      POSTGRES_DB: demo_db

  redis:
    image: redis:alpine
✔ Step 2: Restart
docker compose up -d
docker compose ps
Expected →
web    running
db     running
redis  running
________________________________________
🔥 PART 3 — Persistent Storage + Custom Network
✔ Step 1: Update YAML
Open file:
notepad docker-compose.yml
Replace content with:
version: "3.9"

networks:
  app-net:

volumes:
  db-data:

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    networks:
      - app-net
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: demo
      POSTGRES_PASSWORD: demo
      POSTGRES_DB: demo_db
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - app-net
✔ Step 2: Run + Stop + Run again
docker compose up -d
docker compose down
docker compose up -d
Expected →
🔥 Even after restart, PostgreSQL data persists.
________________________________________
🔥 PART 4 — Fast Iteration: Flask + Docker Compose
📁 Folder structure should look like:
compose-lab/
 ├ app.py
 ├ Dockerfile
 └ docker-compose.yml
✔ Step 1: Create Flask app
notepad app.py
Paste:
from flask import Flask
app = Flask(__name__)
@app.route("/")
def home():
    return "Hello from Flask + Docker!"
if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
✔ Step 2: Dockerfile
notepad Dockerfile
Paste:
FROM python:3.10-slim
WORKDIR /app
COPY app.py /app/
RUN pip install flask
CMD ["python", "app.py"]
✔ Step 3: Add web build config in docker-compose.yml
Modify:
  web:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - db
✔ Step 4: Build and run
docker compose up --build
Open browser:
http://localhost:5000
Edit app.py text and save
Then reload browser → updated output appears 🤩
________________________________________
📌 Important Commands Summary
Action	Command
Start containers	docker compose up -d
Stop containers	docker compose down
List running services	docker compose ps
Rebuild after code change	docker compose up --build
Scale service	docker compose up --scale web=2 -d
________________________________________
Week 7
Okay, I will convert WEEK 7 – MAVEN into a very clear, step-by-step, easy-to-follow practical guide just like Week 5 and Week 6.
No confusion — only what to do, how to do, where to click, what to run.
________________________________________
🚀 WEEK 7 – MAVEN (FULL LAB ACTION PLAN — CRYSTAL CLEAR PRACTICAL GUIDE)
🔥 PART 1 — Understanding Maven Folder Structure
When you create a Maven project, the structure is always:
project/
 ├─ src/
 │   ├─ main/
 │   │    ├─ java/          → Application .java code
 │   │    └─ resources/     → Files like config.properties, static files
 │   └─ test/
 │        ├─ java/          → Unit test .java code
 │        └─ resources/     → Test resources
 ├─ pom.xml                  → Main Maven configuration file
 └─ target/                  → Generated after build (class, JAR/WAR)
________________________________________
🔥 PART 2 — Basic Maven Commands
You will use only these:
Action	Command
Clean old build	mvn clean
Build + Test	mvn install
Run tests only	mvn test
Build without tests	mvn install -DskipTests
Package JAR/WAR	mvn package
Main command you run most:
mvn clean install
________________________________________
🔥 PART 3 — Creating a Maven Java Project in Eclipse
✔ Step-by-step
1️⃣ Open Eclipse
2️⃣ File → New → Project → Maven → Maven Project → Next
3️⃣ Keep default workspace → Next
4️⃣ Select archetype:
org.apache.maven.archetypes → maven-archetype-quickstart 1.4
→ Next
5️⃣ Enter:
Group Id: com.example
Artifact Id: my-maven-project
→ Finish
6️⃣ If console asks "Y/N", type → Y
Result
Your project is generated → you will see:
src/main/java
src/test/java
pom.xml
________________________________________
🔥 PART 4 — Build the Project
Right-click on project → Run As → Maven clean
Then:
Right-click on project → Run As → Maven install
Check console → must show:
BUILD SUCCESS
To run Java program:
Right-click App.java → Run As → Java Application
________________________________________
🔥 PART 5 — Add Dependency to Maven
Dependency = library.
Example: add Gson dependency.
Open pom.xml → paste inside <dependencies>:
<dependency>
  <groupId>com.google.code.gson</groupId>
  <artifactId>gson</artifactId>
  <version>2.10</version>
</dependency>
Then run:
mvn clean install
Gson JAR will download into:
C:\Users\<name>\.m2\repository
________________________________________
🔥 PART 6 — Creating a Maven Web Project
Steps:
1.	File → New → Project → Maven → Maven Project
2.	Next → Next
3.	Choose archetype:
maven-archetype-webapp 1.4
4.	Enter:
Group Id: com.example
Artifact Id: my-web-app
→ Finish
Add servlet dependency
Go to mvnrepository.com → search Java Servlet API
Copy latest dependency → paste in pom.xml:
<dependency>
  <groupId>javax.servlet</groupId>
  <artifactId>javax.servlet-api</artifactId>
  <version>4.0.1</version>
  <scope>provided</scope>
</dependency>
Configure Tomcat
Window → Show View → Servers
Add → Tomcat 9 → Next → Browse Tomcat folder → Finish
Build Web Project
Right-click on project → Run As → Maven clean
Right-click on project → Run As → Maven install
If BUILD SUCCESS → you can deploy
Right-click index.jsp → Run As → Run on Server
Browser output → Hello World webpage
________________________________________
🔥 PART 7 — Configure Java Version (compiler plugin)
Paste inside <build> section of pom.xml:
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-compiler-plugin</artifactId>
  <version>3.11.0</version>
  <configuration>
    <source>17</source>
    <target>17</target>
  </configuration>
</plugin>
Run:
mvn package
________________________________________
🔥 PART 8 — JUnit Test & Reports
Add a test class under:
src/test/java
Example:
@Test
public void testSum() {
    assertEquals(5, 2 + 3);
}
Run:
mvn test
Check reports:
target/test-classes
target/surefire-reports
________________________________________
🔥 PART 9 — Create Executable JAR
Add plugin in pom.xml:
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-jar-plugin</artifactId>
  <configuration>
    <archive>
      <manifest>
        <mainClass>com.example.Main</mainClass>
      </manifest>
    </archive>
  </configuration>
</plugin>
Run:
mvn package
java -jar target/myapp.jar
________________________________________
🔥 PART 10 — Build WAR
Add:
<packaging>war</packaging>
Run:
mvn clean install
WAR file appears:
target/mywebapp.war
→ Deploy on Tomcat
________________________________________
🔥 PART 11 — Multi-Module Maven Project (Parent–Child)
📌 Condition → Parent packaging type must be pom
Parent
MultiModule
 |— pom.xml  (packaging = pom)
 |— child1
 |— child2
To link child2 depends on child1 → add:
<dependency>
  <groupId>KMIT</groupId>
  <artifactId>MultimoduleChild1</artifactId>
  <version>0.0.1-SNAPSHOT</version>
</dependency>
Build order:
parent → child1 → child2
________________________________________
⭐ WEEK 8 — PART I
Maven Java Project Automation Using Jenkins
(Full, detailed, easy-to-understand explanation)
________________________________________
🔵 Introduction
In this task, we automate the building and testing of a Maven Java project using Jenkins.
We create two Jenkins jobs:
1.	MavenJava_Build → Build the code
2.	MavenJava_Test → Test the built code
Then we connect them in a pipeline view to visualize the workflow.
________________________________________
⭐ STEP 1 — Open Jenkins Dashboard
•	Open browser → type:
•	http://localhost:8080
•	This opens Jenkins home page.
________________________________________
⭐ STEP 2 — Create First Job (MavenJava_Build)
This job downloads code from GitHub and runs Maven build commands.
✔ 1. Click New Item
(left side menu)
✔ 2. Enter item name:
MavenJava_Build
✔ 3. Select:
Freestyle Project
Click OK
________________________________________
⭐ STEP 3 — Configure MavenJava_Build
✔ A. Description
Write something meaningful:
Java Build demo
________________________________________
✔ B. Source Code Management → Git
•	Select Git
•	Paste your GitHub repo URL of the Maven Java project
•	Example:
•	https://github.com/username/maven-java-demo
•	Branch to build:
•	*/main
or:
*/master
________________________________________
✔ C. Build Steps
🔹 Build Step 1
Add build step → Invoke top-level Maven targets
Fill:
•	Maven version: MAVEN_HOME
•	Goals:
•	clean
🔹 Build Step 2
Add build step → Invoke top-level Maven targets
Fill:
•	Maven version: MAVEN_HOME
•	Goals:
•	install
This compiles the project and creates a JAR file.
________________________________________
✔ D. Post-Build Actions
🔹 Action 1 — Archive the artifacts
•	Add Post-build Action → Archive the artifacts
•	Files:
•	**/*
This stores the build output in Jenkins.
________________________________________
🔹 Action 2 — Trigger Next Job
•	Add Post-build Action → Build other projects
•	Projects to build:
•	MavenJava_Test
•	Trigger:
✔ Only if build is stable
This links Build → Test.
________________________________________
✔ E. Save
Click:
•	Apply
•	Save
________________________________________
⭐ STEP 4 — Create Second Job (MavenJava_Test)
This job tests the code built in the first job.
✔ 1. Go to Dashboard → Click New Item
✔ 2. Enter name:
MavenJava_Test
✔ 3. Choose:
✔ Freestyle project
Click OK
________________________________________
⭐ STEP 5 — Configure MavenJava_Test
✔ A. Description
Test demo
________________________________________
✔ B. Build Environment
Check:
✔ Delete workspace before build starts
This ensures fresh workspace every time.
________________________________________
✔ C. Build Step — Copy artifacts
(Requires “Copy Artifact Plugin”)
Click:
Add build step → Copy artifacts from another project
Fill:
•	Project name:
•	MavenJava_Build
•	Build:
✔ Stable build only
•	Artifacts to copy:
•	**/*
This copies output from the first job.
________________________________________
✔ D. Build Step — Run Tests
Click:
Add build step → Invoke top-level Maven targets
Fill:
•	Maven version: MAVEN_HOME
•	Goals:
•	test
This runs JUnit tests.
________________________________________
✔ E. Post-build Action — Archive Test Output
Click:
Add Post-build Action → Archive the artifacts
Files:
**/*
________________________________________
✔ F. Save
Click:
✔ Apply
✔ Save
________________________________________
⭐ STEP 6 — Create Pipeline View
This gives a visual representation of job execution.
✔ 1. Go to Dashboard
✔ 2. Click “+” (New View)
✔ 3. Enter:
MavenJava_Pipeline
✔ 4. Select:
Build Pipeline View
Click OK
________________________________________
⭐ STEP 7 — Configure Pipeline View
✔ A. Layout:
Based on upstream/downstream relationship
✔ B. Initial Job:
MavenJava_Build
Click:
✔ Apply
✔ Save
________________________________________
⭐ STEP 8 — Run the Pipeline
•	Go to:
MavenJava_Pipeline
•	Click Run
•	Jenkins will execute:
1.	MavenJava_Build
2.	MavenJava_Test (automatically)
✔ If GREEN → Success
✔ If RED → Error (check console)
Click each build box → view console output & artifacts.
________________________________________
⭐ WEEK 8 — PART II
Maven Web Project Automation Using Jenkins
(Build → Test → Deploy → Tomcat → Pipeline)
________________________________________
🔵 Introduction
In this part, we automate a Maven Web (WAR) application using Jenkins.
We create:
1️⃣ MavenWeb_Build → Download code + build WAR
2️⃣ MavenWeb_Test → Test the web project
3️⃣ MavenWeb_Deploy → Deploy WAR file to Tomcat
4️⃣ MavenWeb_Pipeline → Visual pipeline view
5️⃣ Open browser → view deployed web app
This completes CI/CD for a web application.
________________________________________
⭐ STEP 1 — Create Job: MavenWeb_Build
✔ 1. Go to Dashboard → Click New Item
✔ 2. Enter name:
MavenWeb_Build
✔ 3. Choose:
✔ Freestyle Project
Click OK
________________________________________
⭐ STEP 2 — Configure MavenWeb_Build
✔ A. Description
Web Build demo
________________________________________
✔ B. Source Code Management → Git
Select Git
Paste your Maven Web GitHub repo URL, example:
https://github.com/yourusername/maven-web-demo
Branch:
*/main
or
*/master
________________________________________
✔ C. Build Steps
🔹 Build Step 1 — Clean
Click:
Add build step → Invoke top-level Maven targets
Fill:
•	Maven version: MAVEN_HOME
•	Goals:
•	clean
🔹 Build Step 2 — Install
Click:
Add build step → Invoke top-level Maven targets
Fill:
•	Maven version: MAVEN_HOME
•	Goals:
•	install
This will generate:
target/*.war
________________________________________
✔ D. Post-build Actions
🔹 Action 1 — Archive artifacts
Click:
Add Post-build Action → Archive the artifacts
Files:
**/*
This saves WAR file in Jenkins.
________________________________________
🔹 Action 2 — Build other projects
Click:
Add Post-build Action → Build other projects
Fill:
•	Projects to build:
•	MavenWeb_Test
•	Trigger:
✔ Only if build is stable
This links Build → Test.
________________________________________
✔ E. Save
Click:
✔ Apply
✔ Save
________________________________________
⭐ STEP 3 — Create Job: MavenWeb_Test
✔ 1. Dashboard → New Item
✔ 2. Enter:
MavenWeb_Test
✔ 3. Choose Freestyle Project
Click OK
________________________________________
⭐ STEP 4 — Configure MavenWeb_Test
✔ A. Description
Test demo
________________________________________
✔ B. Build Environment
Check:
✔ Delete workspace before build starts
________________________________________
✔ C. Copy Artifacts from Build Job
Click:
Add build step → Copy artifacts from another project
Fill:
•	Project name:
•	MavenWeb_Build
•	Which build:
✔ Stable build only
•	Artifacts to copy:
•	**/*
________________________________________
✔ D. Build Step — Run Maven Tests
Click:
Add build step → Invoke top-level Maven targets
Fill:
•	Maven version: MAVEN_HOME
•	Goals:
•	test
________________________________________
✔ E. Post-build Action — Archive Artifacts
Click:
Add Post-build Action → Archive the artifacts
Files:
**/*
________________________________________
✔ F. Post-build — Trigger Deploy Job
Click:
Add Post-build Action → Build other projects
Fill:
MavenWeb_Deploy
________________________________________
✔ G. Save
Click:
✔ Apply
✔ Save
________________________________________
⭐ STEP 5 — Create Job: MavenWeb_Deploy
✔ 1. Dashboard → New Item
✔ 2. Enter:
MavenWeb_Deploy
✔ 3. Choose Freestyle Project
Click OK
________________________________________
⭐ STEP 6 — Configure MavenWeb_Deploy
✔ A. Description
Web Code Deployment
________________________________________
✔ B. Build Environment
Check:
✔ Delete workspace before build starts
________________________________________
✔ C. Copy WAR from Test Job
Click:
Add build step → Copy artifacts from another project
Fill:
•	Project name:
•	MavenWeb_Test
•	Build:
✔ Stable build only
•	Artifacts to copy:
•	**/*.war
________________________________________
⭐ STEP 7 — Deploy WAR to Tomcat
You must have Tomcat installed.
✔ A. Post-build → Deploy WAR/EAR to a container
Click:
Add Post-build Action → Deploy WAR/EAR to a container
Fill:
•	WAR/EAR files:
•	**/*.war
•	Context path:
•	webpath
(This will create: localhost:8085/webpath)
________________________________________
✔ B. Add Container → Tomcat 9.x Remote
Fill:
Credentials:
•	Username: admin
•	Password: 1234
Tomcat URL:
http://localhost:8085/
________________________________________
✔ C. Save
Click:
✔ Apply
✔ Save
________________________________________
⭐ STEP 8 — Create MavenWeb_Pipeline View
✔ 1. Go to Dashboard → Click + (New View)
✔ 2. Enter:
MavenWeb_Pipeline
✔ 3. Choose:
Build Pipeline View
Click OK
________________________________________
⭐ STEP 9 — Configure the Pipeline View
Fill:
✔ Layout:
Based on upstream/downstream relationship
✔ Initial Job:
MavenWeb_Build
Click:
✔ Apply
✔ Save
________________________________________
⭐ STEP 10 — Run the Full Pipeline
In MavenWeb_Pipeline:
Click ▶️ Run
You will see:
1.	MavenWeb_Build (green)
2.	MavenWeb_Test (green)
3.	MavenWeb_Deploy (green)
Pipeline is successful when all turn GREEN.
________________________________________
⭐ STEP 11 — View the Deployed Web App
Open browser:
http://localhost:8085/webpath
You should see your web project output (index.jsp or servlet response).
________________________________________




















________________________________________
⭐ WEEK 9: Pipeline Creation Using Script
________________________________________
1. Aim
To create a Jenkins Scripted Pipeline for a Maven Java project, configure build triggers, and execute all stages using a Groovy-based Jenkinsfile.
________________________________________
2. Procedure
✔ Step 1 — Open Jenkins
Go to:
http://localhost:8080
✔ Step 2 — Create a New Pipeline Job
•	Click New Item
•	Name:
•	Pipeline_Script_MavenJava
•	Select: Pipeline
•	Click OK
________________________________________
3. General Section
Write:
This project demonstrates scripted pipeline execution for Maven Java using Jenkins.
________________________________________
4. Build Triggers
Choose any (your choice), example:
H/5 * * * *
(Triggers every 5 minutes.)
________________________________________
5. Advanced Project Options
Set:
Definition → Pipeline Script
Paste the full script (given below).
________________________________________
⭐ 6. Complete Script for Week 9 (FINAL VERSION)
✅ Works
✅ Tested
✅ Success on your system
➡️ Copy-paste exactly this:
pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    stages {

        stage('git repo & clean') {
            steps {
                bat "git clone https://github.com/mokshitha10/MavenJava_Project.git"
                bat "mvn clean -f MavenJava_Project"
            }
        }

        stage('install') {
            steps {
                bat "mvn install -f MavenJava_Project"
            }
        }

        stage('test') {
            steps {
                bat "mvn test -f MavenJava_Project"
            }
        }

        stage('package') {
            steps {
                bat "mvn package -f MavenJava_Project"
            }
        }
    }
}

If it is failing go to setting tools add maven home there apache url
⭐ WEEK 10 — WORKING WITH MINIKUBE, KUBERNETES & NAGIOS
________________________________________
⭐ 1. Aim
To deploy and manage applications using Minikube (Kubernetes), scale pods, expose services, monitor systems using Nagios, and create an AWS free-tier account.
________________________________________
⭐ 2. Tools Used
•	Minikube
•	kubectl
•	Docker Desktop
•	Nagios Monitoring Tool
•	AWS Free Tier
________________________________________
⭐ 3. Concepts Overview
🔵 Kubernetes
A tool to automatically run, restart, scale, and manage containers.
🔵 Pod
Smallest deployable unit in Kubernetes.
A Pod contains one or more containers.
🔵 Minikube
A lightweight local Kubernetes cluster for practice.
🔵 Nagios
A monitoring tool that tracks:
•	Servers
•	Services
•	Applications
•	Alerts
________________________________________
⭐ 4. MINIKUBE INSTALLATION (EASY METHOD)
✔ Step 1 — Open PowerShell as Administrator
Search → PowerShell → Right-click → Run as Administrator
✔ Step 2 — Install Chocolatey
Set-ExecutionPolicy Bypass -Scope Process -Force; `
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
✔ Step 3 — Install Minikube
choco install minikube -y
✔ Step 4 — Install kubectl
choco install kubernetes-cli -y
________________________________________
⭐ 5. START MINIKUBE
If Docker Desktop is installed:
minikube start --driver=docker
Check status:
minikube status
If running → continue.
________________________________________
⭐ 6. DEPLOY NGINX APPLICATION IN KUBERNETES
✔ Step 1 — Create Deployment
kubectl create deployment mynginx --image=nginx
✔ Step 2 — Check Deployment & Pods
kubectl get deployments
kubectl get pods
✔ Step 3 — Describe Deployment
kubectl describe deployment mynginx
________________________________________
⭐ 7. EXPOSE THE DEPLOYMENT
Expose Nginx to port 80:
kubectl expose deployment mynginx --type=NodePort --port=80
Check service:
kubectl get svc
________________________________________
⭐ 8. SCALE THE DEPLOYMENT
Scale to 4 replicas:
kubectl scale deployment mynginx --replicas=4
Check pods:
kubectl get pods
You should see 4 Running pods.
________________________________________
⭐ 9. ACCESS THE NGINX PAGE
Method 1 — Port Forward
kubectl port-forward svc/mynginx 8081:80
Open:
http://localhost:8081
Method 2 — Using Minikube
minikube service mynginx --url
Open the generated URL.
________________________________________
⭐ 10. MINIKUBE DASHBOARD (OPTIONAL)
minikube dashboard
________________________________________
⭐ 11. CLEANUP
kubectl delete deployment mynginx
kubectl delete service mynginx
minikube stop
________________________________________
⭐ 12. NAGIOS USING DOCKER
✔ Step 1 — Pull Nagios Image
docker pull jasonrivers/nagios:latest
✔ Step 2 — Run Nagios
docker run --name nagiosdemo -p 8888:80 jasonrivers/nagios:latest
✔ Step 3 — Access Dashboard
Open browser:
http://localhost:8888
Login:
•	Username: nagiosadmin
•	Password: nagios
Inside you can view:
•	Hosts
•	Services
•	Alerts
✔ Step 4 — Stop Nagios
docker stop nagiosdemo
docker rm nagiosdemo
________________________________________
⭐ WEEK 11 – PART 1: Jenkins CI using GitHub Webhooks (Detailed, Simple Explanation)
This part explains how GitHub automatically triggers Jenkins whenever you push code.
________________________________________
🧩 1. Why do we use Webhooks?
Normally Jenkins pulls (checks) GitHub again and again to see if there is any update.
This wastes time.
Webhooks solve it:
👉 GitHub pushes a notification instantly to Jenkins
👉 Jenkins automatically starts the build
👉 No need to click “Build Now”
This is Continuous Integration (CI).
________________________________________
🧩 2. Why ngrok is needed?
GitHub needs to send a message to Jenkins.
But Jenkins running on localhost cannot be accessed by GitHub, because it is inside your PC.
ngrok creates a public internet URL → which connects to → your local Jenkins.
Example:
https://offerable-unprovidentially-elyse.ngrok-free.dev -> http://localhost:8080
Now GitHub can reach your Jenkins.
________________________________________
🧩 3. Steps to set up Webhook Integration
Step 1: Start ngrok tunnel
Run:
ngrok http 8080
You get a public URL like:
https://offerable-unprovidentially-elyse.ngrok-free.dev
This becomes your Jenkins URL for GitHub.
________________________________________
Step 2: Add Webhook in GitHub
GitHub → Repo → Settings → Webhooks → Add Webhook
Fill:
✔ Payload URL
https://<ngrok-url>/github-webhook/
✔ Content type
application/json
✔ Trigger
Just the push event
👉 Click Add Webhook
GitHub will show a green ✔ if successful.
________________________________________
Step 3: Configure Jenkins Job
Jenkins → Your Job → Configure → Build Triggers
Enable:
✔ GitHub hook trigger for GITScm polling
Save.
This tells Jenkins:
“When GitHub sends a signal, start the build automatically.”
________________________________________
Step 4: Test the CI pipeline
1.	Edit any file in the GitHub repo (ex: README.md)
2.	Commit and push
3.	Jenkins will automatically start a build
4.	Console Output will show:
Started by GitHub push by mokshitha10
This confirms CI is working.
________________________________________
Here is everything from Week 11 explained clearly, briefly, and neatly — exactly as your lab wants.
I took all content from your uploaded file and rewrote it in clean, easy-to-understand steps.
📌 Cited from your file: 
________________________________________
🌟 WEEK 11 — JENKINS CI/CD + WEBHOOK + EMAIL SETUP (COMPLETE NOTES)
(Very easy, very neat, very clear)
________________________________________
🔵 PART 1 — CI USING GITHUB WEBHOOKS
✅ Goal:
Whenever you push code to GitHub → Jenkins should automatically build the project.
________________________________________
Step 1 — Configure Webhook in GitHub 
1️⃣ Open your GitHub repository
➡ Go to Settings → Webhooks
2️⃣ Click Add Webhook
3️⃣ In Payload URL, enter:
https://<YOUR_NGROK_URL>/github-webhook/
4️⃣ Set:
•	Content type: application/json
•	Events: ✔ Just the push event
5️⃣ Click Add Webhook
________________________________________
🔵 PART 2 — Setup & Run ngrok (to expose Jenkins to the internet)
(Because GitHub cannot access localhost directly)
1️⃣ Download ngrok
https://ngrok.com/download
2️⃣ Extract zip → you will get ngrok.exe
3️⃣ Add your auth token
Copy token from ngrok → Your Authtoken
Run in CMD:
ngrok config add-authtoken <your_token>
4️⃣ Start tunnel for Jenkins (port 8080)
ngrok http 8080
5️⃣ You will see:
Forwarding https://something.ngrok-free.dev -> http://localhost:8080
👉 Copy the HTTPS URL.
👉 Use that URL in your GitHub webhook.
________________________________________
🔵 PART 3 — Jenkins Accepts Webhooks 
1️⃣ Open Jenkins → your Job → Configure
2️⃣ Scroll to Build Triggers
Tick:
✔ GitHub hook trigger for GITScm polling
3️⃣ Save
________________________________________
🔵 PART 4 — TEST THE WEBHOOK
1️⃣ Edit any file in your repo
2️⃣ git add → git commit → git push
3️⃣ GitHub sends webhook → Jenkins receives it → Build starts automatically
🎉 WEBHOOK SUCCESSFUL
________________________________________
🌟 RESULT:
You created full CI automation:
GitHub Push → Webhook → Jenkins Build.
________________________________________
🟣 PART 5 — EMAIL NOTIFICATIONS (SUCCESS/FAILURE)
Step 1 — Generate Gmail App Password
(Normal password won’t work)
1️⃣ Go to:
https://myaccount.google.com
2️⃣ Enable 2-Step Verification
(Settings → Security → 2-Step Verification)
3️⃣ Create an App Password
Security → App Passwords
•	App: Other
•	Name: Jenkins
•	Click Generate
🔑 Copy the 16-digit password.
________________________________________
Step 2 — Install Plugin in Jenkins
Manage Jenkins → Manage Plugins
Install:
✔ Email Extension Plugin
________________________________________
Step 3 — Configure Global Email in Jenkins
Go to:
Manage Jenkins → Configure System
Fill:
Field	Value
SMTP Server	smtp.gmail.com
Use SMTP Auth	✔
Username	your Gmail
Password	your App Password
Use SSL	✔
SMTP Port	465
🔹 Click Test Configuration
You should receive a test mail.
________________________________________
Step 4 — Enable Email in a Job
Inside your job:
Post-Build Actions → Editable Email Notification
Fill:
•	Recipient list → your email
•	Trigger → ✔ Failure, ✔ Success
•	Content → default is fine
💾 Save
🎉 Now Jenkins sends email on success/failure.
________________________________________
🌟 WEEK 12 – FULL LAB (EXTREMELY EASY STEPS)
1. Deploy index.html on AWS EC2 using Docker
________________________________________
🟦 STEP 1 — Login to AWS Academy
1.	Open your course invitation email → click Start.
2.	Sign in to AWS Academy with your student account.
3.	Go to Modules → AWS Academy Learner Lab.
4.	Click Start Lab.
5.	Wait until the red AWS turns green → lab is ready.
________________________________________
🟦 STEP 2 — Create EC2 Instance
1.	Click AWS (top left).
2.	Search for EC2 → open it.
3.	Click Launch Instance.
4.	Fill these:
✔ Stage 1 → Instance Name
ubuntu-webserver
✔ Stage 2 → Choose AMI
Select: Ubuntu Server 20.04 LTS (Free Tier Eligible)
✔ Stage 3 → Architecture
Choose: 64-bit (x86)
✔ Stage 4 → Instance Type
t2.micro (free tier)
✔ Stage 5 → Create Key Pair
•	Click Create new key pair
•	Name: aws-key
•	Format: .pem
•	Download file → keep it safe
✔ Stage 6 → Network / Security Group
Tick all checkboxes:
✔ SSH
✔ HTTP
✔ HTTPS
(so your website loads)
✔ Stage 7 → Storage
Keep 8GB default
✔ Stage 8 → Launch Instance
Click Launch
Go to Instances → wait until Running + 2/2 checks passed
________________________________________
🟦 STEP 3 — Connect to EC2 via SSH
1.	Select the instance → click Connect.
2.	Choose SSH Client tab.
3.	Copy the command:
4.	ssh -i "aws-key.pem" ubuntu@<public-ip>
5.	Open PowerShell as Administrator.
6.	Go to folder where your .pem file is stored:
7.	cd <your pem folder>
8.	Paste the ssh command → press Enter.
You are now inside the Ubuntu server.
________________________________________
🟦 STEP 4 — Install Software on Ubuntu
Run these commands one by one:
✔ Update Ubuntu
sudo apt update
✔ Install Docker
sudo apt-get install docker.io
✔ Install Git
sudo apt install git
✔ Install nano editor
sudo apt install nano
________________________________________
🟦 STEP 5 — Create Web App & Push to GitHub
✔ A. Create a folder locally
Inside it, create:
index.html
✔ B. Open Git Bash inside folder
Run:
git init
git add .
git commit -m "first commit"
✔ C. Create new GitHub repo
Copy the HTTPS URL.
✔ D. Push your code
git branch -M main
git remote add origin <repo-url>
git push -u origin main
Your index.html is now in GitHub.
________________________________________
🟦 STEP 6 — Clone Repo on EC2
In the EC2 terminal:
git clone <your-repo-url>
cd <repo-folder>
________________________________________
🟦 STEP 7 — Create Dockerfile on EC2
Run:
nano Dockerfile
Paste this:
FROM nginx:latest
COPY . /usr/share/nginx/html
Save:
•	CTRL+O → Enter
•	CTRL+X
________________________________________
🟦 STEP 8 — Build & Run Docker Container
✔ Build Image
sudo docker build -t mywebapp .
✔ Run Container
sudo docker run -d -p 80:80 mywebapp
________________________________________
🟦 STEP 9 — View Website in Browser
1.	Go to EC2 → Instances → copy Public IPv4 address
2.	Paste in browser:
http://<your-public-ip>
Your index.html page should load.
________________________________________
🟦 STEP 10 — Stop Container
sudo docker ps
sudo docker stop <container-id>
________________________________________
🟦 STEP 11 — Terminate EC2 Instance
EC2 → select instance → Instance State → Terminate
You are done with Exercise 1.
________________________________________
🌟 EXERCISE 2 — Maven Web Project Deployment on EC2
________________________________________
🟣 Steps (Very Short & Clear)
✔ Create new EC2 instance
Same steps as Exercise 1 (Ubuntu + KeyPair + Security group + Launch).
✔ SSH into instance
Use the ssh -i command again.
✔ Install software
sudo apt update
sudo apt install git
sudo apt install docker.io
✔ Clone MAVEN WEB PROJECT from GitHub
Copy your repo link
git clone <maven-repo-url>
cd <project-folder>
✔ If your branch is not main
Change default branch in GitHub settings → set master to default.
✔ Build Docker image for Maven web app
sudo docker build -t mymavenapp .
✔ Run container on port 9090
sudo docker run -d -p 9090:8080 mymavenapp
✔ Open public IP with port
http://<public-ip>:9090
❗ If app does NOT load
Go to:
EC2 → Security Groups → Edit Inbound Rules → Add:
Custom TCP  |  9090  |  0.0.0.0/0
Save and refresh browser.
✔ Stop container
sudo docker ps
sudo docker stop <container-id>
✔ Terminate instance
EC2 → Instance → Terminate
________________________________________

