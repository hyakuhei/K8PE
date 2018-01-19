# K8PE
Kubernetes Adaptive Policy Engine
Pronounced 'Cape' the Kubernetes Adaptive Policy Engine is an idea for a service that runs in production K8 clusters and periodically makes dynamic changes to the RBAC policies of running applications/users.

The intention is to borrow heavily from the work of two already fantastic projects:
* RepoKid https://github.com/Netflix/repokid
* audit2rbac https://github.com/liggitt/audit2rbac

We imagine a service that performs two duties as it live monitors the k8 audit stream. 

The first is to monitor the behaviour of applications/users over time. To provide visibility of unusual events or activities, to highlight more dangerous catagories of api requests etc.

The second is to perodically remove unused privileges from running applications/users - reducing over-provisioning of permission over time. Within a framework that allows a/b testing of new policies and allows policies to be rolled back if issues arise.



