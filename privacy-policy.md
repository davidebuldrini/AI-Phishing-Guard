# Privacy Policy for AI Phishing Guard

**Effective Date:** April 14, 2025

Thank you for using **AI Phishing Guard** ("the Extension"), developed by **Reijo Hård** ("we," "us," or "our"). We are committed to protecting your privacy. This Privacy Policy explains how we handle information in relation to the Extension.

## 1. Purpose of the Extension

The Extension is designed to enhance your online security by detecting potential phishing websites, particularly those targeting financial information. It works by analyzing website characteristics when you interact with certain input fields.

## 2. Information We Process

To provide its core functionality, the Extension needs to process certain information. We have designed it with your privacy as a priority:

*   **Website URL:** When you focus on specific input fields (typically `<input>` elements, excluding `<textarea>`) on a website for the first time (per domain, unless the domain is already marked as 'safe' or 'risky' in your local storage), the Extension processes the full URL of the current webpage.
*   **Limited Page Metadata:** In order to perform the security analysis via our secure proxy, the Extension extracts and sends the following limited, generally non-personal metadata from the current webpage:
    *   The page `<title>`.
    *   The content of the `<meta name="description">` tag, if present.
    *   The text content of `<h1>` tags found on the page.
*   **Domain Status:** The Extension uses `chrome.storage.local` on your device to store the security status ('safe' or 'risky') associated with website hostnames (e.g., "example.com") that have been analyzed. This includes the status itself and a timestamp of the last check. Optionally, if a site is marked 'risky', the associated score and reason might be stored locally to be displayed again if needed. This data is stored locally within your browser's profile for the extension and is not tied to your personal identity on our servers.
*   **Interaction Data (Locally):** The content script temporarily detects `focusin` events on input fields to determine *when* to potentially trigger a check. The *content* you type into fields is **NEVER** read, stored, or transmitted by the Extension.

## 3. Information We DO NOT Collect

We are committed to minimizing data collection. The Extension **DOES NOT** collect, store, or transmit:

*   Your personal browsing history (beyond the single URL being analyzed at the time of the check).
*   Any data you type into forms or input fields (passwords, credit card numbers, names, emails, etc.).
*   The full text content or source code of the pages you visit (only the limited metadata mentioned above is used for analysis).
*   Your personal IP address (while our proxy server receives it as part of standard web requests, we do not log or use it for tracking purposes related to the analysis result).
*   Any other personally identifiable information (PII).

## 4. How Information is Used (API Call via Proxy)

*   **Analysis Trigger:** The analysis is triggered only under specific conditions: the domain hasn't been marked 'safe' or 'risky' previously in your local storage, and you focus on an input field identified by the extension as potentially sensitive (e.g., likely for credit card details based on its attributes).
*   **Secure Proxy:** When an analysis is needed, the Extension sends the **current page URL** and the **limited page metadata** (Title, Description, H1s) described in Section 2 to our secure backend proxy server hosted at **https://rapid-rain-3de8.bulbius81.workers.dev/**.
*   **AI Analysis:** Our proxy server then forwards this limited data, along with our secure API key, to a third-party AI service (currently Google Gemini) for risk assessment. The AI service analyzes the provided data and returns a risk score and justification.
*   **Response Handling:** Our proxy server receives the score and reason from the AI service and sends *only* this score and reason back to your Extension.
*   **No Data Retention (Proxy):** Our proxy server is designed to be stateless regarding your analysis requests. It does not store the URLs, metadata, or AI results associated with specific users after the analysis is complete and the result is relayed back to the extension.
*   **Local Status Storage:** Based on the AI score, the Extension stores the 'safe' or 'risky' status (and related metadata like timestamp, optionally score/reason) for the domain hostname in your browser's local storage (`chrome.storage.local`) to avoid re-analyzing the same domain unnecessarily on future visits or interactions.

## 5. Third-Party Services

*   **Google Gemini API:** We use Google's Gemini API via our secure proxy for the core website risk analysis. The data sent is limited as described above. Google's handling of data submitted via their API is governed by their own API terms and privacy policies.
*   **Cloudflare Workers (or your proxy provider):** Our secure proxy server is hosted on Cloudflare Workers. Their standard logging and security practices apply to the infrastructure supporting the proxy service.
*   **Trustpilot (User-Initiated):** The Extension's popup includes a button allowing *you* to optionally open the current site's review page on Trustpilot (`trustpilot.com`) in a new tab. No data is sent to Trustpilot automatically by the Extension. Your interaction with Trustpilot is subject to their own privacy policy.

## 6. Security

We take reasonable measures to protect information within our control:

*   The sensitive AI API key is kept secure on our backend proxy and is never included in the Extension's client-side code.
*   Communication between the Extension and the proxy uses HTTPS encryption.
*   The Extension only requests the minimum browser permissions necessary for its core functionality (currently `storage` and `tabs`).
*   Data stored locally (`chrome.storage.local`) by the extension is limited to domain safety statuses and related metadata.

However, please be aware that no internet transmission or electronic storage method is 100% secure.

## 7. User Control and Choices

*   **Disabling/Enabling:** You can disable or enable the Extension at any time through Chrome's extension management page (`chrome://extensions`).
*   **Clearing Storage:** You can clear the data stored by the Extension (the domain statuses) by uninstalling the extension or potentially through Chrome's site data clearing options.
*   **Proceeding on Risky Sites:** The warning dialog allows you to consciously choose to proceed on a site flagged as risky, which will then mark that site as 'safe' in the local storage for future visits.

## 8. Children's Privacy

The Extension is not intended for use by children under the age of 13 (or the relevant age of consent in your jurisdiction). We do not knowingly collect information from children.

## 9. Changes to This Privacy Policy

We may update this Privacy Policy from time to time. We will notify you of any significant changes by updating the effective date at the top of this policy and potentially through other means (like an update note in the extension description). We encourage you to review this policy periodically.

## 10. Contact Us

If you have any questions or concerns about this Privacy Policy or our data handling practices, please contact us at: **lassos_strider.1@icloud.com**

---
