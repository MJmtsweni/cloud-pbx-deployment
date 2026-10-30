# Switch Telecom network requirements

Received from Switch Telecom support, 28 October 2026.

| Item | Value |
| --- | --- |
| Registrar / proxy | sip.switchtel.co.za |
| Switch server range | 196.216.192.0/24 (196.216.192.0 – 196.216.192.255, 256 addresses) |
| SIP signalling | UDP 5060–5063, inbound and outbound |
| RTP media (voice) | UDP 10000–20000, inbound and outbound |
| Also allow | NTP and web services |
| SIP ALG | Must be disabled |
| DTMF | RFC2833 |
| Codecs enabled on trunk | G.711 A-law, G.729a |

## How this is applied

- **VPS firewall (FreePBX Firewall):** 196.216.192.0/24 trusted for SIP and RTP. Everyone else blocked from SIP.
- **Asterisk RTP range:** 10000–20000 (FreePBX default) matches Switch.
- **SIP ALG:** not applicable on the VPS (public IP, no router in front). Disable it on the office router used by the softphones.
- **IP ACL on Switch side:** Switch locks the trunk to the VPS IP after first successful registration.
