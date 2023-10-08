# Electrum Protocol

This document describes the full Electrum Protocol. This protocol is used over a TCP connection on port 50001 and SSL/TLS on port 50002. It uses JSON-RPC (both 1.0 and 2.0), where every message is terminated by a line break (`\n`).

## Methods

All methods defined for the Electrum Protocol. The "(array only)" means that the parameter can only be sent in a parameter array, at the position of the index for that parameter.

### `blockchain.block.get_header`

| Introduced | Deprecated | Removed |
| - | - | - |
| `0.2` | N/A | N/A |

#### Parameters

| Index (Array) | Name (Object) | Description | Introduced |
| - | - | - | - |
| `0` | `height` (array only) | Height of block. | See method. |

### `blockchain.transaction.get_merkle`

| Introduced | Deprecated | Removed |
| - | - | - |
| `0.2` | N/A | N/A |

#### Parameters

| Index (Array) | Name (Object) | Description | Introduced |
| - | - | - | - |
| `0` | `tx_hash` (array only) | Hash of transaction. | See method. |
| `1` | ... | ... |

### `server.version`

| Introduced | Deprecated | Removed |
| - | - | - |
| Unversioned | N/A | N/A |

#### Parameters

| Index (Array) | Name (Object) | Description | Introduced |
| - | - | - | - |
| `0` | `version` (array only) | Version of the client. (Likely not the protocol version, or not anymore since 0.5/0.6.) Required until 0.9/0.10. Optional in 1.0. | See method. |
| `1` | `protocol_version` (array only) | Version of the protocol. Optional. Must be a string (or float) until at least 1.0. | `0.5` or `0.6` |

#### Result

 - For "Unversioned" and `0.1`, the result can be the string `ok`.
 - For `0.1` to `1.0`, the result can be a string with the protocol version code.

## Versions

| Version | Description |
| - | - |
| Unversioned | The early stage that there was no concept of protocol version yet. Unversioned servers can send `ok` when receiving a `server.version` message. |
|	`0.1`	| The first versioned protocol version. Servers with this version can send `ok` when receiving a `server.version` message, but they also can send `0.1`. |
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
