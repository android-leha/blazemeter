# blazemeter

!!! Please remove my credentials from jenkins =)

/app - Docker application folder

/deployment - k8s deployments scripts 


2 stages:
- Build Dockerfile and push it to docker hub
- Deploy docker image on k8s


Job: http://35.209.163.141:8080/blue/organizations/jenkins/blazemeter/detail/master/19/pipeline


Multi branch pipeline is set to manual trigger(no polling).
To support several branches, need to add deployments 
in different namespaces (per branch name)
and different ingres paths
