## ECS</br>

**Find out specific task_id list associated with ECS:**
```
/usr/local/bin/aws ecs list-tasks --cluster <cluuster-name> --output text | awk '{print $2}' | awk -F 'task/' '{print $2}'
```
**Identify tasks name from task-ids:**
```
/usr/local/bin/aws ecs describe-tasks --cluster <cluster-name> --tasks $task_id --query "tasks[*].{Name:containers[].name}" --output text | awk '{print $2}'
```
**Stop specific task running on cluster:**
```
/usr/local/bin/aws ecs stop-task --task $task_id --cluster <cluster-name>
```
**Forcefully deploy new task on cluster:**
```
/usr/local/bin/aws ecs update-service --cluster <cluster-name> --force-new-deployment --service <service-name>
```

## ECR</br>
**Download ECR vulnerability scanned report:**
```
/usr/local/bin/aws ecr describe-image-scan-findings --repository-name <repo_name> --image-id imageDigest=sha256:04c19e7b60465d538220197e9e505c833e8724ed8fdef20c97ddbf42fc14e4d3 > <file_name>
```

## VPC</br>

**Find out vpc-id based on name:**
```
/usr/local/bin/aws ec2 describe-vpcs --filters "Name=tag:Name,Values=<vpc_name>" --query "Vpcs[*].{Name:VpcId}" --output text
```
**Find out security group-id from vpc:**
```
/usr/local/bin/aws ec2 describe-security-groups --filters "Name=vpc-id,Values=$vpc_id" --query "SecurityGroups[?GroupName == '<sg_name>'].{Name:GroupId}" --output text
```
**Add ingress rule to SG:**
```
/usr/local/bin/aws ec2 authorize-security-group-ingress --group-id "$group_id" --protocol "$protocol" --port "$port" --cidr "$ip_address"/32
```


