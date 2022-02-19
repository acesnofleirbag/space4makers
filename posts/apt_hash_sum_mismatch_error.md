# APT Hash Sum Mismatch Error

### Why this Happens?

For some reason the APT cannot makes the correct compression of the files,
occurring in this error

### Solution

```shell
sudo apt autoclean

sudo rm -rf /var/lib/apt/lists/*

sudo apt update --fix-missing
```

by @thebe111
