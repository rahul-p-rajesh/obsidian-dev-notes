
## Why docker
1. Previous to docker we used to spin up a VM (Virtual machines) which were usually (2-10gb, takes 30sec to boot) a devops guy use to manually install all the dependency such as language, db, pull the code, build it run it etc.
2. in terms of verically scaling a new VM was spinned up and the same process was done again which was tedious.
3. Came in Containers which solved the same isolation problem **without duplicating the kernel**.


### What is containers
1. A container is not a VM. A container is not a special kind of process. 
2. A container **is** a regular Linux process — with restrictions applied by two kernel features.
3. Container = Process + Namespaces + Cgroup


#### What is a kernal
1. A kernal is a process that is responsible for communicating to the hardware.
2. Application code can communicate to the hardware via kernals only.
#### What is a namespace
1. namespace is the kernel's way of giving a process a **private, restricted view** of one of these resources.
2. 



### What is docker
Platform for building, shipping, and running applications inside **containers**



