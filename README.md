# My NixOS Expirement

## Stage 1

Static deployment of 3 services (prometheus/grafana, prostgres, erlang/elixir) where I mainly explore NixOS itself as well as Erlang integration.

### Components

 - Nix(OS);
 - prometheus;
 - grafana;
 - postgres;
 - erlang/elixir;
 - nixops (virtualbox/ec2).

### Service

Since I don't have a full-fledged open sourced web project for BEAM I piggyback on hex_web because it has:
 - developed API;
 - DB integration;
 - it uses plugs and ecto.
 
I want to integrate it with my Prometheus stuff in a separate branch of my fork.

#### Instances/VMs

 - DB, just for postgres (node_exporter, prostgres, postgres_exporter) (I'm not sure Nixops can provision RDS, I want to monitor it with prometheus anyway);
 - WEB, just for hex_web (node_exporter, nginx, nginx_exporter, hex_web);
 - Monitoring, for Prometheus&Grafana (node_exporter, prometheus, grafana).
 
What's interesting there is that nixops can generate proper configuration even though instances will have "random" addresses (assigned by AWS when AMI starts).

Prometheus, grafana, nginx, exporters are known nixos packages already. Hex_web might be tricky:
 - hex_packages.nix is extremely outdated, looks like I have to try to regenerate it or even write definigtions manually;
 - Erlang release generation using nix tools;
 - Importing seed data.
 
#### Other resources:
 
 - I want to explores Route 53 integration
 
## Ideas for the next stages

 - backups;
 - continuous deployment;
 - auto-scaling (is it even possible?).
 
# Links
 - [NixOS manual](https://nixos.org/nixos/manual)
 - [Nix manual](https://nixos.org/nix/manual/)
 - [Nixpkgs manual](https://nixos.org/nixpkgs/manual/)
 - [NixOps manual](https://nixos.org/nixops/manual)
 - [NIX COOKBOOK](http://funops.co/nix-cookbook/)
 - [Erlang Factory SF video](https://www.youtube.com/watch?v=xRSFJH3Lw6I)
 - https://github.com/erlang-nix
 - https://github.com/zalora/microgram

 
