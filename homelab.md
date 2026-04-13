---
layout: default
title: "Homelab"
permalink: /homelab/
---

<section class="homelab-hero">
    <div class="container">
        <h1 class="section-title">Homelab</h1>
        <p class="homelab-intro">
            This homelab exists for one reason: learning. It runs a production-grade Kubernetes cluster on 
            commodity hardware at home — intentionally overengineered for the sake of understanding how the 
            pieces fit together. Everything from bare-metal provisioning to GitOps, secrets management, and 
            DNS automation is real infrastructure running real workloads. Not because it needs to be this 
            complex, but because that's where the learning happens.
        </p>
    </div>
</section>

<section class="homelab-section">
    <div class="container">
        <h2 class="homelab-section-title">
            <i class="fas fa-server"></i> Hardware
        </h2>

        <h3 class="homelab-subsection-title">Hosts</h3>
        <div class="table-wrapper">
            <table class="homelab-table">
                <thead>
                    <tr>
                        <th>Host</th>
                        <th>Hardware</th>
                        <th>RAM</th>
                        <th>Role</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><code>pve1</code></td>
                        <td>HP Microserver G8</td>
                        <td>16 GB</td>
                        <td>Proxmox hypervisor</td>
                    </tr>
                    <tr>
                        <td><code>pve2</code></td>
                        <td>HP Microserver G8</td>
                        <td>8 GB</td>
                        <td>Proxmox hypervisor</td>
                    </tr>
                    <tr>
                        <td><code>pve3</code></td>
                        <td>Intel NUC i7</td>
                        <td>64 GB</td>
                        <td>Proxmox hypervisor</td>
                    </tr>
                    <tr>
                        <td><code>bare1</code></td>
                        <td>Dell Optiplex 3080</td>
                        <td>16 GB</td>
                        <td>Bare-metal Talos worker</td>
                    </tr>
                    <tr>
                        <td><code>NAS</code></td>
                        <td>Synology DS2415+</td>
                        <td>—</td>
                        <td>NFS storage</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <h3 class="homelab-subsection-title">Proxmox VMs</h3>
        <div class="table-wrapper">
            <table class="homelab-table">
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Host</th>
                        <th>RAM</th>
                        <th>Function</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><code>plex</code></td>
                        <td>pve1</td>
                        <td>2 GB</td>
                        <td>Plex Media Server (GPU passthrough)</td>
                    </tr>
                    <tr>
                        <td><code>homeassistant</code></td>
                        <td>pve1</td>
                        <td>2 GB</td>
                        <td>Home Assistant (Zigbee passthrough)</td>
                    </tr>
                    <tr>
                        <td><code>talos-control-plane-1</code></td>
                        <td>pve2</td>
                        <td>4 GB</td>
                        <td>Kubernetes control-plane</td>
                    </tr>
                    <tr>
                        <td><code>talos-control-plane-2</code></td>
                        <td>pve1</td>
                        <td>4 GB</td>
                        <td>Kubernetes control-plane</td>
                    </tr>
                    <tr>
                        <td><code>talos-control-plane-3</code></td>
                        <td>pve3</td>
                        <td>4 GB</td>
                        <td>Kubernetes control-plane</td>
                    </tr>
                    <tr>
                        <td><code>talos-worker-1</code></td>
                        <td>pve2</td>
                        <td>2 GB</td>
                        <td>Kubernetes worker</td>
                    </tr>
                    <tr>
                        <td><code>talos-worker-2</code></td>
                        <td>pve1</td>
                        <td>4 GB</td>
                        <td>Kubernetes worker</td>
                    </tr>
                    <tr>
                        <td><code>talos-worker-3</code></td>
                        <td>pve3</td>
                        <td>16 GB</td>
                        <td>Kubernetes worker (media workloads)</td>
                    </tr>
                    <tr>
                        <td><code>talos-worker-4</code></td>
                        <td>bare1</td>
                        <td>16 GB</td>
                        <td>Kubernetes worker (bare-metal)</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <h3 class="homelab-subsection-title">Network (VLANs)</h3>
        <div class="table-wrapper">
            <table class="homelab-table">
                <thead>
                    <tr>
                        <th>VLAN</th>
                        <th>Name</th>
                        <th>Subnet</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>10</td>
                        <td>Home</td>
                        <td>10.0.10.0/24</td>
                    </tr>
                    <tr>
                        <td>60</td>
                        <td>Servers / Proxmox</td>
                        <td>10.0.60.0/24</td>
                    </tr>
                    <tr>
                        <td>70</td>
                        <td>IoT</td>
                        <td>10.0.70.0/24</td>
                    </tr>
                    <tr>
                        <td>80</td>
                        <td>Kubernetes / Talos</td>
                        <td>10.0.80.0/24</td>
                    </tr>
                    <tr>
                        <td>99</td>
                        <td>Management</td>
                        <td>native untagged</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</section>

