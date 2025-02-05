
The cod efirst needs to be tested to making sure it's working prpoerly and then merged to the main branch
![](Pasted%20image%2020250205104651.png)

We are then going to delpoy this tested code to a virtual machine to make sure it's working correctly on the infastrucutre

![](Pasted%20image%2020250205105100.png)

Our trigger is a git push which is being listened to the change by a webhook.
e.g. a change is made and pushed and this is listened by Jenkins using a webhook
A **webhook** is telling one service to another service that something happened 

![](Pasted%20image%2020250205105251.png)

![](Pasted%20image%2020250205105349.png)

![](Pasted%20image%2020250205110605.png)

`Jenkins Server 1:  http://34.254.6.118:8080 `
`Jenkins Server 2:  http://52.31.15.176:8080`

Password in pass store


![](Pasted%20image%2020250205112030.png)

We first create a new item

![](Pasted%20image%2020250205112116.png)
Select a freestyle project

![](Pasted%20image%2020250205112634.png)

![](Pasted%20image%2020250205112839.png)

Execute shell build step

Different prjects can be split into different jobs

![](Pasted%20image%2020250205113029.png)

Then save it

The. job will sit in the worker node and wait till it's ready to do the job

the worker nodes is a vm jenkins makes, and does an action then deletes itself

Once the worker node has been idle for too long it dletes itself byy jenkins

![](Pasted%20image%2020250205113355.png)

We can see the 1 pipeline job by selecting 1

![](Pasted%20image%2020250205113458.png)

We can go to console output to see the sesult of what happens when our pipeline ran

This is running the command on that worker node

![](Pasted%20image%2020250205113552.png)

![](Pasted%20image%2020250205113744.png)

![](Pasted%20image%2020250205113820.png)

![](Pasted%20image%2020250205113921.png)

![](Pasted%20image%2020250205113938.png)

![](Pasted%20image%2020250205113956.png)
We can link it tgoether to make one job to ruun after the other
![](Pasted%20image%2020250205114832.png)

![](Pasted%20image%2020250205114955.png)

If we want to link another job to the first one we do this
first go to the first prject and navigate to here

![](Pasted%20image%2020250205115101.png)

Make sure there is no comma or space in the name

Think of each pipeline as a job, and if breakdown big tasks of things to do into small jobs and then link them together

![](Pasted%20image%2020250205115506.png)

You have to navigate to each job to see if the the cnhage you made was successful
![](Pasted%20image%2020250205115540.png)


Jenkins is an automation server, it can automate many things, not just CI/CD pipelines
