---
title: My attempts and notes
layout: default
parent: Python 
grand_parent: Coding Practices
---
# Personal Notes or My Attempts
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Tox 

Tox is a venv managing tool that aims to integrate automative and standardize testing  

You can follow this to setup your tox envs

> Note: the `ca-bundle.crt` looks like
> AB UniPass Authentications Root CA
> --- Begin Certificate ---
> AB UniPass Root CA, ACCVRAIZ1, AC RAIZ FNMT-RCM, Actalis Auth Root CA, AffirmTrust Networking, Affirmtrust Premium, Amazon Root CA2, 

```ini
[tox]
envlist =
    check_format

[testenv]
allowlist_externals = poetry
skip_install = true
deps=
    poetry==1.8.3
    poetry-dynamic-versioning[plugin]==1.2.0
setenv=
    POETRY_CERTIFICATES_ABC_ARTIFACTORY_CERT=/etc/pki/tls/certs/ca-bundle.crt


[testenv:poetry]

```

# Python tips 

## Finding prime numbers in a list (slow vs quick) [@b001](https://www.youtube.com/shorts/g9fIWtSexLs)
> ### Technique used: filter(), list-comprehension

```python
nums = range(1,1000) # list of nums from 1 - 1000

def is_prime(num):
    for x in range(2,num):
        if (num % x) == 0:
            return False # if not prime
        return True

# Built in python function: filter (def(),list of elements) 
# Means applying the function to each element in the list 
primes_slow = list(filter(is_prime,nums)) # list of filter object 
```
{:.note}

primes_slow returns a 1, which is NOT a prime number
{:.warning}

```python
def is_prime(num):
    for x in range(2,num):
        if (num%x) == 0:
            return False # if not prime
        return True

primes_quick = [x for x in range(2,1000) if is_prime(x)]
```
{:.note}