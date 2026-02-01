# Full Regular Expression

```regex
^(?![ \t]*//).*?(?:\b(?:exec\.Command|exec\.CommandContext|syscall\.Exec|plugin\.Open|reflect\.Value\.Call)\b|\b(?:FormFile|io\.Copy|ioutil\.WriteFile|os\.Create|multipart\.NewReader|FileHeader\.Open)\b|\b(?:db\.Query|db\.Exec|db\.Prepare|Raw\(|Where\(|First\(|Find\()\b.*(?:\+|%s|\$\{)|\b(?:mongo\.Collection\.(?:Find|InsertOne|UpdateOne|DeleteOne|Aggregate)|bson\.M|bson\.D)\b.*(?:\$where|\$\w+)|\b(?:ldap\.Dial|ldap\.DialURL|SearchRequest|ModifyRequest|Bind)\b|\b(?:xpath\.Compile|xmlquery\.Find|xmlquery\.Query)\b|\b(?:gob\.Decode|gob\.NewDecoder|json\.Unmarshal|xml\.Unmarshal|yaml\.Unmarshal)\b|\b(?:template\.New|template\.Must|Execute|ExecuteTemplate|pongo2|mustache|amber|jet\.New)\b|\b(?:xml\.Unmarshal|xml\.NewDecoder|xmlquery|etree)\b|\b(?:http\.Get|http\.Post|http\.Do|http\.NewRequest|fasthttp\.Do|url\.Parse|net\.Dial|net\.DialTCP)\b|\b(?:os\.Open|os\.Remove|os\.Rename|os\.Mkdir|os\.MkdirAll|os\.Create|os\.WriteFile|ioutil\.ReadFile|ioutil\.WriteFile|filepath\.Walk)\b|\b(?:zip\.NewReader|zip\.OpenReader|archive/zip|tar\.NewReader|tar\.Reader)\b|\b(?:jwt\.Parse|jwt\.ParseWithClaims|jwt\.NewWithClaims|jwt\.Sign|jwt\.Verify)\b|\b(?:http\.Redirect|http\.RedirectHandler|c\.Redirect|ctx\.Redirect|Context\.Redirect)\b|\b(?:Access-Control-Allow-Origin|handlers\.CORS|WithOrigins|AllowCredentials)\b|\b(?:for\s*\{\}|for\s*true|while\s*true|time\.Sleep|ioutil\.ReadAll|bytes\.Repeat)\b|\b(?:regexp\.MustCompile|regexp\.Compile)\(".*(?:\+|\*){2,}.*"\))
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
^(?![ \t]*//).*?\b(http\.Redirect|http\.RedirectHandler|c\.Redirect|ctx\.Redirect|Context\.Redirect)\b
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