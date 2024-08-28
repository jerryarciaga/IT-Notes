You can set locks that prevent either deletions or modifications. In the portal, these locks are called **Delete** and **Read-Only**. In the command line, these locks are called `CanNotDelete` and `ReadOnly`.
* `CanNotDelete` means authorized users can read and modify the resource, but they can't delete it.
* `ReadOnly` means authorized users can read a resource, but they can't delete or update it. Applying this lock is similar to restricting all authorized users to the permission that the **Reader** role provides.

---

See also:
* [Resource Locks - Microsoft Learn]([https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources?tabs=json](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources?tabs=json)

Related Links:
* [[Azure/Describe Azure management and governance|Describe Azure management and governance]]

Tags:
#az900 #resource #azure 