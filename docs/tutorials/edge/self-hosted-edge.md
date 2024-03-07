(edge-self-hosted)=
# Self-hosted options 

In this section, we outline installation instructions for some
third-party supported self-hosted options, such as
[MicroK8s](https://microk8s.io/) and [K3s](https://k3s.io/). These are
third-party tools and CrateDB is not responsible for those tools. That
said, we have tested the instructions provided below for functionality.

Users less familiar with customizing their Kubernetes stack on their own
may find any of these approaches a practical solution for easier CrateDB
Cloud on Kubernetes setup.

(edge-tools-microk8s)=
## MicroK8s 

Below is a full walkthrough of how to get CrateDB Cloud on Kubernetes 
up and running on MicroK8s. The steps are merely examples of a process 
validated by us; other methods may work also. We provide this information
for ease of use and to illustrate how to work with CrateDB Cloud 
on Kubernetes.

(edge-tools-microk8s-setup)=
### Set up MicroK8s

Follow the instructions from the [MicroK8s
docs](https://microk8s.io/docs). For the purposes of this tutorial, we
assume a [snap](https://snapcraft.io/)-based distribution, such as
[Ubuntu](https://ubuntu.com/). On this occasion, you'll be setting up a
three-node Kubernetes cluster. You can also use a single node for
testing purposes if you wish. Regardless, the installation instructions
must be run on every node you set up.

:::{code} console
sudo snap install microk8s --classic --channel=1.21

sudo usermod -a -G microk8s $USER
sudo chown -f -R $USER ~/.kube

microk8s status --wait-ready
microk8s kubectl get nodes

alias kubectl='microk8s kubectl'

microk8s enable dns storage
:::

(edge-tools-microk8s-setup-cluster)=
### Set up cluster

On one of the nodes, run the command to get joining instructions. This
will print the command that you need to run on the other two nodes to
create a Kubernetes cluster.

:::{code} console
microk8s add-node
:::

(edge-tools-microk8s-join)=
### Join nodes to cluster

Now SSH into the two remaining nodes and run the command you received on
the first node.

:::{code} console
root@ub11:~# microk8s join <IP of first node>:25000/<cluster id>
Contacting cluster at <IP address>
Waiting for this node to finish joining the cluster...
:::

(edge-tools-microk8s-storage)=
### Use a storage solution

The MicroK8s setup will require a storage solution. In this case, the
tutorial shows how to do so using [Longhorn](https://longhorn.io/), a
distributed storage solution for Kubernetes. You can follow the
[Longhorn installation
instructions](https://longhorn.io/docs/1.1.1/deploy/install/install-with-kubectl/)
as described below. (Other storage solutions for Kubernetes may work as
well.)

First the installation:

:::{code} console
kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/v1.1.1/deploy/longhorn.yaml
:::

Then you need to specify the root directory:

:::{code} console
kubectl -n longhorn-system edit deployment longhorn-driver-deployer

- name: KUBELET_ROOT_DIR
value: /var/snap/microk8s/common/var/lib/kubelet
:::

(edge-tools-microk8s-create-region)=
### Set up CrateDB Cloud on Kubernetes region

At this stage, you can create a CrateDB Cloud on Kubernetes region via the CrateDB 
Cloud Console. Follow the steps outlined above
{ref}`from the CrateDB sign up onwards <edge-signup>` to proceed.

(edge-tools-microk8s-script)=
### Run the script

Run the script with the following command:

:::{code} console
wget -qO- https://console.cratedb.cloud/edge/cratedb-cloud-edge.sh > edge-installer.sh
chmod u+x edge-installer.sh
./edge-installer --dry-run  <token>
:::

Note that `dry-run` provides, as the name suggests, a method to test the
installation by generating the manifests that are going to be applied
without applying them. This gives you an opportunity to verify them
before the full install.

The `<token>` in question is the token you receive from the CrateDB
Console Cloud on Kubernetes region field in the Regions tab of the Organization
Overview. For more information on this section of the CrateDB Console,
refer to the {ref}`CrateDB Cloud Console overview <overview-org-regions>`.

With this, you should be ready to use CrateDB Cloud on 
Kubernetes via Microk8s.

(edge-tools-k3s)=
## K3S 

Below is a full walkthrough of how to get CrateDB Cloud on Kubernetes 
up and running on K3S. The steps are merely examples of a process 
validated by us; other methods may work also. We provide this information 
for ease of use and to illustrate how to work with CrateDB Cloud 
on Kubernetes.

(edge-tools-k3s-setup)=
### Set up K3S

A simple way to bootstrap the K3S setup is with
[k3sup](https://github.com/alexellis/k3sup). However, this tutorial
assumes you will use K3S native, which offers more granularity. Also,
this setup is suitable for a multi-node cluster.

First you have to set up the master node:

:::{code} console
export INSTALL_K3S_VERSION="v1.19.10+k3s1"
curl -sfL https://get.k3s.io | sh -s - --disable=traefik

mkdir ~/.kube
cp /etc/rancher/k3s/k3s.yaml ~/.kube/config
export KUBECONFIG=~/.kube/config
kubectl config set-context default
kubectl get node -o wide
:::

Next, get the token:

:::{code} console
cat /var/lib/rancher/k3s/server/node-token
:::

Note that the master node will operate both as a master and as a worker.

(edge-tools-k3s-join)=
### Join nodes to cluster

Next, you set up other worker nodes (as many as applicable to your use
case):

:::{code} console
export token=<token>
export INSTALL_K3S_VERSION="v1.19.10+k3s1"
curl -sfL https://get.k3s.io | K3S_URL="https://ub1:6443" K3S_TOKEN=$token sh -
:::

(edge-tools-k3s-uninstall)=
### Uninstall

If you need to uninstall, run:

:::{code} console
/usr/local/bin/k3s-agent-uninstall.sh
:::

(edge-tools-k3s-storage)=
### Use a storage solution

The K3S setup for CrateDB Cloud on Kubernetes will require a storage 
solution. In this case, the tutorial shows how to do so using
[Longhorn](https://longhorn.io/), a distributed storage solution for
Kubernetes. You can follow the [Longhorn installation instructions]
(https://longhorn.io/docs/1.1.1/deploy/install/install-with-kubectl/)
as described below. (Other storage solutions for Kubernetes may work as
well.)

First the installation:

:::{code} console
kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/v1.1.1/deploy/longhorn.yaml
:::

Then you need to specify the root directory. Note that unlike in the
Microk8s example above, you need to redirect the directory:

:::{code} console
kubectl -n longhorn-system edit deployment longhorn-driver-deployer

    - name: KUBELET_ROOT_DIR
    value: /var/lib/rancher/k3s/agent/kubelet  ..... /var/lib/kubelet
:::

(edge-tools-k3s-setup-region)=
### Set up CrateDB Cloud on Kubernetes region

At this stage, you can create a CrateDB Cloud on Kubernetes region via the CrateDB Cloud
Console. Follow the steps outlined above
{ref }`from the CrateDB sign up onwards <edge-signup>` to proceed.

(edge-tools-k3s-script)=
### Run the script

Run the script with the following command:

:::{code} console
wget -qO- https://console.cratedb.cloud/edge/cratedb-cloud-edge.sh > edge-installer.sh
chmod u+x edge-installer.sh
./edge-installer --dry-run  <token>
:::

Note that `dry-run` provides, as the name suggests, a method to test the
installation by generating the manifests that are going to be applied
without applying them. This gives you an opportunity to verify them
before the full install.

The `<token>` in question is the token you receive from the CrateDB
Console Cloud on Kubernetes region field in the Regions tab of the Organization
Overview. For more information on this section of the CrateDB Console,
refer to the {ref}`CrateDB Cloud Console overview <overview-org-regions>`.

With this, you should be ready to use CrateDB Cloud on Kubernetes via K3S.

(edge-tools-custom-tls)=
## Custom TLS certificates

By default, CrateDB Cloud on Kubernetes will issue self-signed certificates for CrateDB
instances running in your Cloud on Kubernetes region. It is also possible to use
"proper" TLS certificates if required. In the examples below, we will
configure [letsencrypt](https://letsencrypt.org/) to issue certificates
and use them with CrateDB Cloud on Kubernetes clusters.

(edge-tools-custom-tls-issuer)=
### Create a `ClusterIssuer`

CrateDB Cloud on Kubernetes uses an industry standard app called
[cert-manager](https://github.com/cert-manager/cert-manager/) for
managing TLS certificates. To issue valid certificates, you would need
to follow the cert-manager [tutorial for letsencrypt via the DNS
solver](https://cert-manager.io/docs/configuration/acme/dns01/). CrateDB
clusters are provisioned behind a Load Balancer, and as such the only
way to solve letsencrypt challenges is via DNS. Your configuration will
vary, but if you use `Route53` as your DNS provider, you will end up
with a configuration similar to this:

:::{code} yaml
apiVersion: cert-manager.io/v1alpha3
kind: ClusterIssuer
metadata:
  name: letsencrypt-dns
spec:
  acme:
    email: administrators@yourorg.com
    privateKeySecretRef:
      name: letsencrypt
    server: https://acme-v02.api.letsencrypt.org/directory
    solvers:
    - dns01:
        route53:
          accessKeyID: [your-access-key]
          region: eu-central-1
          secretAccessKeySecretRef:
            key: aws_secret_access_key
            name: your_secret
:::

(edge-tools-custom-tls-certificate)=
### Ask for a new certificate

To ask [letsencrypt](https://letsencrypt.org/) for a new certificate,
create a `Certificate` Kubernetes resource:

:::{code} yaml
apiVersion: cert-manager.io/v1alpha3
kind: Certificate
metadata:
  name: my-certificate
  namespace: my-namespace
spec:
  dnsNames:
  - my-cluster-1.my.fully.qualified.domain.example.com
  issuerRef:
    kind: ClusterIssuer
    name: letsencrypt-dns
  keystores:
    jks:
      create: true
      passwordSecretRef:
        key: keystore-password
        name: keystore-passwords
    pkcs12:
      create: true
      passwordSecretRef:
        key: keystore-password
        name: keystore-passwords
  secretName: my-target-secret-for-this-certificate
:::

:::{note}
Note that you must do this inside of a namespace where your CrateDB will
be running.
:::

The secret called `keystore-passwords` will be created automatically
when you create the CrateDB Cloud Project in this region.

(edge-tools-custom-tls-replace)=
### Replace the existing certificate used by your cluster

As your CrateDB Cloud on Kubernetes cluster comes with a self-signed certificate, you
will need to replace it. Fortunately, this is fairly straightforward,
and only requires a quick edit to the CrateDB Cluster's `StatefulSet`,
i.e.:

:::{code} console
$ kubectl -n $YOUR_NAMESPACE edit sts crate-data-hot-$CLUSTER_ID
:::

Then find the following section and replace the secret name with the
`secretName` specified when creating the `Certificate` entity above,
i.e.:

:::{code} yaml
- name: keystore
  secret:
    defaultMode: 420
    items:
    - key: keystore.jks
      path: keystore.jks
    secretName: my-target-secret-for-this-certificate
:::

Once this is done, you will have to bounce each of the CrateDB pods for
the change to be picked up. Once the pods are back up, they will present
the configured certificate on both the HTTP and PGSQL ports.

:::{note}
Note that you need to access CrateDB via a valid DNS name for this to
work, so make sure that
`my-cluster-1.my.fully.qualified.domain.example.com` correctly points to
your CrateDB instance (i.e. via an external network load balancer).
:::
