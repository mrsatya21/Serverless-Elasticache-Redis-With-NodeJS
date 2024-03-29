# Elasticache Redis (*Serverless*) with NodeJs in *Amazon Linux 2023*
This is a Repository that contains YAML CloudFormation template to create an ElastiCache Redis (Serverless) cluster with an Amazon Linux 2023 EC2 instance and connect to the Redis cluster with NodeJS. 

### NOTE: Only to be used in AWS CLOUD

#### This is a CloudFormation YAML template. 

This template can be used to create an ElastiCache Redis (Serverless) cluster with an Amazon Linux 2023 EC2 instance and connect to the Redis cluster with NodeJS.

1. Download the template to your local machine from the GitHub repository.

    ```sh
    wget https://raw.githubusercontent.com/mrsatya21/Serverless-Elasticache-Redis-With-NodeJS/main/template.yaml
    ```
2. Use the template to [create the Stack](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-create-stack.html) through AWS Console.

3. This stack will create an EC2 instance with name `Ec2InstanceForRedisServerless` and an ElastiCache cluster `redisserverless`in the region in which you create the stack. 

4. After creating the stack [connect to Ec2 instance `Ec2InstanceForRedisServerless`](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connect-linux-inst-ssh.html#connect-linux-inst-sshClient) and run the command -
    ```node 
    node /home/ec2-user/redis.js
    ```

5. You will get output something like this - 
    ```
    set ping dong:  OK
    get ping:  dong
    set ding pong:  OK
    get ding:  pong
    ```
