Abstract:
This project is a practical research investigation focused on identifying phishing indicators based on a real-world simulation provided by the TryHackMe platform, as part of the SOC Level 1 learning path. During this project, I conducted an in-depth analysis of an email received by a sales executive, which raised suspicions due to an unexpected attachment and a reference to a money transfer.

Objective:
The primary goal of this research was to develop a structured approach to analyzing suspicious emails using techniques and tools commonly applied in a Security Operations Center (SOC) environment. The project aimed to enhance the following competencies:

Email header analysis and metadata extraction;

Detection of phishing techniques such as spoofing, fake reply-to addresses, and disguised malicious attachments;

Use of external tools and intelligence sources (WHOIS, MXToolbox, VirusTotal, etc.);

Safe handling and examination of potentially malicious files.

Methodology:
Initial Setup:
A suspicious .eml file simulating a phishing attempt was provided. The email was sent to a sales employee from a client contact and contained an unsolicited attachment along with a message about a financial transaction.

Email Analysis:

Used Thunderbird to visually examine the email and retrieve key information such as timestamp, sender name, email address, and reply-to field.

Identified discrepancies between the sender's name and reply-to address, suggesting email spoofing.

Technical Analysis:

Extracted the Originating IP from the email headers.

Performed WHOIS lookup on the IP, revealing it belonged to HostWinds LLC, a hosting provider frequently associated with suspicious activity.

Retrieved SPF and DMARC records for the sender’s domain using MXToolbox, identifying misconfigurations that allowed spoofing (SPF with -all, but no enforced DKIM or DMARC).

Attachment Analysis:

Saved the .CAB attachment (disguised as a PDF).

Generated a SHA256 hash of the file and scanned it using VirusTotal, confirming it as malicious.

Identified the actual file type as RAR archive, a common method for hiding malicious executables.

Findings:
Multiple Indicators of Compromise (IoCs) were identified:

Mismatch between the “From” and “Reply-To” addresses;

Use of a third-party hosting provider unrelated to the sender’s domain;

Disguised attachment (PDF icon, CAB extension, RAR content);

Weak SPF/DMARC configuration enabling spoofing.

All extracted data was documented in a structured format suitable for reporting to a senior analyst or incident response team.

Conclusion:
This project provided hands-on experience with phishing detection and investigation techniques. It demonstrated how much critical information can be obtained from email headers and attachments when analyzed properly.

I gained practical skills in using industry-standard tools and techniques for email threat analysis, and developed a repeatable methodology for investigating suspicious communications. The ability to identify spoofing attempts, examine email metadata, and safely handle potentially malicious files is essential for any SOC Level 1 analyst — and this project strengthened my readiness for that role.
