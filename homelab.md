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
                        <td><code>bare-metal1</code></td>
                        <td>Dell Optiplex 3080</td>
                        <td>16 GB</td>
                        <td>Bare-metal Talos worker</td>
                    </tr>
                    <tr>
                        <td><code>bare-metal2</code></td>
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

        <h3 class="homelab-subsection-title">Nodes</h3>
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
                        <td>6 GB</td>
                        <td>Plex Media Server (GPU passthrough)</td>
                    </tr>
                    <tr>
                        <td><code>homeassistant</code></td>
                        <td>pve1</td>
                        <td>4 GB</td>
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
                        <td>2 GB</td>
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
                        <td>pve3</td>
                        <td>16 GB</td>
                        <td>Kubernetes worker</td>
                    </tr>
                    <tr>
                        <td><code>talos-worker-2</code></td>
                        <td>pve3</td>
                        <td>16 GB</td>
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
                        <td>bare-metal1</td>
                        <td>16 GB</td>
                        <td>Kubernetes worker (bare-metal)</td>
                    </tr>
                    <tr>
                        <td><code>talos-worker-5</code></td>
                        <td>bare-metal2</td>
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
            <i class="fas fa-memory"></i> Kubernetes Cluster RAM
        </h2>

        <div class="ram-stats">
            <div class="ram-stat-card">
                <div class="ram-stat-value">90 GB</div>
                <div class="ram-stat-label">Total cluster RAM</div>
            </div>
            <div class="ram-stat-card">
                <div class="ram-stat-value">8</div>
                <div class="ram-stat-label">Nodes</div>
            </div>
            <div class="ram-stat-card">
                <div class="ram-stat-value">80 GB</div>
                <div class="ram-stat-label">Worker capacity</div>
            </div>
            <div class="ram-stat-card">
                <div class="ram-stat-value">10 GB</div>
                <div class="ram-stat-label">Control-plane capacity</div>
            </div>
        </div>

        <div class="ram-chart">
            <div class="ram-chart-legend">
                <span class="ram-legend-item ram-legend-cp"><i class="fas fa-circle"></i> Control-plane</span>
                <span class="ram-legend-item ram-legend-worker"><i class="fas fa-circle"></i> Worker (VM)</span>
                <span class="ram-legend-item ram-legend-bare"><i class="fas fa-circle"></i> Worker (bare-metal)</span>
            </div>

            <div class="ram-row">
                <span class="ram-label"><code>talos-control-plane-1</code></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-cp" style="width: 25%">4 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>talos-control-plane-2</code></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-cp" style="width: 12.5%">2 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>talos-control-plane-3</code></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-cp" style="width: 25%">4 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>talos-worker-1</code></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-worker" style="width: 100%">16 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>talos-worker-2</code></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-worker" style="width: 100%">16 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>talos-worker-3</code></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-worker" style="width: 100%">16 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>talos-worker-4</code></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-bare" style="width: 100%">16 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>talos-worker-5</code></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-bare" style="width: 100%">16 GB</div>
                </div>
            </div>
        </div>

        <h3 class="homelab-subsection-title" style="margin-top: 2.5rem;">Physical host allocation</h3>
        <div class="ram-chart">
            <div class="ram-chart-legend">
                <span class="ram-legend-item" style="color: var(--text-secondary)"><i class="fas fa-circle" style="color: #2563eb"></i> Allocated</span>
                <span class="ram-legend-item" style="color: var(--text-secondary)"><i class="fas fa-circle" style="color: var(--border-color)"></i> Available</span>
            </div>

            <div class="ram-row">
                <span class="ram-label"><code>pve1</code> <small>16 GB</small></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-worker" style="width: 75%">12 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>pve2</code> <small>8 GB</small></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-worker" style="width: 50%">4 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>pve3</code> <small>64 GB</small></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-worker" style="width: 81.25%">52 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>bare-metal1</code> <small>16 GB</small></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-bare" style="width: 100%">16 GB</div>
                </div>
            </div>
            <div class="ram-row">
                <span class="ram-label"><code>bare-metal2</code> <small>16 GB</small></span>
                <div class="ram-bar-track">
                    <div class="ram-bar ram-bar-bare" style="width: 100%">16 GB</div>
                </div>
            </div>
        </div>
    </div>
</section>

<section class="homelab-section">
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

        <h3 class="homelab-subsection-title" style="margin-top: 2.5rem;">GitOps flow</h3>
        <div class="flow-diagram">
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-code"></i></div>
                <div class="flow-node-label">Git push</div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fab fa-github"></i></div>
                <div class="flow-node-label">GitHub</div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-sync-alt"></i></div>
                <div class="flow-node-label">FluxCD<small>polls every 10m</small></div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-lock-open"></i></div>
                <div class="flow-node-label">SOPS decrypt<small>Age key</small></div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-dharmachakra"></i></div>
                <div class="flow-node-label">Kubernetes API</div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node flow-node-end">
                <div class="flow-node-icon"><i class="fas fa-check-circle"></i></div>
                <div class="flow-node-label">Deployed</div>
            </div>
        </div>
    </div>
</section>

<section class="homelab-section homelab-section-alt">
    <div class="container">
        <h2 class="homelab-section-title">
            <i class="fas fa-project-diagram"></i> Architecture
        </h2>

        <h3 class="homelab-subsection-title">External traffic</h3>
        <div class="flow-diagram">
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-globe"></i></div>
                <div class="flow-node-label">Internet</div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-cloud"></i></div>
                <div class="flow-node-label">Cloudflare<small>DNS + proxy</small></div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-right-left"></i></div>
                <div class="flow-node-label">Cloudflared<small>encrypted tunnel</small></div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-network-wired"></i></div>
                <div class="flow-node-label">Cilium Ingress<small>10.0.80.101</small></div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node flow-node-end">
                <div class="flow-node-icon"><i class="fas fa-th-large"></i></div>
                <div class="flow-node-label">App</div>
            </div>
        </div>

        <h3 class="homelab-subsection-title">Internal DNS resolution</h3>
        <div class="flow-diagram">
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-laptop"></i></div>
                <div class="flow-node-label">Device</div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-shield-alt"></i></div>
                <div class="flow-node-label">AdGuard DNS<small>via DHCP</small></div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-map-marker-alt"></i></div>
                <div class="flow-node-label">*.hoite.nl<small>ExternalDNS record</small></div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node">
                <div class="flow-node-icon"><i class="fas fa-network-wired"></i></div>
                <div class="flow-node-label">Cilium Ingress<small>10.0.80.101</small></div>
            </div>
            <div class="flow-arrow"><i class="fas fa-chevron-right"></i></div>
            <div class="flow-node flow-node-end">
                <div class="flow-node-icon"><i class="fas fa-th-large"></i></div>
                <div class="flow-node-label">App</div>
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
                        <td><strong>Profilarr</strong></td>
                        <td>Imports and syncs custom formats and quality profiles from TRaSH Guides to Radarr and Sonarr</td>
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
