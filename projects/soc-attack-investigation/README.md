# SOC Analyst Pre-Test: Attack Investigation and Detection Engineering

## Project Overview

As part of a SOC Analyst pre-test, I was provided with raw log data and tasked with identifying a potentially compromised host, reconstructing the suspected attack chain, and developing Splunk searches to detect related activity.

The investigation focused on correlating network and authentication events to build a clearer picture of the observed activity rather than treating each event in isolation.

## Objectives

- Identify the host associated with the suspicious activity.
- Reconstruct the suspected attack sequence from available logs.
- Investigate potential initial access, command-and-control (C2) communication, lateral movement, and data exfiltration.
- Develop Splunk SPL searches to identify relevant activity.
- Document findings and potential detection opportunities.

## Investigation Findings

The provided logs contained a sequence of events consistent with a potential multi-stage intrusion.

### 1. Initial Access: Archive Download over HTTP

**Observed activity:** A ZIP archive was downloaded over HTTP from an external IP address.

**Investigation focus:**
- Identify the source and destination IP addresses.
- Review the request URI, timestamp, and available file metadata.
- Determine whether the downloaded archive can be associated with subsequent suspicious activity.

**Detection objective:** Identify potentially suspicious executable or archive downloads over HTTP.

### 2. Potential Command-and-Control Beaconing

**Observed activity:** Repeated TLS connections to an external IP address occurred at approximately 60-second intervals.

**Investigation focus:**
- Examine connection timestamps and intervals.
- Identify the internal host initiating the connections.
- Review available network metadata and TLS indicators.
- Correlate the activity with the earlier download.

Regular intervals can be consistent with automated beaconing, but periodic connections alone do not confirm malware or C2 activity.

**Detection objective:** Identify repeated connections to the same destination at consistent intervals.

### 3. Potential Lateral Movement

**Observed activity:** SMB2 NTLMSSP authentication attempts were recorded between internal hosts.

**Investigation focus:**
- Identify the source and destination hosts.
- Determine whether authentication attempts succeeded or failed, if that information is available.
- Correlate the events with the suspected compromised host and surrounding timestamps.

SMB authentication activity can be legitimate. Additional evidence is needed to establish whether lateral movement occurred.

**Detection objective:** Surface suspicious SMB authentication activity for further investigation.

### 4. Potential Data Exfiltration

**Observed activity:** A large outbound HTTPS POST request was observed to an external IP address.

**Investigation focus:**
- Review request timestamps, destination, and available byte counts.
- Establish whether the traffic originated from the suspected compromised host.
- Correlate the event with earlier activity.
- Determine whether the available logs support a conclusion about data transfer.

A large outbound POST may warrant investigation, but it does not independently prove that data was stolen.

**Detection objective:** Identify unusually large outbound HTTPS requests for further review.

## Splunk Detection Searches

The following searches are based on the event signatures described in the assessment. Field names and data availability may need to be adjusted to match the actual log source.

### Suspicious Archive or Executable Download

```spl
index=* alert.signature="*Executable or archive download over HTTP*"
| table _time src_ip dest_ip uri
| sort 0 _time
```

**Purpose:** Review matching download events and establish their timeline.

### Potential C2 Communication

```spl
index=* alert.signature="*Suspicious TLS client fingerprint*"
| bin _time span=1m
| stats count by _time src_ip dest_ip
| sort 0 src_ip dest_ip _time
```

**Purpose:** Group matching TLS events into one-minute time buckets to help review repeated connections. This is a starting point, not a complete periodic-beacon detection rule; further analysis of connection intervals and TLS metadata is required.

### SMB Authentication Activity

```spl
index=* alert.signature="*SMB2 NTLMSSP AUTH attempt*"
| table _time src_ip dest_ip
| sort 0 _time
```

**Purpose:** Review SMB authentication events and correlate them with activity involving the suspected host.

These searches identify events matching the specified signatures. Their effectiveness depends on the underlying data, field mappings, and event coverage.

## Correlation and Attack Timeline

The investigation considered the following sequence:

1. An archive was downloaded over HTTP.
2. Repeated TLS connections to an external destination followed.
3. SMB authentication activity occurred between internal hosts.
4. A large outbound HTTPS POST was observed.

Correlating these events provides a hypothesis of a multi-stage intrusion. Establishing the exact sequence, confirming host relationships, and determining whether each stage succeeded requires validating timestamps, source and destination fields, and additional supporting evidence.

## Incident Response Recommendations

If these findings were observed in a live environment, appropriate next steps could include:

- Validate the suspected host using endpoint telemetry and additional logs.
- Preserve relevant log records and other forensic evidence.
- Investigate the downloaded archive in a controlled environment.
- Review DNS, TLS, firewall, and endpoint records for corroborating evidence.
- Check SMB authentication outcomes and identify other potentially affected hosts.
- Investigate the outbound HTTPS transfer and determine whether sensitive data was involved.
- Apply containment measures according to the incident response process if compromise is substantiated.
- Convert validated findings into tested detections and document false-positive considerations.

## Skills Demonstrated

- Security log analysis and correlation.
- Splunk Search Processing Language (SPL).
- Suspicious network activity investigation.
- Attack-chain reconstruction.
- Detection development.
- Incident triage and response recommendations.
- Technical documentation.

## Assessment Context and Limitations

This work was completed as a SOC Analyst pre-test using provided raw logs. The investigation reflects the evidence and task scope available during the assessment.
