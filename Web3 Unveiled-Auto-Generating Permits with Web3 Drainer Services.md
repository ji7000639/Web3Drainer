# Unlocking Web3 Secrets: How to Automate Permit Signatures for Tokens

As I ventured into the realm of Web3, one question that immediately piqued my curiosity was how to determine if a token has a 'Permit' function and, if so, how to automatically generate the necessary parameters for its signature.

Now, I could simply tell you to fetch the API for the ABI (Application Binary Interface) definition and check if the 'permit' is included, but is that the whole story? Well, there's a twist involving proxy contracts, which we'll get to later. First, let’s explore the solution I uncovered:

## Identifying the 'Permit' Function Signature

After some digging, I discovered that most tokens with a 'Permit' function feature a read-only ABI definition called `DOMAIN_SEPARATOR`. But what about tokens that support 'Permit' without this property? They do exist, and they use `DOMAIN_TYPEHASH` and `PERMIT_TYPEHASH` instead. Therefore, it's crucial to check for all three to ensure accuracy.

## Assembling the Parameters for a 'Permit'

Typically, you'll need parameters like `name`, `version`, and `nonce`. But is the ABI for `nonce` always the same? Not quite. There are several variations to look out for, such as `['nonces', '_nonces', 'nonce', 'getNonce']`. It's possible to make individual requests for these functions to retrieve the corresponding values, thus...
