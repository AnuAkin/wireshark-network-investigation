# Investigation Report

## Scenario

A packet capture was provided for analysis. The objective was to identify network activity, investigate communications between hosts, and determine whether any suspicious behavior was present.

---

## Methodology

The investigation followed these phases:

1. Packet overview
2. Protocol hierarchy analysis
3. Endpoint analysis
4. Conversation analysis
5. DNS investigation
6. HTTP investigation
7. TCP Stream analysis

---

## Key Findings

### Most Active Host

10.2.28.88 generated the largest amount of traffic throughout the capture.

---

### Primary Internal Communication

The majority of communication occurred between:

- 10.2.28.88
- 10.2.28.2

These communications consisted primarily of DNS, LDAP, TCP, and HTTP traffic.

---

### DNS Activity

Observed DNS requests included:

- wpad.mshome.net
- bing.com
- Internal Active Directory DNS lookups

No immediately suspicious domains were identified during the initial review.

---

### HTTP Analysis

HTTP GET and POST requests were identified.

Repeated POST requests were observed to:

fakeurl.htm

The requests originated from:

10.2.28.88

and were sent to:

45.131.214.85

---

### TCP Stream Analysis

Inspection of the TCP stream revealed:

- HTTP POST requests
- User-Agent: NetSupport Manager/1.3
- Connection: Keep-Alive
- Direct communication with a public IP address

Because NetSupport Manager is legitimate remote administration software that has also been abused in malicious campaigns, additional investigation would be recommended before determining whether the activity was authorized.

---

## Conclusion

No definitive malicious activity was confirmed during this investigation.

However, communication with an external public IP address using the NetSupport Manager User-Agent warranted additional review and would be appropriate for escalation in a production SOC environment.
