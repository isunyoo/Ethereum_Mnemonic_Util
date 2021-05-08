================================ \
Ethereum Mnemonic Key Utils
================================

### Requirements

`pip3 install base58 ecdsa`


### Examples

#### Mnemonic key > private key

$ echo "Ethereum mnemonic keys" > mySeedFile \
$ python3 mnemonic_utils.py mySeedFile \


#### Mnemonic key > private key #2

from mnemonic_utils import mnemonic_to_private_key
private_key = mnemonic_to_private_key("Ethereum mnemonic keys")
print("Your private key is: {}".format(str(binascii.hexlify(private_key), 'utf-8')))


#### Private key > Mist keystore using eth-keyfile module

import binascii
import eth_keyfile
json_keyfile = eth_keyfile.create_keyfile_json(binascii.unhexlify(private_key), b"any password")


#### Private key > Mist keystore using web3.py module

import binascii
from web3.auto import w3
json_keyfile = w3.eth.account.privateKeyToAccount(binascii.unhexlify(private_key)).encrypt(b"any password")
