## Config File


### Source

Sources can be defined as two type. A sitemap, which is a traditional sitemap that 
points to resources or a sitemap index that points to a set of sitemaps.

The other is a sitegraph, which is a pre-computed graph for a site.  

Examples of their formats respectively are:

#### sitemap

```yaml
 sourcetype: sitemap
  name: unidata
  logo: ""
  url: https://www.unidata.ucar.edu/sitemap.xml
  headless: false
  pid: https://www.re3data.org/repository/r3d100010355
  propername: UNIDATA
  domain: http://www.unidata.ucar.edu/
  active: false
  credentialsfile: ""
  other: {}
  headlesswait: 0
  delay: 0
```

#### sitegraph

```yaml  
- sourcetype: sitegraph
  name: aquadocs
  logo: ""
  url: https://oih.aquadocs.org/aquadocs.json
  headless: false
  pid: http://hdl.handle.net/1834/41372
  propername: AquaDocs
  domain: https://aquadocs.org
  active: false
  credentialsfile: ""
  other: {}
  headlesswait: 0
  delay: 0
```

### Example config file

A complete configuration file follows.  

```yaml
context:
  cache: true
  strict: true
contextmaps:
  - prefix: "https://schema.org/"
    file: "./jsonldcontext.json"  # wget http://schema.org/docs/jsonldcontext.jsonld
  - prefix: "http://schema.org/"
    file: "./jsonldcontext.json"  # wget http://schema.org/docs/jsonldcontext.jsonld
gleaner:
  mill: true
  runid: runX
  summon: true
summoner:
    after: ""
    delay:  # milliseconds (1000 = 1 second) to delay between calls (will FORCE threads to 1)
    headless: http://geocodes-dev.earthcube.org:9222
    mode: full
    threads: 5
millers:
  graph: true
minio:
  address:
  port:
  ssl:
  accesskey:
  secretkey:
  bucket:
sources:
- sourcetype: sitemap
  name: unidata
  logo: ""
  url: https://www.unidata.ucar.edu/sitemap.xml
  headless: false
  pid: https://www.re3data.org/repository/r3d100010355
  propername: UNIDATA
  domain: http://www.unidata.ucar.edu/
  active: false
  credentialsfile: ""
  other: {}
  headlesswait: 0
  delay: 0
- sourcetype: sitegraph
  name: aquadocs
  logo: ""
  url: https://oih.aquadocs.org/aquadocs.json
  headless: false
  pid: http://hdl.handle.net/1834/41372
  propername: AquaDocs
  domain: https://aquadocs.org
  active: false
  credentialsfile: ""
  other: {}
  headlesswait: 0
  delay: 0

```