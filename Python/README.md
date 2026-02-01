# Full Regular Expression

```regex
^(?![ \t]*#).*?(?:\b(?:os\.(?:system|popen|spawn[a-z]*|exec[a-z]*)|subprocess\.(?:call|Popen|run|check_output)|commands\.getoutput|eval|exec|compile|execfile|input|pickle\.load(?:s)?|marshal\.load(?:s)?)\b|\b(?:request\.files|cgi\.FieldStorage|django\.core\.files|flask\.request\.files|werkzeug\.datastructures\.FileStorage)\b|\b(?:cursor\.(?:execute|executemany|executescript))\b.*(?:\+|%s|%d|\{)|\b(?:collection\.(?:find|find_one|update|delete|aggregate)|pymongo\..*|mongoengine\..*)\b.*(?:\$where|\$\w+)|\b(?:ldap3\.Connection|ldap\.initialize|SimpleLDAPObject\.search)\b.*(?:filter|search)\b|\b(?:lxml\.etree\.XPath|xml\.etree\.ElementTree\.XPath)\b|\b(?:pickle\.load(?:s)?|marshal\.load(?:s)?|yaml\.load|shelve\.open)\b|\b(?:jinja2\.Template|django\.template|mako\.template|tornado\.template)\b|\b(?:xml|lxml|etree|xml\.etree|xml\.sax|xml\.dom|minidom)\.(?:parse|fromstring|XMLParser)\b|\b(?:requests\.(?:get|post|put|delete|request)|urllib\.request\.urlopen|http\.client\.HTTPConnection|httpx\.(?:get|post|request)|aiohttp\.ClientSession\(\)?\.(?:get|post|request)|socket\.socket\.connect)\b|\b(?:open|os\.(?:open|read|write|remove|unlink|rename|renames|replace|rmdir|removedirs|mkdir|makedirs|chmod|link)|shutil\.(?:rmtree|move|copyfile|copy|copy2|copytree|copyfileobj|make_archive|unpack_archive)|zipfile\.(?:ZipFile|is_zipfile)|pathlib\.Path\.(?:unlink|write_text|read_text|mkdir|rmdir|rename))\b|\b(?:zipfile\.ZipFile\(\S*\)\.extract(?:all)?|tarfile\.TarFile\(\S*\)\.extract(?:all)?)\b|\b(?:jwt\.encode|jwt\.decode|PyJWT|authlib\.jose|flask_jwt_extended|djangorestframework_jwt)\b|\b(?:flask\.redirect|django\.shortcuts\.redirect|starlette\.responses\.RedirectResponse)\b|\b(?:Access-Control-Allow-Origin|flask_cors\.CORS|django-cors-headers|FastAPI\.add_middleware\(CORSMiddleware\))\b|\b(?:time\.sleep|asyncio\.sleep|while\s+True:|for\s*\(;;\)|subprocess\.call\(['"]yes['"]\)|multiprocessing\.Process)\b|\bre\.(?:match|search|findall|sub|compile)\b.*(?:\+|\*|\{[0-9,]+\}))
```

## RCE(Os command unjection, Code Injection)

```
\b(os\.(system|popen|spawn[a-z]*|exec[a-z]*)|subprocess\.(call|Popen|run|check_output)|commands\.getoutput|eval|exec|compile|execfile|input|pickle\.load(s)?|marshal\.load(s)?)\b
```

## File Uploads

```
\b(request\.files|cgi\.FieldStorage|django\.core\.files|flask\.request\.files|werkzeug\.datastructures\.FileStorage)\b
```

## Sql Injection

```
\b(cursor\.(execute|executemany|executescript))\b.*(\+|\%s|\%d|\{)|\b(SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|CREATE|TRUNCATE)\b
```

## NoSQL Injection

```
\b(collection\.(find|find_one|update|delete|aggregate)|pymongo\..*|mongoengine\..*)\b.*(\$where|\$\w+)
```

## Ldap Injection

```
\b(ldap3\.Connection|ldap\.initialize|SimpleLDAPObject\.search)\b.*(filter|search)\b
```

## XPath Injection

```
\b(lxml\.etree\.XPath|xml\.etree\.ElementTree\.XPath)\b
```

## Insecure deserialization

```
\b(pickle\.load(s)?|marshal\.load(s)?|yaml\.load|shelve\.open)\b
```

## SSTI

```
\b(jinja2\.Template|django\.template|mako\.template|tornado\.template)\b
```

## XXE

```
\b(xml|lxml|etree|xml\.etree|xml\.sax|xml\.dom|minidom)\.(parse|fromstring|XMLParser)\b
```

## SSRF

```
\b(requests\.(get|post|put|delete|request)|urllib\.request\.urlopen|http\.client\.HTTPConnection|httpx\.(get|post|request)|aiohttp\.ClientSession\(\)?\.(get|post|request)|socket\.socket\.connect)\b
```

## File/Folder manipulation(read, delete, creation)

```
\b(open|os\.(open|read|write|remove|unlink|rename|renames|replace|rmdir|removedirs|mkdir|makedirs|chmod|link)|shutil\.(rmtree|move|copyfile|copy|copy2|copytree|copyfileobj|make_archive|unpack_archive)|zipfile\.(ZipFile|is_zipfile)|pathlib\.Path\.(unlink|write_text|read_text|mkdir|rmdir|rename))\b
```

## Zip vulns

```
\b(zipfile\.ZipFile\(\S*\)\.extract(all)?|tarfile\.TarFile\(\S*\)\.extract(all)?)\b
```

## JWT

```
\b(jwt\.encode|jwt\.decode|PyJWT|authlib\.jose|flask_jwt_extended|djangorestframework_jwt)\b
```

## Open Redirect

```
\b(flask\.redirect|django\.shortcuts\.redirect|starlette\.responses\.RedirectResponse)\b
```

## Cors

```
\b(Access-Control-Allow-Origin|flask_cors\.CORS|django-cors-headers|FastAPI\.add_middleware\(CORSMiddleware)\b
```

## Dos

```
\b(time\.sleep|asyncio\.sleep|while\s+True:|for\s*\(;;\)|subprocess\.call\(['"]yes['"]\)|multiprocessing\.Process)\b
```

## ReDOS

```
\bre\.(match|search|findall|sub|compile)\b.*(\+|\*|\{[0-9,}])
```