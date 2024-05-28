## Manage Identiy in Azure
Greate video: https://www.youtube.com/watch?v=vr1IIkGHiKQ&t

### Using AZ CLI

##### Create ID
`az role assignment create --assignee <app-(client)-id> --role <role> --scope /subscriptions/<subscriptio-ID>/resourceGroups/<resource-group>`
##### Delete ID
`az role assignment delete --assignee <app-(client)-id> --role Reader --scope /subscriptions/<subscriptio-ID>resourceGroups/<resource-group>/providers/Microsoft.Storage/storageAccounts/dlastor`

##### Check Roles of ID
`az role assignment list --assignee <app-(client)-id> --output table`

`az role assignment list --assignee <app-(client)-id> --all --output table` **!!!**

*In the AZURE portal, you can check **which Identities** with **what roles** are attached to your resource, by checking the **Access Control (IAM)** in the respective pane of the resource. So you approach this question by going via the 'role assignments' tab in IAM.*

### !!! But note
If you want to know what roles are assign to my ID looking in the Azure Portal, you won't find the info and you need to use Azure CLI.
There you have to use 