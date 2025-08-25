# Full Regular Expression

```regex
^(?![ \t]*//).*?\b(exec\.Command|exec\.CommandContext|syscall\.Exec|plugin\.Open|reflect\.Value\.Call|FormFile|io\.Copy|ioutil\.WriteFile|os\.Create|multipart\.NewReader|FileHeader\.Open|db\.Query|db\.Exec|db\.Prepare|Raw\(|Where\(|First\(|Find\().*(\+|\%s|\$[{]|SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|TRUNCATE|mongo\.Collection\.(Find|InsertOne|UpdateOne|DeleteOne|DeleteMany|Aggregate)|bson\.M|bson\.D|DirContext\.search|InitialDirContext|SearchControls|LdapTemplate\.search|com\.unboundid\.ldap|xpath\.Compile|xmlquery\.Find|xmlquery\.Query|gob\.Decode|gob\.NewDecoder|json\.Unmarshal|xml\.Unmarshal|yaml\.Unmarshal|template\.New|template\.Must|Execute|ExecuteTemplate|pongo2|mustache|amber|jet\.New|xml\.NewDecoder|xmlquery|etree|http\.Get|http\.Post|http\.Do|http\.NewRequest|fasthttp\.Do|url\.Parse|net\.Dial|net\.DialTCP|os\.(Remove|Rename|Mkdir|MkdirAll|WriteFile)|filepath\.Walk|zip\.NewReader|zip\.OpenReader|archive/zip|tar\.NewReader|tar\.Reader|jwt\.Parse|jwt\.ParseWithClaims|jwt\.NewWithClaims|jwt\.Sign|jwt\.Verify|http\.Redirect|http\.RedirectHandler|c\.Redirect|Access-Control-Allow-Origin|handlers\.CORS|WithOrigins|AllowCredentials|for\s*\{\}|for\s*true|while\s*true|time\.Sleep|ioutil\.ReadAll|bytes\.Repeat|regexp\.MustCompile|regexp\.Compile)\b
```


## RCE(Os command unjection, Code Injection)

```
^(?![ \t]*//).*?\b(exec\.Command|exec\.CommandContext|syscall\.Exec|plugin\.Open|reflect\.Value\.Call)\b
```

## File Uploads

```
^(?![ \t]*//).*?\b(FormFile|io\.Copy|ioutil\.WriteFile|os\.Create|multipart\.NewReader|FileHeader\.Open)\b
```

## Sql Injection

```
^(?![ \t]*//).*?\b(db\.Query|db\.Exec|db\.Prepare|Raw\(|Where\(|First\(|Find\().*(\+|\%s|\$[{])|\b(SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|TRUNCATE)\b
```

## NoSQL Injection

```
^(?![ \t]*//).*?\b(mongo\.Collection\.(Find|InsertOne|UpdateOne|DeleteOne|Aggregate)|bson\.M|bson\.D).*(\$where|\$\w+)
```

## Ldap Injection

```
^(?![ \t]*//).*?\b(ldap\.Dial|ldap\.DialURL|SearchRequest|ModifyRequest|Bind)\b
```

## XPath Injection

```
^(?![ \t]*//).*?\b(xpath\.Compile|xmlquery\.Find|xmlquery\.Query)\b
```

## Insecure deserialization

```
^(?![ \t]*//).*?\b(gob\.Decode|gob\.NewDecoder|json\.Unmarshal|xml\.Unmarshal|yaml\.Unmarshal)\b
```

## SSTI

```
^(?![ \t]*//).*?\b(template\.New|template\.Must|Execute|ExecuteTemplate|pongo2|mustache|amber|jet\.New)\b
```

## XXE

```
^(?![ \t]*//).*?\b(xml\.Unmarshal|xml\.NewDecoder|xmlquery|etree)\b
```

## SSRF

```
^(?![ \t]*//).*?\b(http\.Get|http\.Post|http\.Do|http\.NewRequest|fasthttp\.Do|url\.Parse|net\.Dial|net\.DialTCP)\b
```

## File/Folder manipulation(read, delete, creation)

```
^(?![ \t]*//).*?\b(os\.Open|os\.Remove|os\.Rename|os\.Mkdir|os\.MkdirAll|os\.Create|os\.WriteFile|ioutil\.ReadFile|ioutil\.WriteFile|filepath\.Walk)\b
```

## Zip vulns

```
^(?![ \t]*//).*?\b(zip\.NewReader|zip\.OpenReader|archive/zip|tar\.NewReader|tar\.Reader)\b
```

## JWT

```
^(?![ \t]*//).*?\b(jwt\.Parse|jwt\.ParseWithClaims|jwt\.NewWithClaims|jwt\.Sign|jwt\.Verify)\b
```

## Open Redirect

```
^(?![ \t]*//).*?\b(jwt\.Parse|jwt\.ParseWithClaims|jwt\.NewWithClaims|jwt\.Sign|jwt\.Verify)\b
```

## Cors

```
^(?![ \t]*//).*?\b(Access-Control-Allow-Origin|handlers\.CORS|WithOrigins|AllowCredentials)\b
```

## Dos

```
^(?![ \t]*//).*?\b(for\s*\{\}|for\s*true|while\s*true|time\.Sleep|ioutil\.ReadAll|bytes\.Repeat)\b
```

## ReDOS

```
^(?![ \t]*//).*?\b(regexp\.MustCompile|regexp\.Compile)\(".*(\+|\*){2,}.*"\)
```