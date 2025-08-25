# Full Regular Expression

```regex
^(?![ \t]*;).*?\b(clojure\.java\.shell/sh|Runtime/getRuntime|ProcessBuilder|Class/forName|resolve|requiring-resolve|ns-resolve|var|get-method|clojure\.lang\.Reflector|eval|load-string|load-reader|slurp|spit|jdbc/query|jdbc/execute!|next\.jdbc/execute!|doto|defrecord|proxy|reify|gen-class|mongo\.client|get-collection|find|insert|update|delete|aggregate|DirectorySearcher|DirContext|InitialDirContext|SearchControls|XPathFactory|XPathExpression|DocumentBuilderFactory|TransformerFactory|ObjectInputStream|XMLDecoder|cheshire\.parse-string|clojure\.data\.json/read-str|selmer/render|enlive/html-resource|hiccup/html|clostache/render|mustache/render|clojure\.xml/parse|SAXParserFactory|XMLInputFactory|HttpURLConnection|URL\.openConnection|http/get|http/post|client/request|java\.net\.Socket|clojure\.java\.io/copy|ZipInputStream|JarFile|io\.jsonwebtokens|buddy\.sign/jws|ring.util.response/redirect|while\s*\(true\)|dotimes|Thread/sleep|BigInteger\.pow|re-pattern|re-matcher|re-find|re-seq)\b.*(\+|#\{|\%s|SELECT|INSERT|UPDATE|DELETE|DROP|ALTER)
```

## RCE(Os command unjection, Code Injection)

```
^(?![ \t]*;).*\b(clojure\.core/(eval|load-file|load-string|read-string)|.shell/sh|Runtime\.getRuntime\(\).exec|ProcessBuilder\.new)\b
```

## File Uploads

```
^(?![ \t]*;).*\b(clojure\.java\.io/copy|ring\.middleware\.multipart-params|clojure\.java\.io/input-stream)\b
```

## Sql Injection

```
^(?![ \t]*;).*\b(clojure\.java\.jdbc/query|clojure\.java\.jdbc/execute!|next\.jdbc/execute!)\b.*(\+|\#\{|\%s|SELECT|INSERT|UPDATE|DELETE|DROP|ALTER)
```

## NoSQL Injection

```
^(?![ \t]*;).*\b(monger\.collection/(find|update|remove|insert)|congomongo/with-mongo)\b.*(\$where|\$\w+)
```

## Ldap Injection

```
^(?![ \t]*;).*\b(javax\.naming\.ldap|InitialLdapContext|DirContext)\b
```

## XPath Injection

```
^(?![ \t]*;).*\b(javax\.xml\.xpath\.XPathFactory|XPathExpression|XPathFactory\.newInstance)\b
```

## Insecure deserialization

```
^(?![ \t]*;).*\b(clojure\.edn/read-string|clojure\.core/read-string|java\.io\.ObjectInputStream\.readObject)\b
```

## SSTI

```
^(?![ \t]*;).*\b(selmer/render|stencil/render|hiccup\.core/html)\b
```

## XXE

```
^(?![ \t]*;).*\b(javax\.xml\.parsers\.DocumentBuilderFactory|SAXParserFactory|clojure\.data\.xml/parse)\b
```

## SSRF

```
^(?![ \t]*;).*\b(clj-http\.client/(get|post|put|delete)|http-kit/client|java\.net\.URL|HttpURLConnection)\b
```

## File/Folder manipulation(read, delete, creation)

```
^(?![ \t]*;).*\b(clojure\.java\.io/(reader|writer|delete-file|file)|java\.nio\.file\.Files)\b
```

## Zip vulns

```
^(?![ \t]*;).*\b(java\.util\.zip\.ZipFile|clojure\.java\.io/input-stream.*ZipFile)\b
```

## JWT

```
^(?![ \t]*;).*\b(buddy\.sign\.jwt/(sign|verify)|buddy\.auth\.jwt)\b
```

## Open Redirect

```
^(?![ \t]*;).*\b(ring\.util\.response/redirect|redirect-uri)\b
```

## Cors

```
^(?![ \t]*;).*\b(ring.middleware.cors/wrap-cors|Access-Control-Allow-Origin)\b
```

## Dos

```
^(?![ \t]*;).*\b(loop|recur|while|future|pmap|mapv|reduce)\b.*(\*{2,}|range|repeat)
```

## ReDOS

```
^(?![ \t]*;).*\b(clojure\.core/re-matches|re-find|re-seq|java\.util\.regex\.Pattern/compile)\b.*(\+|\*|\{[0-9,]+\})
```