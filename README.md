# Achilles Shield - Browser Extension for Focused Learning

Achilles Shield is a Chrome extension designed to create a safer and more focused online learning environment for students at a specific private middle school. It provides customizable web filtering capabilities, allowing the school to manage website access, block inappropriate content, and restrict access to distracting or unfiltered online resources.

**This extension is intended for *unlisted* distribution and use *exclusively* within the school's managed environment. It is *not* designed for general public use.**

## Features

*   **Customizable Web Filtering:**
    *   Uses a combination of whitelists, blacklists, and keyword filtering to control website access.
    *   Filtering rules are defined in a remotely hosted configuration file (`Security_System.txt`), allowing for centralized management and updates by the school's IT staff.
    *   Leverages the `declarativeNetRequest` API for efficient and privacy-respecting filtering.

*   **Google Service Management:**
    *   Specifically restricts access to certain Google services (e.g., Google Images, YouTube) that can easily lead to unfiltered and inappropriate content.
    *   Redirects users to safer alternatives when attempting to access blocked Google services.
    *   Allows core Google Search functionality while maintaining restrictions on potentially problematic areas.

*   **Emergency Shutdown:**
    *   Includes a remote "kill switch" mechanism that allows the school to instantly disable the extension across all devices in case of an unforeseen issue or emergency.
    *   The shutdown status is controlled via a simple text file hosted on Google Docs.

*   **Local Control and Privacy:**
    *   The extension operates entirely locally, enforcing the school-defined filtering rules.
    *   *No user data is collected, stored, or transmitted.* The extension does not track browsing history, search queries, or any other personal information.
    * Limited google authentication, only used for authentication processes.

* **Administrative Control**
    * There is an administrative control panel (Password Protected)
    * SHA-256 encryption of the admin password.

## Installation (For School IT Staff)

1.  **Download:** Download the extension files from this repository.
2.  **Chrome Extensions Page:** Open Chrome and navigate to `chrome://extensions`.
3.  **Developer Mode:** Enable "Developer mode" in the top right corner.
4.  **Load Unpacked:** Click the "Load unpacked" button.
5.  **Select Directory:** Select the directory where you downloaded the extension files.
6. **Publish to Chrome Webstore:** The extension must be published, unlisted, to the chrome webstore.
7.  **Deployment:** Deploy the extension to student Chromebooks through the school's Google Admin console. *Do not distribute the extension publicly.*

## Configuration (`Security_System.txt`)

The extension's filtering rules are defined in the `Security_System.txt` file, which is fetched from this repository:

[https://raw.githubusercontent.com/ThatOneFungi/SecuritySystem/refs/heads/main/Security_System.txt](https://raw.githubusercontent.com/ThatOneFungi/SecuritySystem/refs/heads/main/Security_System.txt)

The file is in JSON format and has the following structure:

```json
{
  "whitelist": [
    "example.com",
    "another-example.org"
  ],
  "blockedTerms": [
    "inappropriateTerm1",
    "inappropriateTerm2"
  ],
  "blacklistedUrls": [
    "distracting-site.com",
    "another-bad-site.net"
  ],
  "blockedGoogleServices": [
      { "type": "path", "value": "imghp" },
      { "type": "path", "value": "videos" },
      { "type": "subdomain", "value": "news" }
  ],
  "redirectUrl": "https://www.safesearchkids.com/",
  "adminPassword": "YOUR_HASHED_PASSWORD_HERE"
}
