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

---

### `server.banner`

| Introduced | Deprecated | Removed |
| - | - | - |
| Unversioned | N/A | N/A |

#### Parameters

None

#### Result

A string, with a banner sentence of the server.

### `server.cache`

| Introduced | Deprecated | Removed |
| - | - | - |
| Unversioned | N/A | N/A |

#### Parameters

None

#### Result

A integer.

### `server.debug`

| Introduced | Deprecated | Removed |
| - | - | - |
| `0.8` or `0.9` | N/A | N/A |

Renamed from `server.heapy`.

#### Parameters

| Index (Array) | Name (Object) | Description | Introduced |
| - | - | - | - |
| `0` | `password` (array only) | Password of server admin. Optional if there is none. | See method. |
| `1` | `s` | Expression to be evalutated. Optional. | See method. |

#### Result

A string, the result value of the evalutated expression.

### `server.donation_address`

| Introduced | Deprecated | Removed |
| - | - | - |
| `0.9` or `0.10` | N/A | N/A |

#### Parameters

#### Result

A string with an address of donation.

### `server.getpid`

| Introduced | Deprecated | Removed |
| - | - | - |
| `0.9` or `0.10` | N/A | N/A |

#### Parameters

None

#### Result

An integer, the Process ID of the server.

### `server.heapy`

| Introduced | Deprecated | Removed |
| - | - | - |
| `0.8` | `0.8` | `0.8` and `0.9` |

Renamed to `server.debug`.

#### Parameters

| Index (Array) | Name (Object) | Description | Introduced |
| - | - | - | - |
| `0` | `password` (array only) | Password of server admin. Optional if there is none. | See method. |
| `1` | `s` | Expression to be evalutated. Optional. | See method. |

#### Result

A string, the result value of the evalutated expression.

### `server.info`

| Introduced | Deprecated | Removed |
| - | - | - |
| Unversioned | N/A | N/A |

#### Parameters

| Index (Array) | Name (Object) | Description | Introduced |
| - | - | - | - |
| `0` | `password` (array only) | Password of server admin. Optional if there is none. | See method. |

#### Result

An array of all sessions that the server is currently serving. In the unversioned beginning it was only a string containing the session address, but even before 0.1 this was already changed to an object with the following properties:
 - `address`
 - `version`
 - `subscriptions`

And later also:
 - `time`
 - `name`

### `server.load`

| Introduced | Deprecated | Removed |
| - | - | - |
| Unversioned | N/A | N/A |

#### Parameters

None

#### Result

An integer, some approximate of a queue size.

### `server.peers`

| Introduced | Deprecated | Removed |
| - | - | - |
| ? | N/A | N/A |

TODO

### `server.peers.subscribe`

| Introduced | Deprecated | Removed |
| - | - | - |
| Unversioned | N/A | N/A |

It is not a subscription, but just a method to get peers.

#### Parameters

None

#### Result

An array with peers. Each array item is also an array, with the first element an IP address, the second element a hostname and later, also a third element with additional information. This third element is an array, where the first character identifies the information:
 - `v` (Version) - Indicates the version of the peer: `v1.0`
 - `p` (Pruning) - Indicates the pruning limit: `p10000`
 - `t` (TCP) - Indicates that the peer supports a TCP connection: `t` (default port 50001) or `t1234`.
 - `s` (SSL/TLS) - Indicates that the peer supports a SSL/TLS connection: `s` (default port 50002) or `s4321`.

### `server.stop`

| Introduced | Deprecated | Removed |
| - | - | - |
| Unversioned | N/A | N/A |

#### Parameters

| Index (Array) | Name (Object) | Description | Introduced |
| - | - | - | - |
| `0` | `password` (array only) | Password of server admin. Optional if there is none. | See method. |

#### Result

A string confirming the server will be stopped.

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
