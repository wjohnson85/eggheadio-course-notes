# Delete an item from a DynamoDB table with delete operation

**[📹 Video](https://egghead.io/lessons/aws-delete-an-item-from-a-dynamodb-table-with-delete-operation)**

 <TimeStamp start="0:37" end="1:07">


Let's delete a todo!

```ts
const deleteTodoItem = async (data: { id: string }) => {
    const { id } = data;

    if (id && id !== "") {
        await dynamo
            .delete({
                TableName: tableName,
                Key: {
                    // each todo needs a unique id
                    id
                }
            })
            .promise();
    }

    return id;
};
```
 </TimeStamp>


 <TimeStamp start="1:15" end="1:30">

Let's test this by sending a `DELETE` request:
```JSON
{
    "id": "this_is_a_new_id"
}
```
 </TimeStamp>
 
 
  <TimeStamp start="1:31" end="1:38">
   
We should get a response like this: `"Todo item with an id of this_is_a_new_id deleted from the database"`.
     </TimeStamp>




👍 Validate that the todo item was indeed deleted with a new `GET` request.
