# APT Hash Sum Mismatch

### Why This Happens?

For some reason the APT cannot makes the correct compression of the files, generating this error

### Solution

```console
$ sudo apt autoclean
$ sudo rm -rf /var/lib/apt/lists/*
$ sudo apt update --fix-missing
```

