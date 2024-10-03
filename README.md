# Apache_Solr_commands
Creating a Collection and Indexing the Employee Data in Apache Solr.
Prerequisite:
•	Java
•	Apache Solr

Step by Step Procedure:
1.	Open the Directory of the Apache Solr and open that path in the terminal.
2.	Then we have to start the Solr it is done by using the following command
`bin\solr start -c
`
![image](https://github.com/user-attachments/assets/89d88f0d-ec50-4327-b346-1e8b6f1a7cf6)


3.	Then open the http://localhost:8983

![image](https://github.com/user-attachments/assets/f7cd00d7-dd34-4695-b2a7-0c4b7ddfdf47)












4.	We have started the Solr. Now we have to create the collection. It can be done by different ways by sending a POST request to the Server using curl tool by specifying the collection name and the number of Shards and ReplicationFactors.
```curl --request POST --url http://localhost:8983/api/collections --header "Content-Type: application/json" --data "{\"name\":\"EmployeeData\",\"numShards\":1,\"replicationFactor\":1}"
```
![image](https://github.com/user-attachments/assets/9dc7fe1d-f868-4ee8-9804-06e49d536798)







5.	Now go to the localhost:8983 and check whether the collection that we specified has been created or not.
![image](https://github.com/user-attachments/assets/31cc20d4-79f5-4a34-8766-21652f8fcc23)











6.	Now we have to define the Schema, it also can be done by using the curl tool by sending POST request. For the required data, the schema is defined by follows

```curl --request POST --url http://localhost:8983/api/collections/EmployeeData/schema --header "Content-Type: application/json" --data "{\"add-field\": [{\"name\": \"employee_id\", \"type\": \"string\", \"multiValued\": false},{\"name\": \"full_name\", \"type\": \"text_general\", \"multiValued\": false},{\"name\": \"job_title\", \"type\": \"text_general\", \"multiValued\": false},{\"name\": \"department\", \"type\": \"text_general\", \"multiValued\": false},{\"name\": \"business_unit\", \"type\": \"text_general\", \"multiValued\": false},{\"name\": \"gender\", \"type\": \"string\", \"multiValued\": false},{\"name\": \"ethnicity\", \"type\": \"string\", \"multiValued\": false},{\"name\": \"age\", \"type\": \"pint\", \"multiValued\": false},{\"name\": \"hire_date\", \"type\": \"pdate\", \"multiValued\": false},{\"name\": \"annual_salary\", \"type\": \"pdouble\", \"multiValued\": false},{\"name\": \"bonus_pct\", \"type\": \"pfloat\", \"multiValued\": false},{\"name\": \"country\", \"type\": \"text_general\", \"multiValued\": false},{\"name\": \"city\", \"type\": \"text_general\", \"multiValued\": false},{\"name\": \"exit_date\", \"type\": \"pdate\", \"multiValued\": false}]}"
```

![image](https://github.com/user-attachments/assets/6820a096-2815-42c5-a607-a658dfc43781)


















7.	Now we can see that schema that we defined has reflected in the site.

![image](https://github.com/user-attachments/assets/7b3f7b9d-e1f8-486a-ad4a-bacd0bc0da52)























8.	After that we have to index the documents from the csv file. It can be done by sending POST request using curl tool.
```curl "http://localhost:8983/solr/EmployeeData/update?commit=true" --data-binary @C:\Users\harih\Desktop\Employee.csv -H "Content-Type: application/csv"
```



![image](https://github.com/user-attachments/assets/776cdc43-53df-4ebc-8c09-de6923c9ea9c)








9.	We can see that the documents are indexed from the site.



![image](https://github.com/user-attachments/assets/fbca6a76-d51e-459a-a10f-7b4a35f1f340)









![image](https://github.com/user-attachments/assets/a8304dea-1e8e-4b08-aed2-b85e6f18a0d5)












10.	Now we can give queries to retrieve the information.




![image](https://github.com/user-attachments/assets/bf7c48a8-7206-4840-ae13-5ccf208e2c4f)















Instead of using once if we started the Solr, we can use the inbuilt options to create collection then upload the csv using inbuilt function and the schema will be assigned automatically. The snapshots of the following inbuilt functions are as follows.


![image](https://github.com/user-attachments/assets/f4557afe-9843-4b08-8640-8d88bdb04c28)

 

![image](https://github.com/user-attachments/assets/dbc99ac9-1b42-4900-9341-c9dc843bb898)

 
