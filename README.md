## Elasticache Redis *(serverless)* with NodeJs in *Amazon Linux 2023*
This is a Repository that contains YAML CloudFormation template to create an ElastiCache Redis *(serverless)* cluster with an *Amazon Linux 2023* EC2 instance and connect to the Redis cluster with 'NodeJS'. 

### Consideration/prerequisites 

- I have used the *Instance profile*, that I have in my account. I request everyone to change the *Instance profile* in the given template *(in line number [36](https://github.com/mrsatya21/Serverless-Elasticache-Redis-With-NodeJS/blob/main/template.yaml#L36))*.

- The *Instance profile*, that I have used was having *[AmazonSSMManagedInstanceCore](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AmazonSSMManagedInstanceCore.html)* policy attached to it, along with a custom policy that allows *DescribeStacks* and *ListStacks* policy. 

- I assume user(s) to have a little bit of knowledge about CloudFormation. 

- For LAZY people, use the template in branch **[WithInstanceProfile](https://github.com/mrsatya21/Serverless-Elasticache-Redis-With-NodeJS/blob/WithInstanceProfile/README.md)**.

- Select the *Security group* which is in default VPC. Otherwise, make sure your *Security group* is present in a VPC, which have at-least 3 subnet. 

- *Security group*, must be allowing Inbound/Outbound traffic to port 6379 *(default redis port)*. 

#### This is a CloudFormation YAML template. 

This template can be used to create an ElastiCache Redis *(serverless)* cluster with an *Amazon Linux 2023* EC2 instance and connect to the Redis cluster with NodeJS.

1. Download the template to your local machine from the GitHub repository.
    > ```sh
    > wget https://raw.githubusercontent.com/sattyagrah/Serverless-Elasticache-Redis-With-NodeJS/main/template.yaml
    > ```

2. Use the template to *[create the Stack](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-create-stack.html)* through AWS Console.

3. This stack will create an EC2 instance with name `Ec2InstanceForRedisServerless` and an ElastiCache cluster `redisserverless`in the region in which you create the stack. 

4. After creating the stack *[connect to Ec2 instance `Ec2InstanceForRedisServerless`](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connect-linux-inst-ssh.html#connect-linux-inst-sshClient)* and run the command -
    > ```sh 
    > [ "$(awk -F"'" '/const redisHost/ {print $2}' /home/ec2-user/redis.js)" == "" ] && echo "'redisHost' is empty." || node /home/ec2-user/redis.js
    > ```

5. You will get output something like this - 
    > ```
    > set ping dong:  OK
    > get ping:  dong
    > set ding pong:  OK
    > get ding:  pong
    > ```