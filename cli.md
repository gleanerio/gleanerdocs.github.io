---
layout: default
title: CLI use
nav_order: 5
---

# CLI

## QuickStart

Before using Gleaner, note that Gleaner does have one prerequisite in the form of an accessible S3-compliant 
object store.  This can be AWS S3, Google Cloud Storage or others.  Also, there is the open source 
and free Minio object store which is used in many of the examples in GleanerIO. 

Once you have the object store running and ready, you are ready to run Gleaner. 
Pull down the release that matches your system from [version 3.0.4](https://github.com/gleanerio/gleaner/releases/tag/v3.0.4-dev).
Below is an example of pulling this down for a Linux system on AMD64 architecture.  

```
wget https://github.com/gleanerio/gleaner/releases/download/v3.0.4-dev/gleaner-v3.0.4-dev-linux-amd64.tar.gz
```

You will need a configuration file and an example of one can be found in the resources directory.  See also 
the config file in the Gleaner Config page.

You can set the values in this configuration file.  However, you can leave the Minio value empty and pass
them via environment variables.  This sort of approach can work better in some orchestration environments or just 
be a safer approach to managing these keys.  

```
export MINIO_ADDRESS=localhost
export MINIO_PORT=9000
export MINIO_USE_SSL=false
export MINIO_ACCESS_KEY=KEYVALUE
export MINIO_SECRET_KEY=SECRETVALUE
export MINIO_BUCKET=mybucket
```

With those set and your configuration file in place you can run Gleaner with 


```
  ./gleaner -cfg gleanerconfig.yaml --source nameFromCfgFile -rude
```


```
EarthCube Gleaner
Usage of /tmp/go-build589932266/b001/exe/main:
  -cfg string
        Configuration file (can be YAML, JSON) Do NOT provide the extension in the command line. -cfg file not -cfg file.yml (default "config")
  -log string
        The log level to output (trace | debug | info | warn | error | fatal) (default "warn")
  -mode string
        Set the mode (full | diff) to index all or just diffs (default "full")
  -rude
        Ignore any robots.txt crawl delays or allow / disallow statements
  -setup
        Run Gleaner configuration check and exit
  -source string
        Override config file source(s) to specify an index target
```
