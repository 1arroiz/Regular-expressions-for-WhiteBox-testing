# Full Regular Expression without false positives(mostly)

```regex
^(?![ \t]*//)(?![ \t]*\*).*?(?:\b(?:Runtime\.getRuntime\(\)\.exec|ProcessBuilder|Process\.start|ScriptEngineManager|javax\.script|kotlin\.script|KClass\.java\.classLoader\.loadClass|Class\.forName|Method\.invoke)\b|\b(?:MultipartFile|Part|getPart|transferTo|FileOutputStream|Files\.write|ServletInputStream)\b|\b(?:Statement\.execute(?:Query|Update)?|Connection\.createStatement|prepareStatement\((?:.*\+.*|\$\{)|ResultSet|JdbcTemplate\.query|EntityManager\.createQuery)\b|\b(?:MongoCollection\.find|findOne|updateOne|updateMany|deleteOne|deleteMany|aggregate|BsonDocument|BasicDBObject|Criteria\.where|SpringDataMongo)\b|\b(?:DirContext\.search|InitialDirContext|SearchControls|LdapTemplate\.search|UnboundID|com\.unboundid\.ldap)\b|\b(?:XPathFactory\.newInstance|XPathExpression\.compile|XPath\.evaluate|DocumentBuilderFactory\.newInstance)\b|\b(?:ObjectInputStream\.readObject|XMLDecoder\.readObject|kryo\.readClassAndObject|Gson\.fromJson|Jackson\.ObjectMapper\.readValue|kotlinx\.serialization\.decodeFromString)\b|\b(?:Thymeleaf|FreeMarker|Mustache|Velocity|PebbleEngine|TemplateEngine|StringTemplate|handlebars)\b|\b(?:DocumentBuilderFactory\.newInstance|SAXParserFactory\.newInstance|TransformerFactory\.newInstance|XMLInputFactory\.newInstance)\b|\b(?:HttpURLConnection|URL\.openConnection|OkHttpClient\.newCall|WebClient\.create|getForObject|getInputStream|Socket)\b|\b(?:File\.(?:createNewFile|delete|mkdir|mkdirs|renameTo|setReadable|setWritable)|Files\.(?:createFile|delete|move|copy|readAllBytes)|Path\.toFile|FileOutputStream|FileInputStream|BufferedReader|BufferedWriter)\b|\b(?:ZipInputStream|ZipFile|JarFile|JarInputStream|java\.util\.zip)\b|\b(?:Jwts\.parser|Jwts\.parse|JwtHelper|SignedJWT\.parse|Auth0\.JWT|io\.jsonwebtoken)\b|\b(?:response\.sendRedirect|HttpServletResponse\.encodeRedirectURL|RedirectView|return\s+"redirect:")\b|\b(?:@CrossOrigin|CorsFilter|setHeader\("Access-Control-Allow-Origin"|CorsConfiguration)\b|\b(?:Thread\.sleep|while\s*\(true\)|for\s*\(;;\)|BigInteger\.(?:pow|modPow)|Regex\(".*(?:\*|\+){2,}.*"\))\b|\b(?:Pattern\.compile|Regex\(|RegexOption)\b.*(?:\(\.\*\)|\(\[[^\]]+\]\*\)|(?:\+|\*){2,}))
```

## RCE(Os command unjection, Code Injection)

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(Runtime\.getRuntime\(\)\.exec|ProcessBuilder|Process\.start|ScriptEngineManager|javax\.script|kotlin\.script|KClass\.java\.classLoader\.loadClass|Class\.forName|Method\.invoke)\b
```

## File Uploads

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(MultipartFile|Part|getPart|transferTo|FileOutputStream|Files\.write|ServletInputStream)\b
```

## Sql Injection

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(Statement\.execute(Query|Update)?|Connection\.createStatement|prepareStatement\((.*\+.*|\$[{])|ResultSet|JdbcTemplate\.query|EntityManager\.createQuery)\b|\b(SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|TRUNCATE)\b
```

## NoSQL Injection

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(MongoCollection\.find|findOne|updateOne|updateMany|deleteOne|deleteMany|aggregate|BsonDocument|BasicDBObject|Criteria\.where|SpringDataMongo)\b
```

## Ldap Injection

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(DirContext\.search|InitialDirContext|SearchControls|LdapTemplate\.search|UnboundID|com\.unboundid\.ldap)\b
```

## XPath Injection

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(XPathFactory\.newInstance|XPathExpression\.compile|XPath\.evaluate|DocumentBuilderFactory\.newInstance)\b
```

## Insecure deserialization

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(ObjectInputStream\.readObject|XMLDecoder\.readObject|kryo\.readClassAndObject|Gson\.fromJson|Jackson\.ObjectMapper\.readValue|kotlinx\.serialization\.decodeFromString)\b
```

## SSTI

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(Thymeleaf|FreeMarker|Mustache|Velocity|PebbleEngine|TemplateEngine|StringTemplate|handlebars)\b
```

## XXE

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(DocumentBuilderFactory\.newInstance|SAXParserFactory\.newInstance|TransformerFactory\.newInstance|XMLInputFactory\.newInstance)\b
```

## SSRF

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(HttpURLConnection|URL\.openConnection|OkHttpClient\.newCall|WebClient\.create|getForObject|RestTemplate|getInputStream|Socket)\b
```

## File/Folder manipulation(read, delete, creation)

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(File\.(createNewFile|delete|mkdir|mkdirs|renameTo|setReadable|setWritable)|Files\.(createFile|delete|move|copy|readAllBytes)|Path\.toFile|FileOutputStream|FileInputStream|BufferedReader|BufferedWriter)\b
```

## Zip vulns

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(ZipInputStream|ZipFile|JarFile|JarInputStream|java\.util\.zip)\b
```

## JWT

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(Jwts\.parser|Jwts\.parse|JwtHelper|SignedJWT\.parse|Auth0\.JWT|io\.jsonwebtoken)\b
```

## Open Redirect

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(response\.sendRedirect|HttpServletResponse\.encodeRedirectURL|RedirectView|return\s+"redirect:")\b
```

## Cors

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(@CrossOrigin|CorsFilter|setHeader\("Access-Control-Allow-Origin"|CorsConfiguration)\b
```

## Dos

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(Thread\.sleep|while\s*\(true\)|for\s*\(;;\)|BigInteger\.(pow|modPow)|Regex\(".*(\*|\+){2,}.*"\))\b
```

## ReDOS

```
^(?![ \t]*//)(?![ \t]*\*).*?\b(Pattern\.compile|Regex\(|RegexOption)\b.*(\(\.\*\)|\(\[[^\]]+\]\*\)|(\+|\*){2,})
```