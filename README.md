# Talos KubeSpan + cilium Native-Routing

This serves as a demo and documentation when utilizing Talos
[KubeSpan](https://docs.siderolabs.com/talos/v1.11/networking/kubespan#kubespan)
for [Native-Routing](https://docs.cilium.io/en/v1.18/network/concepts/routing/#arch-direct-routing)
in cilium.

The [Taskfile.yml](Taskfile.yml) wraps most commands required to configure a
working demo cluster. You are required to provide IP addresses via `vars`.

Get started by booting your Talos nodes and ensure these are in maintenance mode.
Note the IP addresses and configure the `CONTROLPLANES` and `WORKERS` variables
inside the [Taskfile.yml](Taskfile.yml).

Enusre requirements are installed:
- [talosctl](https://docs.siderolabs.com/talos/v1.11/getting-started/talosctl)
- [task](https://taskfile.dev/)
- [helm](https://helm.sh/)
- [yq](https://github.com/mikefarah/yq/)

Afterwards you should be able to start everything using:

```shell
task gen-talos
task bootstrap
export KUBECONFIG="$(pwd)/kubeconfig"
export TALOSCONFIG="$(pwd)/talosconfig"

kubectl get nodes -o wide
```

Check the available tasks using `task --list` for more info.

>Not all cilium options you will find in the Taskfile are required but have been
to test stuff

Credits to: <https://github.com/siderolabs/talos/issues/9043>
