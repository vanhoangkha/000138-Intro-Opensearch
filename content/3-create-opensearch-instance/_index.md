---
title : "Create OpenSearch Instance"
date: 2024-01-01
weight : 3
chapter : false
pre : " <b> 3. </b> "
---
1. Open [Amazon OpenSearch Service console](https://ap-southeast-1.console.aws.amazon.com/aos/home?region=ap-southeast-1#opensearch/dashboard)

2. Click **Create domain**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-1.png?featherlight=false&width=90pc)

3. Enter domain name: `fcjdms`
    - Selecting deployment type is **Development and testing**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-2.png?featherlight=false&width=90pc)

4. In **Data nodes** section:
    - Select 1 availability zone
    - Select **t3.small.search** for instance type
    - Enter `2` for number of nodes
    - Select **General Purpose (SSD) - gp2** for **EC2 volume type**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-3.png?featherlight=false&width=90pc)

5. Expand the **Dedicated master nodes** section and check to **Enbale dedicated master nodes**
    - Selecting instance type is **t3.small.search**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-4.png?featherlight=false&width=90pc)

6. Select **Public access** for **Network**
    - Select **Create master user** 
    - Enter username, password and confirm password

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-5.png?featherlight=false&width=90pc)

7. In the **Access policy** section, select **Only use fine-grained access control**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-6.png?featherlight=false&width=90pc)

8. Scroll down to bottom and click **Create**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-7.png?featherlight=false&width=90pc)

9. Wait a few minutes for the domain to initialize

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-8.png?featherlight=false&width=90pc)

10. Once the domain is ready, note down the domain endpoint and click the OpenSearch Dashboards URL.

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-9.png?featherlight=false&width=90pc)

11. Open the AWS Lambda console. Select **search_docs** function
    - Select **Configuration** tab
    - Select **Environment variables** on the left menu
    - Click **Edit**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-10.png?featherlight=false&width=90pc)

12. Click **Add environment variable**
    - Enter `SEARCH_DOMAIN` for Key
    - Paste the OpenSearch domain endpoint to Value cell và delete **https://**
    - Click **Save**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-11.png?featherlight=false&width=90pc)

13. Repeat steps 11 and 12 for **load_stream** function
14. Back to the OpenSearch Dashboards tab, and enter the user information you created. Then press **Log in**.

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-12.png?featherlight=false&width=90pc)

15. Open the menu in the upper left corner and select **Security**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-13.png?featherlight=false&width=90pc)

16. Select **Roles** on the left menu.
    - Select **all_access**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-14.png?featherlight=false&width=90pc)

17. Select **Mapped users** tab and click **Manage mapping**.

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-15.png?featherlight=false&width=90pc)

18. In the **Backend roles** section:
    - Enter the Role ARN of role that the **search_docs** is executing.
    - Click **Add another backend role**
    - Enter the Role ARN of the role that the **load_stream** function is executing.
    - Click **Map**

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-16.png?featherlight=false&width=90pc)

19. You have completed map the Lambda role to a user of OpenSearch domain.

![CreateOpenSearch](/images/3-create-opensearch-instance/3-create-opensearch-instance-17.png?featherlight=false&width=90pc)