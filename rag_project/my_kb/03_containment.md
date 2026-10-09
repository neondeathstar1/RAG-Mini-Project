# Containment and Cleanup

Once an email is confirmed malicious, the first action is to remove every copy from the company. Analysts run a content search in Microsoft Purview to find the message in all mailboxes and then soft delete it. The target is to finish this within 30 minutes of the malicious verdict. Soft deleted messages stay recoverable for 14 days in case a mistake is found.

Next, analysts block the indicators. The sender address and domain are added to the block list on the secure email gateway. Malicious URLs are blocked at the web proxy, and file hashes are added to the blocklist in the EDR platform. Every block entry is tagged with the ticket number so it can be reviewed and removed later.

If a user entered credentials, the analyst resets the user's password, revokes all active sessions and refresh tokens, and requires the user to register multifactor authentication again. The analyst then reviews the sign-in logs for the previous 7 days and looks for new inbox rules, because attackers often create a rule that forwards or hides messages.

If an attachment executed, the analyst uses the EDR network containment feature to isolate the device from everything except the security console. The device is not powered off, because memory contents may be needed for analysis. The device stays isolated until Tier 2 confirms it is clean or it is reimaged.

All evidence, including the original message, headers, sandbox reports, and logs, is saved to the case folder and kept for 12 months.
