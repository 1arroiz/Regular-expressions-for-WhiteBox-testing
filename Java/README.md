# Full Regular Expression

```regex
^(?![ \t]*//)(?![ \t]*/\*).*?(?:\b(?:Runtime\.getRuntime\(\)\.exec|ProcessBuilder\s*\(|ScriptEngineManager\.getEngineByName|javax\.tools\.JavaCompiler|Method\.invoke|Class\.forName|GroovyShell|NashornScriptEngineFactory|ScriptEngine\.eval|eval\s*\(|defineClass\s*\(|ClassLoader\s*\(|URLClassLoader\s*\(|Context\s*\(|loadClass\s*\(|lookup\s*\(|lookupLink\s*\(|start\s*\(|exec\s*\(|loadLibrary\s*\(|load\s*\(|Runtime\s*\(|System\s*\()\b|\b(?:javax\.servlet\.http\.Part|getInputStream\(\)|MultipartFile|FileItem|DiskFileItemFactory|ServletFileUpload)\b|\b(?:Statement\.execute(?:Query|Update)|Connection\.createStatement|PreparedStatement\.execute.*\(|JdbcTemplate\.query|JdbcTemplate\.update|EntityManager\.createQuery|SQLQuery)\b.*(?:\+|\?|%s|\$)|\b(?:DBCollection\.find|DBCollection\.insert|DBCollection\.update|MongoCollection<.*>\.(?:find|insertOne|updateOne|deleteOne)|BasicDBObject|Document\(|@Query)\b.*(?:\$where|\$regex|\$ne|\$gt|\$lt)|\b(?:DirContext\.search|InitialDirContext|SearchControls|Attributes|LdapContext)\b.*(?:\+|%s|\$)|\b(?:javax\.xml\.xpath\.XPathFactory|XPathExpression\.compile|DocumentBuilderFactory\.newInstance|TransformerFactory\.newInstance)\b|\b(?:ObjectInputStream\.readObject|XMLDecoder|JSONDeserializer|readObjectOverride|SerializationUtils\.deserialize|readObject\s*\()\b|\b(?:JtwigTemplate|PebbleEngine|FreeMarker|VelocityEngine|Thymeleaf|MustacheFactory|GroovyShell|MVEL\.eval)\b|\b(?:DocumentBuilderFactory(?:\.newInstance)?\s*\(|SAXParserFactory(?:\.newInstance)?\s*\(|XMLInputFactory(?:\.newInstance)?\s*\(|Unmarshaller|Marshaller|TransformerFactory(?:\.newInstance)?\s*\(|SchemaFactory(?:\.newInstance)?\s*\(|parse\s*\(|createXMLStreamReader\s*\(|DocumentBuilder\s*\(|XMLReader\s*\(|SAXParser\s*\(|Transformer\s*\(|transform\s*\(|TransformerFactory\.newTransformer\s*\()\b|\b(?:HttpURLConnection|URL\.openConnection|RestTemplate\.getForObject|RestTemplate\.exchange|OkHttpClient|HttpClient|URLConnection|ApacheHttpClient)\b|\b(?:File\.(?:createNewFile|delete|deleteOnExit|exists|isDirectory|isFile|mkdir|mkdirs|renameTo|listFiles)|Files\.(?:lines|readAllBytes|readString|readAllLines|write|writeString|list|exists|delete|deleteIfExists|copy|move|write|readAll.*|newInputStream)|FileInputStream|FileOutputStream|RandomAccessFile)\b|\b(?:ZipInputStream|ZipOutputStream|ZipFile|ZipEntry|getNextEntry|JarFile|JarEntry)\b|\b(?:io\.jsonwebtoken\.Jwts|JwtParser|JwtBuilder|Algorithm|JWTVerifier|SignedJWT|NimbusJwtDecoder|JwtDecoder)\b|\b(?:response\.sendRedirect|HttpServletResponse\.sendRedirect|RedirectView|ModelAndView\("redirect:)\b|\b(?:@CrossOrigin|CorsFilter|CorsRegistry|CorsConfiguration)\b|\b(?:Thread\.sleep|while\s*\(true\)|for\s*\(;;\)|BigInteger\.pow|Pattern\.compile\(.{100,}\)|Files\.readAllBytes\()\b|\b(?:(?:Pattern\.compile|String\.matches|Matcher\.(?:find|matches|replaceAll))\b.*(?:\+|\*|\{[0-9,]+\})|Pattern\.matches\s*\())
```

