Troubleshooting
---------------

FAQ
===

**How much will this cost?**

That all depends on how many resources you request, and what kind of cloud provider
you are working with. There's not easy answer to this question, but a good rule
of thumb is XXX YUVI AND RYAN FILL IN.

For a more detailed pecture, Ryan Lovett has put together `a short jupyter notebook <https://github.com/data-8/jupyterhub-k8s/blob/master/docs/cost-estimation/gce_budgeting.ipynb>`_ that allows you to generate a predicted cost for running a jupyterhub deployment, given the number of nodes and memory / CPU requirements.

**I thought I had deleted my cloud resources, but they still show up. Why?**

You probably deleted the specific nodes, but not the kubernetes cluster that was controlling those nodes. Kubernetes is designed to make sure that a specific set of resources is available at all times. This means that if you only delete the nodes, but not the kubernetes instance, then it will detect the loss of computers and will create two new nodes to compensate.

**How does billing for this work?!**

Jupyterhub isn't handling any of the billing for your usage - that's done through
whatever cloud service you're using.

Common error messages
=====================

* ``could not find default credentials. See https://developers.google.com/accounts/docs/application-default-credentials for more information.``
    * Execute `gcloud auth application-default login` and follow the prompts. The provided link has other options for advanced use cases.
* ``ERROR: (gcloud.container.clusters.create) ResponseError: code=503, message=Project staeiou-5f880 is not fully initialized with the default service accounts. Please try again later.``
    * Go to ‘https://console.cloud.google.com/kubernetes/list’ and click ‘enable’ and follow the prompts