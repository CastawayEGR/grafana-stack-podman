grafana-stack-podman
=========
[![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![GitHub repo size in bytes](https://img.shields.io/github/repo-size/CastawayEGR/ocpnv.svg?logoColor=brightgreen)](https://github.com/CastawayEGR/ocpnv)
[![GitHub last commit](https://img.shields.io/github/last-commit/CastawayEGR/ocpnv.svg?logoColor=brightgreen)](https://github.com/CastawayEGR/ocpnv)

Grafana Stack for Metrics, Logs, & Traces using Podman

## Installation

Clone this repo locally on your RHEL/CentOS/Rocky Linux/Alma Linux machine.

```$ git clone https://github.com/CastawayEGR/grafana-stack-podman```

Change to the cloned repo directory.

```$ cd grafana-stack-podman```

Now we want to spin this up using podman.

```$ podman play kube grafana-stack.yaml```

We can verify the stack is up and running by running the following.

```$ podman ps```

Next up we can expose Grafana, Mimir, Loki, and Tempo via firewall-cmd.

```$ sudo firewall-cmd --permanent --add-port={3000/tcp,3100/tcp,4317/tcp,4318/tcp,9009/tcp,9095/tcp,9096/tcp,9097/tcp,9411/tcp,14268/tcp}```

```$ sudo firewall-cmd --reload```

Once deployed you can browse to the Grafana deployment by visiting http://{machine_ip}:3000 and logging in with the default credentials.

## Grafana Configuration

Finally we want to configure our 3 newly deployed backends with the following information.

Prometheus: 

```http://{machine_ip}:9009/prometheus```

Loki: 

```http://{machine_ip}:3100```

Tempo: 

```http://{machine_ip}:3200```

That's it you are ready to start ingesting metrics, logs, and traces!

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)

