# Electrum Protocol

This document describes the full Electrum Protocol. This protocol is used over a TCP connection on port 50001 and SSL/TLS on port 50002. It uses JSON-RPC (both 1.0 and 2.0), where every message is terminated by a line break (`\n`).

## Methods

### `blockchain.block.get_header`

| Introduced | Deprecated | Removed |
| - | - | - |
| `0.2` | N/A | N/A |

#### Parameters

| Index (Array) | Name (Object) | Description |
| - | - | - |
| `0` | `height` (array only) | Height of block. |

### `blockchain.transaction.get_merkle`

| Introduced | Deprecated | Removed |
| - | - | - |
| `0.2` | N/A | N/A |

#### Parameters

| Index (Array) | Name (Object) | Description |
| - | - | - |
| `0` | `tx_hash` (array only) | Hash of transaction. |
| `1` | ... | ... |

## Versions

| Version |
| - |
| Unversioned |
|	`0.1`	|
|	`0.2`	|
|	`0.3`	|
|	`0.4`	|
|	`0.5`	|
|	`0.6` |
|	`0.7`	|
|	`0.8`	|
|	`0.9`	|
|	`0.10` |
|	`1.0` |
|	`1.1` |
|	`1.2` |
|	`1.3` |
|	`1.4` |
|	`1.4.1` |
|	`1.4.2` |
|	`1.4.3` |
