# Not the official version

[Real README is elsewhere...](https://github.com/haad/proxychains).


# Changes in my fork


## Remove superfluous output

* remove version message
* default to quiet


## Remove version numbers from binary and library

Why would I want proxychains 3.1 installed when this better version exists?


## Simple SOCKS5 proxy mode

By setting the `PROXY_SOCKS5` environment variable, proxychains.conf will be
completely ignored.  Instead, proxychains will be set up to use a single SOCKS5
proxy on localhost on the port specified by the environment variable.

In addition, the `PROXY_DNS` env var, if set to anything (not just "1"), will
activate proxychains DNS resolving.

### Example

This makes it easy to route all traffic through an OpenSSH "dynamic proxy":

```sh
# choose a port
port=1234

# start a "dynamic proxy"
ssh -fN -D $port some.example.com

# use it
PROXY_SOCKS5=$port proxychains zsh
```
