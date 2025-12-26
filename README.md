# PHP filter chain generator
A CLI to generate PHP filters chain, get your RCE without uploading a file if you control entirely the parameter passed to a require or an include in PHP!

# Usage
## Usage

### Help

```bash
$ python3 php_filter_chain_generator.py --help
usage: php_filter_chain_generator.py [-h] [--chain CHAIN] [--rawbase64 RAWBASE64]

PHP filter chain generator.

optional arguments:
  -h, --help            show this help message and exit
  --chain CHAIN         Content you want to generate. (you will maybe need to pad with spaces for your payload to work)
  --rawbase64 RAWBASE64
                        The base64 value you want to test, the chain will be printed as base64 by PHP, useful to debug.

                        The base64 value you want to test, the chain will be printed as base64 by PHP, useful to debug.

```

### Parameters
```text
--chain CHAIN
    PHP payload to convert into a filter chain.
    Padding with spaces may be required depending on payload length.

    Example:
    $ python3 php_filter_chain_generator.py --chain ' '

--rawbase64 RAWBASE64
    Base64 string to test.
    The tool prints the decoded output as processed by PHP.
```
