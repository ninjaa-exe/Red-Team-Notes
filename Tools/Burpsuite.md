## Installation
`sudo apt-get install burpsuite`
# Proxy

The proxy allows the user to see and modify the content of requests and responses while they are in transit. Additionally, it allows the user to send the request or response to another BurpSuite tool, so there is no need to copy and paste.

# Intruder

The intruder is used to test different values in a request field and check the response to see if it was a success or failure. To add a field, simply select the part you want to modify and click on the “Add” option and to remove it, simply do the same process and click on “Clear”. It has different types of attack and is commonly used to brute force logins, passwords, pins and other forms and also for XSS or SQL Injection

## Sniper

This attack places each payload into each payload position in turn. It uses a single payload set.

The Sniper attack is useful for fuzzing a number of request parameters individually for common vulnerabilities.

## Battering ram

This attack places the same payload into all of the defined payload positions simultaneously. It uses a single payload set.

The Battering ram attack is useful where an attack requires the same input to be inserted in multiple places within the request. For example, a username within a cookie and a body parameter.

## Pitchfork

This attack iterates through a different payload set for each defined position. Payloads are placed into each position simultaneously. For example, the first three requests would be:

- Request one:
    - Position 1 = First payload from Set 1.
    - Position 2 = First payload from Set 2.
- Request two:
    - Position 1 = Second payload from Set 1.
    - Position 2 = Second payload from Set 2.
- Request three:
    - Position 1 = Third payload from Set 1.
    - Position 2 = Third payload from Set 2.

The Pitchfork attack is useful where an attack requires different but related input to be inserted in multiple places within the request. For example, to place a username in one parameter, and a known ID number corresponding to that username in another parameter.

## Cluster bomb

This attack iterates through a different payload set for each defined position. Payloads are placed from each set in turn, so that all payload combinations are tested. For example, the first three requests would be:

- Request one:
    - Position 1 = First payload from Set 1.
    - Position 2 = First payload from Set 2.
- Request two:
    - Position 1 = First payload from Set 1.
    - Position 2 = Second payload from Set 2.
- Request three:
    - Position 1 = First payload from Set 1.
    - Position 2 = Third payload from Set 2.

The Cluster bomb attack is useful where an attack requires unrelated or unknown input to be inserted in multiple places within the request. For example, when guessing both a username and password.

# Repeater

The repeater allows you to send requests repeatedly with manual modifications, being mainly used for:

- Verifying whether the user-supplied values are being verified.
- If user-supplied values are being verified, how well is it being done?
- What values is the server expecting in an input parameter/request header?
- How does the server handle unexpected values?
- Is input sanitation being applied by the server?
- How well the server sanitizes the user-supplied inputs?
- What is the sanitation style being used by the server?
- Among all the cookies present, which one is the actual session cookie.
- How is CSRF protection being implemented and if there is a way to bypass it?

# Decoder

Decoder lists the common encoding methods like URL, HTML, Base64, Hex, etc. This tool comes handy when looking for chunks of data in values of parameters or headers. It is also used for payload construction for various vulnerability classes. It is used to uncover primary cases of IDOR and session hijacking.