<section class="homelab-section homelab-section-alt">
    <div class="container">
        <h2 class="homelab-section-title">
            <i class="fas fa-dharmachakra"></i> Kubernetes Cluster
        </h2>

        <div class="homelab-cards">
            <div class="homelab-card">
                <div class="homelab-card-icon"><i class="fas fa-layer-group"></i></div>
                <h4>Distribution</h4>
                <p>Talos Linux v1.12.6</p>
            </div>
            <div class="homelab-card">
                <div class="homelab-card-icon"><i class="fas fa-cube"></i></div>
                <h4>Kubernetes</h4>
                <p>v1.35.2</p>
            </div>
            <div class="homelab-card">
                <div class="homelab-card-icon"><i class="fas fa-network-wired"></i></div>
                <h4>CNI</h4>
                <p>Cilium 1.19.2<br><small>kube-proxy replacement, Ingress, L2 announcements</small></p>
            </div>
            <div class="homelab-card">
                <div class="homelab-card-icon"><i class="fas fa-code-branch"></i></div>
                <h4>GitOps</h4>
                <p>FluxCD</p>
            </div>
            <div class="homelab-card">
                <div class="homelab-card-icon"><i class="fas fa-lock"></i></div>
                <h4>Secrets</h4>
                <p>SOPS + Age</p>
            </div>
            <div class="homelab-card">
                <div class="homelab-card-icon"><i class="fas fa-database"></i></div>
                <h4>Storage</h4>
                <p>democratic-csi with NFS<br><small>Synology DS2415+</small></p>
            </div>
        </div>
    </div>
</section>

<section class="homelab-section">
    <div class="container">
        <h2 class="homelab-section-title">
            <i class="fas fa-th-large"></i> Installed Stack
        </h2>

        <h3 class="homelab-subsection-title">Infrastructure</h3>
        <div class="table-wrapper">
            <table class="homelab-table">
                <thead>
                    <tr>
                        <th>Component</th>
                        <th>Details</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Cilium</strong></td>
                        <td>v1.19.2 — CNI, Ingress controller, L2 load balancer announcements</td>
                    </tr>
                    <tr>
                        <td><strong>MetalLB</strong></td>
                        <td>LoadBalancer pool on VLAN 80</td>
                    </tr>
                    <tr>
                        <td><strong>cert-manager</strong></td>
                        <td>Automatic TLS via Cloudflare DNS-01 challenge, Let's Encrypt production</td>
                    </tr>
                    <tr>
                        <td><strong>democratic-csi</strong></td>
                        <td>Dynamic NFS PVC provisioning from Synology NAS</td>
                    </tr>
                    <tr>
                        <td><strong>ExternalDNS</strong></td>
                        <td>Automatic DNS record creation in Adguard via webhook provider</td>
                    </tr>
                    <tr>
                        <td><strong>kube-prometheus-stack</strong></td>
                        <td>Prometheus + Grafana for cluster monitoring</td>
                    </tr>
                    <tr>
                        <td><strong>Reloader</strong></td>
                        <td>Automatic pod restarts on ConfigMap/Secret changes</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <h3 class="homelab-subsection-title">Networking</h3>
        <div class="table-wrapper">
            <table class="homelab-table">
                <thead>
                    <tr>
                        <th>App</th>
                        <th>Description</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Adguard Home</strong></td>
                        <td>Network-wide DNS filtering and ad blocking</td>
                    </tr>
                    <tr>
                        <td><strong>Cloudflared</strong></td>
                        <td>Cloudflare Tunnel for secure external access without port forwarding</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <h3 class="homelab-subsection-title">Media</h3>
        <div class="table-wrapper">
            <table class="homelab-table">
                <thead>
                    <tr>
                        <th>App</th>
                        <th>Description</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>qBittorrent</strong></td>
                        <td>Download client</td>
                    </tr>
                    <tr>
                        <td><strong>Prowlarr</strong></td>
                        <td>Indexer manager for the *arr stack</td>
                    </tr>
                    <tr>
                        <td><strong>Radarr (1080p)</strong></td>
                        <td>Movie collection management — 1080p</td>
                    </tr>
                    <tr>
                        <td><strong>Radarr (4K)</strong></td>
                        <td>Movie collection management — 4K</td>
                    </tr>
                    <tr>
                        <td><strong>Sonarr</strong></td>
                        <td>TV series collection management</td>
                    </tr>
                    <tr>
                        <td><strong>Recyclarr</strong></td>
                        <td>Syncs TRaSH Guides quality profiles to Radarr and Sonarr — runs nightly as a CronJob</td>
                    </tr>
                    <tr>
                        <td><strong>Calibre Web Automated</strong></td>
                        <td>E-book library management with automatic imports</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <h3 class="homelab-subsection-title">Dashboard & Observability</h3>
        <div class="table-wrapper">
            <table class="homelab-table">
                <thead>
                    <tr>
                        <th>App</th>
                        <th>Description</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Homepage</strong></td>
                        <td>Unified dashboard for all services</td>
                    </tr>
                    <tr>
                        <td><strong>Grafana</strong></td>
                        <td>Metrics visualisation and cluster monitoring dashboards</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</section>
