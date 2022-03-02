# Package flags

Package flags is a comfort layer around the package `flag`
of the standard library.

* Long or short key

* Falling back on environment variables

* Easy provision of default values

Usage

```bash
myexecutable  -config_file=config.json

myexecutable  -cfg=config.json

export CONFIG_FILE=config.json
```

* The long key takes precedence over the short key.

* The environment variable is only used,  
  if the short and the long key are empty.

* The equal signs are optional.

* The hyphen is required.

```golang
// usage inside your program
fl := flags.New()
fl.Add(
    util.FlagT{
        Long:       "config_file",
        Short:      "cfg",
        DefaultVal: "config.json",
        Desc:       "JSON file containing config data",
    },
)
fl.Add(
    ...
)
fl.Gen()  // taking in the values

cfgPath := fl.ByKey("cfg").Val  // reading some value

```