## RCE(Os command unjection, Code Injection)

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(Runtime\.getRuntime\(\)\.exec|ProcessBuilder\s*\(|ScriptEngineManager\.getEngineByName|javax\.tools\.JavaCompiler|Method\.invoke|Class\.forName|GroovyShell|NashornScriptEngineFactory|ScriptEngine\.eval|eval\s*\(|defineClass\s*\(|ClassLoader\s*\(|URLClassLoader\s*\(|Context\s*\(|loadClass\s*\(|lookup\s*\(|lookupLink\s*\(|start\s*\(|exec\s*\(|loadLibrary\s*\(|load\s*\(|Runtime\s*\(|System\s*\()\b
```

## File Uploads

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(javax\.servlet\.http\.Part|getInputStream\(\)|MultipartFile|FileItem|DiskFileItemFactory|ServletFileUpload)\b
```

## Sql Injection

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(Statement\.execute(Query|Update)|Connection\.createStatement|PreparedStatement\.execute.*\(|JdbcTemplate\.query|JdbcTemplate\.update|EntityManager\.createQuery|SQLQuery)\b.*(\+|\?|\%s|\$)|^(?![ \t]*//)(?![ \t]*/\*).*?\b(SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|CREATE|TRUNCATE)\b
```

## NoSQL Injection

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(DBCollection\.find|DBCollection\.insert|DBCollection\.update|MongoCollection<.*>\.(find|insertOne|updateOne|deleteOne)|BasicDBObject|Document\(|@Query)\b.*(\$where|\$regex|\$ne|\$gt|\$lt)
```

## Ldap Injection

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(DirContext\.search|InitialDirContext|SearchControls|Attributes|LdapContext)\b.*(\+|\%s|\$)
```

## XPath Injection

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(javax\.xml\.xpath\.XPathFactory|XPathExpression\.compile|DocumentBuilderFactory\.newInstance|TransformerFactory\.newInstance)\b
```

## Insecure deserialization

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(ObjectInputStream\.readObject|XMLDecoder|JSONDeserializer|readObjectOverride|SerializationUtils\.deserialize|readObject\s*\()\b
```

## SSTI

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(JtwigTemplate|PebbleEngine|FreeMarker|VelocityEngine|Thymeleaf|MustacheFactory|GroovyShell|MVEL\.eval)\b
```

## XXE

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(DocumentBuilderFactory(?:\.newInstance)?\s*\(|SAXParserFactory(?:\.newInstance)?\s*\(|XMLInputFactory(?:\.newInstance)?\s*\(|Unmarshaller|Marshaller|TransformerFactory(?:\.newInstance)?\s*\(|SchemaFactory(?:\.newInstance)?\s*\(|parse\s*\(|createXMLStreamReader\s*\(|DocumentBuilder\s*\(|XMLReader\s*\(|SAXParser\s*\(|Transformer\s*\(|transform\s*\(|TransformerFactory\.newTransformer\s*\()\b
```

## SSRF

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(HttpURLConnection|URL\.openConnection|RestTemplate\.getForObject|RestTemplate\.exchange|OkHttpClient|HttpClient|URLConnection|ApacheHttpClient)\b
```

## File/Folder manipulation(read, delete, creation)

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(File\.(createNewFile|delete|deleteOnExit|exists|isDirectory|isFile|mkdir|mkdirs|renameTo|listFiles)|Files\.(lines|readAllBytes|readString|readAllLines|write|writeString|list|exists|delete|deleteIfExists|copy|move|write|readAll.*|newInputStream)|FileInputStream|FileOutputStream|RandomAccessFile)\b
```

## Zip vulns

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(ZipInputStream|ZipOutputStream|ZipFile|ZipEntry|getNextEntry|JarFile|JarEntry)\b
```

## JWT

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(io\.jsonwebtoken\.Jwts|JwtParser|JwtBuilder|Algorithm|JWTVerifier|SignedJWT|NimbusJwtDecoder|JwtDecoder)\b
```

## Open Redirect

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(response\.sendRedirect|HttpServletResponse\.sendRedirect|RedirectView|ModelAndView\("redirect:)\b
```

## Cors

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(@CrossOrigin|CorsFilter|CorsRegistry|CorsConfiguration)\b
```

## Dos

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b(Thread\.sleep|while\s*\(true\)|for\s*\(;;\)|BigInteger\.pow|Pattern\.compile\(.{100,}\)|Files\.readAllBytes\()\b
```

## ReDOS

```
^(?![ \t]*//)(?![ \t]*/\*).*?\b((?:Pattern\.compile|String\.matches|Matcher\.(?:find|matches|replaceAll))\b.*(\+|\*|\{[0-9,]+\})|Pattern\.matches\s*\()
```