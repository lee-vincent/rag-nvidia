# NVIDIA LaunchPad Development Environment

This NVIDIA LaunchPad Development Environment provides users with immediate access to a prescriptive labs and a development environment pre-configured with common resources, tools, and IDE extensions to maximize productivity. This particular deployment includes the following platform(s), components, and configurations:

- [NVIDIA Cloud Native Stack](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks)
- [Code Server](https://github.com/coder/code-server/) with a prescriptive workspace

---

## Resources

- [Coder IDE](https://9a3f50f6-05be-0842-44ef-6277672dc4dd.nvidialaunchpad.com/coder/)
    - This web-based IDE is the preferred method of interacting with your NVIDIA LaunchPad environment, with drag-and-drop uploads and easy download capabilities supported out-of-box. Note you may encounter filesize upload limits of ~100MB. It's preferred to import large datasets or object via `pull` (e.g. initiating a download from a terminal in Code Server from an externally hosted object store).
- [Desktop Environment](https://9a3f50f6-05be-0842-44ef-6277672dc4dd.nvidialaunchpad.com/desktop)
    - If you require a full graphical user interface you can access the GPU node directly via NoVNC and your web browser.
- [WebSSH](https://9a3f50f6-05be-0842-44ef-6277672dc4dd.nvidialaunchpad.com/ssh/host/)
    - WebSSH is provided as an alternative to exclusive use of the Code Server IDE.
- [Metrics](https://9a3f50f6-05be-0842-44ef-6277672dc4dd.nvidialaunchpad.com/metrics/)
    - Grafana is included with a preconfigured dashboard and datasource to allow for easy review of environment resource utilization.


## Getting Started

[NVIDIA Cloud Native Stack with Docker](https://github.com/NVIDIA/cloud-native-stack/tree/master/playbooks) allows the flexibility of deploying local docker workloads or Kubernetes workloads directly on a GPU node with appropriate drivers pre-installed for your convenience. To determine what hardware and specs are included in your sandbox you can execute the following commands:

### Docker
```bash
docker run --rm --gpus all nvidia/cuda:12.2.2-base-ubuntu22.04 nvidia-smi
```

### Kubernetes
```bash
kubectl exec daemonset/nvidia-device-plugin-daemonset -n nvidia-gpu-operator -- nvidia-smi
```

Sample output:
```
Defaulted container "nvidia-device-plugin" out of: nvidia-device-plugin, toolkit-validation (init)
Fri Jan 19 00:17:41 2024
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.129.03             Driver Version: 535.129.03   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  GH200 480GB                    Off | 00000009:01:00.0 Off |                    0 |
| N/A   31C    P0             106W / 900W |      5MiB / 97871MiB |      8%      Default |
|                                         |                      |             Disabled |
+-----------------------------------------+----------------------+----------------------+

+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|  No running processes found                                                           |
+---------------------------------------------------------------------------------------+
```