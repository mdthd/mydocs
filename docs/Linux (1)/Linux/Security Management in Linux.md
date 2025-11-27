# Security Management in Linux

## Firewall

Define rules for network traffic

Traffic can be incoming or outgoing

:::info
Should not block **ident protocol** running on port 113

This sends packets to verify our Identity
:::

### Functions:

Analyzes packets incoming or outgoing

Allow traffic

Deny traffic

Forward traffic

### Looking for open ports

```bash
sudo ss -4nap
```

```bash
sudo ss -6nap
```

:::info
LISTEN → waiting for incoming connections

ESTAB → connected and it is outgoing connections
:::