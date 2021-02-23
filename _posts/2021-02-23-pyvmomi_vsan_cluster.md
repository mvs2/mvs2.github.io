---
title: "My ParkWhiz app"
date: 2021-02-18
categories:
  - Python
  - Hour of Code
  - pyVmomi

tags:
  - python
  - Hour Of Code
  - pyVmomi
---

This one is a bit simpler, hopefully.  We are using [pyVmomi][pyvmomi] to enable a cluster for vSAN.  As mentioned in 
the code, you'll need to download the [vSAN Management SDK for Python][vSAN], as VMware has not put this library on Pypi.
You will most likely also want to use something like [argparse][argparse] instead of hard coding vCenter name, cluster name,
admin information, e.t.c.  I didn't add that in here as I wanted to simplify the code presentation.  Hope this helps someone.



```python
"""
check if cluster is vSan enabled and if not enable vSan
marcus_sharp 11/24/2020
"""
import atexit
import ssl
from pyVim import connect
from pyVmomi import vim

# import the VSAN API python bindings
# have to download these manually and extract from https://code.vmware.com/web/sdk/7.0%20U1/vsan-python
import vsanmgmtObjects
import vsanapiutils


def main():
    server = 'your_vcenter'
    si = vc_connect(server)
    atexit.register(connect.Disconnect, si)
    clusterName = "your_cluster"
    cluster = getClusterInstance(clusterName, si)
    if not cluster:
        print('cluster not found, exiting')
        exit()

    vsan_config = cluster.configurationEx.vsanConfigInfo.enabled
    if not vsan_config:
        # vsan is not enabled on cluster
        context = ssl.create_default_context()
        context.check_hostname = False
        context.verify_mode = ssl.CERT_NONE
        vcMos = vsanapiutils.GetVsanVcMos(si._stub, context=context)
        vsanClusterConfigSystem = vcMos['vsan-cluster-config-system']
        vSanSpec = vim.vsan.ReconfigSpec(modify=True, )
        vSanSpec.vsanClusterConfig = vim.vsan.cluster.ConfigInfo(enabled=True)
        vSanSpec.vsanClusterConfig.defaultConfig = vim.vsan.cluster.ConfigInfo.HostDefaultInfo(
            autoClaimStorage=False)
        task = vsanClusterConfigSystem.VsanClusterReconfig(cluster, vSanSpec)
        vsanapiutils.WaitForTasks(task, si)

    else:
        print('vsan already configured on cluster, exiting')


def getClusterInstance(clusterName, serviceInstance):
    content = serviceInstance.RetrieveContent()
    searchIndex = content.searchIndex
    datacenters = content.rootFolder.childEntity
    for datacenter in datacenters:
        cluster = searchIndex.FindChild(datacenter.hostFolder, clusterName)
        if cluster is not None:
            return cluster
    # return None



def vc_connect(vc):
    # Disabling SSL warnings
    context = ssl.create_default_context()
    context.check_hostname = False
    context.verify_mode = ssl.CERT_NONE
    service_instance = None

    try:
        print(f'attempting to connect to {vc}')
        service_instance = connect.SmartConnect(host=vc,
                                                user='vcenteradmin@domain.com',
                                                pwd='admin_pw',
                                                port=443,
                                                sslContext=context)

    except IOError as e:
        pass
    if not service_instance:
        raise SystemExit("Unable to connect to host with supplied info.")
    return service_instance


if __name__ == '__main__':
    main()

```





I run the script via a Windows Scheduled task.  I learned via google searches (mainly answers on StackOverFlow ) that when doing this with Windows, you need to save your python file as a ".pw" file. In the task "Action" tab, under "Program/Script":


[pyVmomi]:https://github.com/vmware/pyvmomi
[vSAN]:https://code.vmware.com/web/sdk/7.0%20U1/vsan-python



