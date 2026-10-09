# Triage Procedure for Reported Phishing

A Tier 1 analyst claims each SEC-PHISH ticket and works through five checks in order. First, read the email headers and confirm the SPF, DKIM, and DMARC results. A message that fails DMARC and claims to be from an internal domain is treated as spoofed. Second, compare the display name, the From address, and the Reply-To address, because attackers often make the display name match an executive while the real address belongs to a free mail service.

Third, look up the sender domain. A domain registered fewer than 30 days ago is considered suspicious by default. Fourth, detonate every link and attachment in the internal sandbox called Detonator, never on an analyst workstation. Detonator returns a verdict and a screenshot of the landing page within about 3 minutes. Fifth, check every URL, IP address, and file hash against VirusTotal and the company threat intelligence feed.

After the checks, the analyst assigns a severity. Severity 1 means a user submitted credentials or a malicious attachment executed on a device. Severity 2 means a user clicked a malicious link but no credentials were entered, or the message targeted an executive or someone in the finance team. Severity 3 means the email is malicious but nobody interacted with it. Severity 4 means the email is spam or harmless.

Triage time targets depend on severity. For Severity 1 the analyst must begin work within 15 minutes of the ticket being created. For Severity 2 the target is 1 hour, for Severity 3 it is 4 business hours, and for Severity 4 it is the next business day. Analysts record every indicator they find in the ticket, including sender address, subject line, URLs, and file hashes, so that other analysts can search for the same campaign.
