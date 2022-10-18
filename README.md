### Built With

- [Jenkins](https://www.jenkins.io/) -  CI/CD tool
- [Amazon AWS](https://aws.amazon.com/) - Cloud services
- [AWS CLI](https://aws.amazon.com/cli/) - Command-line tool for AWS
- [Terraform](https://www.terraform.io/) - Infrastrcuture as code
- [Ansible](https://www.ansible.com/) - Configuration management tool

### More Details about this Project:
- This Project has three Nodes:
    - Master node (a container in my local machine with jenkins and docker installed on it)
    - Two slave nodes:
        - Another docker container in my local machine.
        - An AWS EC2 instance
- Each slave node uses a simple flask app hosted in my github account with this [link](https://github.com/MohamedAdelTaha/Simple_Flask_App.git)
- The flask app consists of three branches (master-dev-test), and each branch has its own Jenkins file.
- The master branch has been deployed in the master node.
    -Task:
        - simple task that echos hello from master branch.
- The dev branch has been deployed on the slave_container_node.
    - Tasks:
        - echos hello from dev branch.
        - get the application code from my github account.
        - build a docker image from this app using Dockerfile inside it.
        - push that image to my dockerhub repo using my credentials.
        - run a container from this image to test the app inside that slave_container_node.
        - send a slack notification to my channel to clarify whether all stages have succeeded or not.
- The test branch has been deployed on the slave_ec2_node.
    - Tasks:
        - echos hello from test branch.
        - get the application code from my github account.
        - build a docker image from this app using Dockerfile inside it.
        - run a container from this image to test the app inside that aws_ec2_slave_node.
        - send a slack notification to my channel to clarify whether all stages have succeeded or not.