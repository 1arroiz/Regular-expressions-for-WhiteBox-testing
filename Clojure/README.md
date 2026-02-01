# Full Regular Expression

```regex
^(?![ \t]*;).*?(?:\b(?:clojure\.core\/(?:eval|load-file|load-string|read-string)|\.shell\/sh|Runtime\.getRuntime\(\)\.exec|ProcessBuilder\.new)\b|\b(?:clojure\.java\.io\/copy|ring\.middleware\.multipart-params|clojure\.java\.io\/input-stream)\b|\b(?:clojure\.java\.jdbc\/query|clojure\.java\.jdbc\/execute!|next\.jdbc\/execute!)\b.*(?:\+|#\{|%s)|\b(?:monger\.collection\/(?:find|update|remove|insert)|congomongo\/with-mongo)\b.*(?:\$where|\$\w+)|\b(?:javax\.naming\.ldap|InitialLdapContext|DirContext)\b|\b(?:javax\.xml\.xpath\.XPathFactory|XPathExpression|XPathFactory\.newInstance)\b|\b(?:clojure\.edn\/read-string|clojure\.core\/read-string|java\.io\.ObjectInputStream\.readObject)\b|\b(?:selmer\/render|stencil\/render|hiccup\.core\/html)\b|\b(?:javax\.xml\.parsers\.DocumentBuilderFactory|SAXParserFactory|clojure\.data\.xml\/parse)\b|\b(?:clj-http\.client\/(?:get|post|put|delete)|http-kit\/client|java\.net\.URL|HttpURLConnection)\b|\b(?:clojure\.java\.io\/(?:reader|writer|delete-file|file)|java\.nio\.file\.Files)\b|\b(?:java\.util\.zip\.ZipFile|clojure\.java\.io\/input-stream.*ZipFile)\b|\b(?:buddy\.sign\.jwt\/(?:sign|verify)|buddy\.auth\.jwt)\b|\b(?:ring\.util\.response\/redirect|redirect-uri)\b|\b(?:ring\.middleware\.cors\/wrap-cors|Access-Control-Allow-Origin)\b|\b(?:loop|recur|while|future|pmap|mapv|reduce)\b.*(?:\*{2,}|range|repeat)|\b(?:clojure\.core\/re-matches|re-find|re-seq|java\.util\.regex\.Pattern\/compile)\b.*(?:\+|\*|\{[0-9,]+\})) 
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