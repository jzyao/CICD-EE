
Create a new Freestyle project

Lock this project to Jenkins slave worker node

![free](/jenkins/images/free.jpg?raw=true "lock")


Add build step --> Execute shell. 

Please replace the <DTR_URL>, <password> with your own


···
DTR_USERNAME=admin
DTR_URL=<DTR_URL>
TAG=1

git clone https://github.com/jzyao/CIrepo.git

cd CIrepo

docker build -t $DTR_URL/admin/citest:$TAG .

docker login -u admin -p <password> $DTR_URL

docker push $DTR_URL/admin/citest:$TAG
···

Now let's run the build. Click Build now. 

You can watch the output of the Build by clicking on the task number in the Build History and then selecting Build Output 


The console output will show you all the details from the script execution. 

![consoleout](/jenkins/images/consoleout.jpg?raw=true "consoleout")


Review the ci/dc18 repository in DTR. You should now see a bunch of tags that have been promoted. 
![dtrresult](/jenkins/images/dtrresult.jpg?raw=true "dtrresult")

