IMPORTANT ❗ ❗ ❗ Please remember to destroy all the resources after each work session. You can recreate infrastructure by creating new PR and merging it to master.
  
![img.png](doc/figures/destroy.png)

1. Authors:

   Group number: 1

   Link to forked repo: https://github.com/JakubPrzesmycki/tbd-workshop-1.git
   
2. Follow all steps in README.md.
    
    Poniżej przedstawiamy efekt wykonania README.md, czym był poprawnie zrealizowany pull request oraz release.

    ![img.png](doc/figures/2.1.png)

    ![img.png](doc/figures/2.1.png)

3. Select your project and set budget alerts on 5%, 25%, 50%, 80% of 50$ (in cloud console -> billing -> budget & alerts -> create buget; unclick discounts and promotions&others while creating budget).

    Ustawione limity:

    ![img.png](doc/figures/3.png)

5. From avaialble Github Actions select and run destroy on main branch.
   
    ![img.png](doc/figures/5.png)

6. Create new git branch and:
    1. Modify tasks-phase1.md file.
    
    2. Create PR from this branch to **YOUR** master and merge it to make new release. 
    
    ![img.png](doc/figures/6.1.png)

    ![img.png](doc/figures/6.2.png)

    ![img.png](doc/figures/6_3.png)

7. Analyze terraform code. Play with terraform plan, terraform graph to investigate different modules.

    ***describe one selected module and put the output of terraform graph for this module here***
   
8. Reach YARN UI
   
    Pierwszym krokiem bylo zdefiniowanie zmiennych srodowiskowych:
     - export PROJECT=tbd-2023l-314241
     - export HOSTNAME=tbd-cluster-m
     - export ZONE=europe-west1-d
     - export PORT=1080
   
    Nastepnie utworzylismy tunel SSH przy pomocy komendy:
     - gcloud compute ssh ${HOSTNAME} --project=${PROJECT} --zone=${ZONE} -- -D ${PORT} -N

    Po wlaczeniu przegladarki "firefox", w ustawieniach sieci wybralismy manualna konfiguracje proxy.
    W sekcji SOCKS Host wprowadzilismy localhost oraz port, oraz zaznaczylismy opcje SOCKS v5.

    Koncowym etapem bylo przejscie do YARN UI, wykorzystujac  URL: http://tbd-cluster-m:8088/
        *(8088 to port dla YARN ResourceManager w daraproc)
    
    ![img.png](doc/figures/YARN_UI_1.png)

    ![img.png](doc/figures/YARN_UI_2.png)

9. Draw an architecture diagram (e.g. in draw.io) that includes:
    1. VPC topology with service assignment to subnets
    2. Description of the components of service accounts
    3. List of buckets for disposal
    4. Description of network communication (ports, why it is necessary to specify the host for the driver) of Apache Spark running from Vertex AI Workbech
  
    ***place your diagram here***

10. Create a new PR and add costs by entering the expected consumption into Infracost
For all the resources of type: `google_artifact_registry`, `google_storage_bucket`, `google_service_networking_connection`
create a sample usage profiles and add it to the Infracost task in CI/CD pipeline. Usage file [example](https://github.com/infracost/infracost/blob/master/infracost-usage-example.yml) 

   ***place the expected consumption you entered here***

   ***place the screenshot from infracost output here***

11. Create a BigQuery dataset and an external table using SQL
    
    ***place the code and output here***
   
    ***why does ORC not require a table schema?***

  
12. Start an interactive session from Vertex AI workbench:

    ***place the screenshot of notebook here***
   
13. Find and correct the error in spark-job.py

    ***describe the cause and how to find the error***

14. Additional tasks using Terraform:

    1. Add support for arbitrary machine types and worker nodes for a Dataproc cluster and JupyterLab instance

    ***place the link to the modified file and inserted terraform code***
    
    3. Add support for preemptible/spot instances in a Dataproc cluster

    ***place the link to the modified file and inserted terraform code***
    
    3. Perform additional hardening of Jupyterlab environment, i.e. disable sudo access and enable secure boot
    
    ***place the link to the modified file and inserted terraform code***

    4. (Optional) Get access to Apache Spark WebUI

    ***place the link to the modified file and inserted terraform code***
