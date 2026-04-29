# NIC Diagnostics

## Baseline Checklist

Collect before theorizing:

- OS and release
- kernel version
- NIC model and driver
- queue and channel layout
- ring sizes
- offload settings
- IRQ mapping and CPU topology
- whether `irqbalance` is active

## Explain Before Acting

Before each command or change, state:

1. what you are checking
2. what you expect to learn
3. what the result means in context

## High-Value Commands

- `ethtool -g/-c/-k/-l/-x <iface>`
- `ethtool --show-priv-flags <iface>`
- `ethtool -S <iface>`
- `bpftool prog`, `bpftool map`, `bpftool net`
- `ip link set ... xdp`
- `grep <iface> /proc/interrupts`
- `cat /proc/irq/<N>/smp_affinity_list`
- `lscpu`
- `ss -s`
- `nstat`

## Counter Interpretation

### Hardware Drop Signals

- `rx_missed_errors`
- `rx_fifo_errors`
- `rx_dropped`

These usually indicate pre-DMA loss, ring exhaustion, or PCI backpressure.

### Intel-Specific Clues

- `rx_queue_N_drops`
- `port.rx_dropped`
- `port.rx_oversize`

Differentiate per-queue congestion from port-level issues.

### Mellanox-Specific Clues

- `rx_out_of_buffer`
- `rx_buff_alloc_err`
- `rx_no_dma_resources`
- `rx_cqe_compress_blks`
- `tx_tso_inner_packets`

When `rx_out_of_buffer` grows, check ring size and striding-RQ-related settings first.

## IRQ Workflow

1. Map IRQs from `/proc/interrupts`.
2. Read `smp_affinity_list` for each IRQ.
3. Compare IRQ placement to the RSS indirection table.
4. Check whether `irqbalance` will overwrite manual changes.
5. Correlate CPU placement with NUMA and hyperthread siblings.

## Kernel and libbpf Gates

- ring buffer support: kernel >= 5.8
- XDP frags: kernel >= 5.18
- kfuncs: kernel >= 5.13, more stable from 6.x
- older enterprise kernels may rely on backports, so verify features rather than assuming by version string alone

## netplan Rules

- Identify `networkd` vs `NetworkManager` first.
- Explain the difference between `netplan apply` and `netplan try`.
- Respect dependency order for bond, VLAN, and bridge stacks.

## Verification

After a tuning change, confirm success with:

- improved delta of relevant `ethtool -S` counters
- improved IRQ distribution
- reduced softirq or CPU hotspots
- improved traffic, latency, or drop metrics under comparable load
