Email Header Analysis - TASK-2 (Elevate Lab)

Objective
The objective was to analyze a potentially malicious email by reviewing its headers and body content to determine if it was a phishing attempt. This task involved manually inspecting the .eml file and identifying red flags based on standard phishing detection techniques.

How I Performed the Header Analysis

1. Opened the .eml File
   I used a text editor or email viewer to open the .eml file and located the email header section.
   The header section ends at the first blank line and includes metadata such as sender, return-path, SPF/DKIM/DMARC results, and received IP addresses.

2. Verified the Sender’s Email Address
   I looked for the From: and Return-Path: headers.
   The sender used emails.gorgias.com, which is unrelated to the official TrustWallet domain.
   There was a mismatch and suspicious formatting in the return path.

3. Checked SPF, DKIM, and DMARC Authentication Results
   I located the Authentication-Results header.
   The results were:

* SPF: pass
* DKIM: pass
* DMARC: fail
  This raised a red flag because DMARC failure indicates the sender is not authorized to send on behalf of the domain.

4. Identified the Sending IP Address
   I examined the Received headers and found the originating IP address: 143.55.227.147.
   I looked it up and found it belongs to Mailgun, a bulk email service that can be misused in phishing.

5. Inspected URLs in the Email Body
   I found the HTML content and located the call-to-action (CTA) link:
   [https://drop-coin-availablenow.site44.com/](https://drop-coin-availablenow.site44.com/)
   The link was routed through sciquest.com, which is a redirection technique used to disguise the final destination.

6. Checked for Urgent or Threatening Language
   The email contained the phrase:
   “All unverified accounts will be suspended on 10/31/2022.”
   This is a scare tactic commonly used in phishing.

7. Checked for Mismatched URLs
   The link text said “Confirm my wallet” but the actual destination was an unrelated domain.
   This is misleading and a classic phishing indicator.

8. Reviewed Language and Tone
   There were no major spelling errors, but the tone was impersonal and templated.
   It did not resemble a genuine customer support message.

Final Conclusion
The email exhibited several phishing indicators:

* Spoofed sender using a third-party domain (gorgias.io)
* Fails DMARC validation
* Redirects to suspicious links
* Uses urgency to create panic
* Impersonates TrustWallet branding
