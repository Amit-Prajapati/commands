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
