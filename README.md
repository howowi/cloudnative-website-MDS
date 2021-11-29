# Cloud Native Website on OCI Container Engine for Kubernetes (OKE) and MySQL Database Service

![pattern](cloudnative-website-mds.png)

This pattern shows how to deploy a cloud native website on Oracle Cloud Infrastructure (OCI) Container Engine for Kubernetes (OKE) via Continuos Integration and Continuos Deployment (CICD) pipeline using OCI DevOps service and integrate with fully managed MySQL Database Service (MDS)

## **Overview:**

1) The website is built using **Nginx** and **PHP** as microservices and access MySQL Database Service.
2) Nginx is exposed as a service of type Load Balancer and it's listening on TCP port 5000. PHP and MySQL will not be exposed for external connectivity to reduce external attack surface.
3) Upon code commit to "main" branch, build pipeline will be triggered automatically to build and test the applications.
4) Deployment pipeline will be triggered automatically once build pipeline runs successfully to deploy application to test OKE cluster, test it, and deploy it to production OKE cluster.

## **1. Deploy OKE Cluster**

OCI provides one-click cluster deployment and will take care of creation of VCN, subnets, security list, Kubernetes Master and Worker Nodes.

## **2. Deploy MySQL Database Service**

```
Steps Here
```

## **3. Set up OCI DevOps CICD Pipeline**

### a. Create Project
```
Steps Here
```
### b. Create Code Repository
```
Steps Here
```
### c. Create Artifacts
```
Steps Here
```
### d. Create Environment
```
Steps Here
```
### e. Create Deployment Pipeline
```
Steps Here
```
### f. Create Build Pipeline
```
Steps Here
```
### g. Create Trigger
```
Steps Here
```

## **4. Trigger CICD Pipeline** 
```
Steps Here
```

## **PHP to MDS Integration Steps**
1. Access MDS host using Bastion

    a. Create Bastion session to MDS host

    b. Create port forwarding using Bastion
    ```
    ssh -i <privateKey> -N -L <localPort>:10.0.10.79:3306 -p 22 ocid1.bastionsession.oc1.uk-london-1.amaaaaaay5l3z3yadxxhqb2uyivjxudpvdielpfx6bsejxe2oz25wypxx7fq@host.bastion.uk-london-1.oci.oraclecloud.com
    ```
    c. Install mysql shell from https://dev.mysql.com/downloads/shell/

    d. Connect to MDS host
    ```
    mysqlsh -h 127.0.0.1 -p '<MDS password>' -u <MDS user>
    ```
    e. Create database. Switch to SQL mode by entering \sql before entering SQL statement.
    ```
    MySQL  127.0.0.1:3306 ssl  JS > \sql
    CREATE DATABASE webappdb;
    ```
    f. List all databases
    ```
    MySQL  127.0.0.1:3306 ssl  SQL > show databases;
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | webappdb           |
    +--------------------+
    ```

2. Create db schema in MDS
    a. Switch to the right database by executing the following SQL statement.
    ```sql
    use webappdb;
    ```
    a. Insert the following SQL statement in mysql shell to create table.
    ```sql
    CREATE TABLE `employee_data`(
    `id` int(11) NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `first_name` VARCHAR(50) NOT NULL,
    `last_name` VARCHAR(50) NOT NULL,
    `gender` VARCHAR(50) NOT NULL,
    `email` VARCHAR(50) NOT NULL,
    `hire_date` VARCHAR(50) NOT NULL,
    `department` VARCHAR(50) NOT NULL,
    `job` VARCHAR(50) NOT NULL,
    `salary` DECIMAL(10,2) NOT NULL
    )AUTO_INCREMENT=1;
    ```
    b. Check the tables
    ```sql
    show tables;
    ```
