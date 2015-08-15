# YAML

![](https://travis-ci.org/owainlewis/yaml.svg?branch=master)

An updated YAML library for Clojure based on Snake YAML and heavily inspired by clj-yaml

[![Clojars Project](http://clojars.org/yaml/latest-version.svg)](http://clojars.org/yaml)

## Install

### Lein

```[io.forward/yaml "1.0.1"]```

### Maven

```
<dependency>
  <groupId>io.forward</groupId>
  <artifactId>yaml</artifactId>
  <version>1.0.1</version>
</dependency>
```

## Usage

```clojure
(ns demo.core
  (:require [yaml.core :as yaml]))
  
;; Parse a YAML file

(yaml/from-file "config.yml")

;; Parse a YAML string

(yaml/parse-string "foo: bar")

;; Dump YAML

(yaml/generate-string {:foo "bar"})

(yaml/generate-string
  [{:name "John Smith", :age 33}
   {:name "Mary Smith", :age 27}])
"- {name: John Smith, age: 33}\n- {name: Mary Smith, age: 27}\n"

(yaml/parse-string "
- {name: John Smith, age: 33}
- name: Mary Smith
  age: 27
")
=> ({:name "John Smith", :age 33}
    {:name "Mary Smith", :age 27})
```

This is mainly an updated version of clj-yaml with some updates

1. Updates snake YAML to latest version
2. Split reader and writer into separate protocols and files
3. Ability to read YAML from file in single function
4. Return vector [] instead of list when parsing java.util.ArrayList

## License

Copyright © 2015 Owain Lewis

Distributed under the Eclipse Public License 
