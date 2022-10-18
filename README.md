### Built With

- [Jenkins](https://www.jenkins.io/) -  CI/CD tool
- [Amazon AWS](https://aws.amazon.com/) - Cloud services
- [AWS CLI](https://aws.amazon.com/cli/) - Command-line tool for AWS
- [Terraform](https://www.terraform.io/) - Infrastrcuture as code
- [Ansible](https://www.ansible.com/) - Configuration management tool

### More Details about this Project:
- This Project has three Nodes:
    1- Master node (a container in my local machine with jenkins and docker installed on it)
    2- Two slave nodes:
        2.1. Another docker container in my local machine.
        2.2. An AWS EC2 instance
- Each slave node uses a simple flask app hosted in my github account with this [link](https://github.com/MohamedAdelTaha/Simple_Flask_App.git)
- The flask app consists of three branches (master-dev-test), and each branch has its own Jenkins file.
- The master branch has been deployed in the master node.
    -Task:
        - simple task that echos hello from master branch.
- The dev branch has been deployed on the slave_container_node.
    - Tasks:
        1- echos hello from dev branch.
        2- get the application code from my github account.
        3- build a docker image from this app using Dockerfile inside it.
        4- push that image to my dockerhub repo using my credentials.
        5- run a container from this image to test the app inside that slave_container_node.
        6- send a slack notification to my channel to clarify whether all stages have succeeded or not.
- The test branch has been deployed on the slave_ec2_node.
    - Tasks:
        1- echos hello from test branch.
        2- get the application code from my github account.
        3- build a docker image from this app using Dockerfile inside it.
        4- run a container from this image to test the app inside that aws_ec2_slave_node.
        5- send a slack notification to my channel to clarify whether all stages have succeeded or not.