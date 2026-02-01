# Full Regular Expression

```regex
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?(?:\b(?:child_process\.(?:exec|execSync|spawn|spawnSync)|vm\.(?:runInNewContext|runInThisContext)|eval|Function\(|setImmediate\(|setTimeout\(|setInterval\()\b|\b(?:multer|formidable|busboy|fs\.createWriteStream|req\.files|req\.file)\b|\b(?:mysql|mysql2|pg|sequelize|knex|db\.query|connection\.query)\b.*(?:\+|\$)|\b(?:db\.collection\(|mongoose\..*find|updateOne|updateMany|remove|deleteOne|aggregate)\b.*(?:\$where|\$regex|\$function|\$expr)|\b(?:ldapjs|activedirectory|client\.search\()\b|\b(?:xpath|xmldom|xpath\.evaluate|select1?)\b|\b(?:serialijse|node-serialize|deserialize|JSON\.parse\()\b|\b(?:ejs|pug|handlebars|mustache|nunjucks|twig|_\.template|res\.render)\b|\b(?:xml2js|xmldom|sax|libxmljs|new DOMParser|xmlbuilder)\b|\b(?:request\(|axios\.(?:get|post)|node-fetch|got|http\.request|https\.request|superagent|needle|urllib)\b|\b(?:fs\.(?:readFile|readFileSync|writeFile|writeFileSync|unlink|unlinkSync|rename|renameSync|mkdir|mkdirSync|rmdir|rmdirSync|copyFile|copyFileSync)|path\.(?:join|resolve|basename|dirname))\b|\b(?:adm-zip|unzipper|yauzl|tar|extract-zip)\b|\b(?:jsonwebtoken|jwt-simple|jose|jwt\.verify|jwt\.decode)\b|\b(?:Object\.assign|Object\.defineProperty|Object\.setPrototypeOf|_\.(?:merge|defaultsDeep)|deepExtend|Hoek\.merge)\b|\b(?:res\.redirect\(|window\.location|document\.location)\b|\b(?:cors|res\.setHeader\(["']Access-Control-Allow-Origin["']\))\b|\b(?:while\s*\(true\)|for\s*\(;;\)|crypto\.pbkdf2Sync|bcrypt\.hashSync|scryptSync|zlib\.inflateSync|JSON\.stringify\(.*(?:BigInt|circular))\b|\b(?:new RegExp|RegExp\(|String\.match|String\.replace|str\.split)\b.*(?:\+|\*|\{[0-9,]+\}))
```

## RCE(Os command unjection, Code Injection)

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(child_process\.(exec|execSync|spawn|spawnSync)|vm\.(runInNewContext|runInThisContext)|eval|Function\(|setImmediate\(|setTimeout\(|setInterval\()\b
```

## File Uploads

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(multer|formidable|busboy|fs\.createWriteStream|req\.files|req\.file)\b
```

## Sql Injection

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(mysql|mysql2|pg|sequelize|knex|db\.query|connection\.query)\b.*(\+|\$|SELECT|INSERT|UPDATE|DELETE|DROP|ALTER)
```

## NoSQL Injection

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(db\.collection\(|mongoose\..*find|updateOne|updateMany|remove|deleteOne|aggregate)\b.*(\$where|\$regex|\$function|\$expr)
```

## Ldap Injection

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(ldapjs|activedirectory|client\.search\()\b
```

## XPath Injection

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(xpath|xmldom|xpath\.evaluate|select1?)\b
```

## Insecure deserialization

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(serialijse|node-serialize|deserialize|JSON\.parse\()\b
```

## SSTI

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(ejs|pug|handlebars|mustache|nunjucks|twig|_.template|res\.render)\b
```

## XXE

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(xml2js|xmldom|sax|libxmljs|new DOMParser|xmlbuilder)\b
```

## SSRF

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(request\(|axios\.(get|post)|node-fetch|got|http\.request|https\.request|superagent|needle|urllib)\b
```

## File/Folder manipulation(read, delete, creation)

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(fs\.(readFile|readFileSync|writeFile|writeFileSync|unlink|unlinkSync|rename|renameSync|mkdir|mkdirSync|rmdir|rmdirSync|copyFile|copyFileSync)|path\.(join|resolve|basename|dirname))\b
```

## Zip vulns

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(adm-zip|unzipper|yauzl|tar|extract-zip)\b
```

## JWT

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(jsonwebtoken|jwt-simple|jose|jwt\.verify|jwt\.decode)\b
```

## Prototype Pollution

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(Object\.assign|Object\.defineProperty|Object\.setPrototypeOf|_\.(merge|defaultsDeep)|deepExtend|Hoek\.merge)\b
```

## Open Redirect

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(res\.redirect\(|window\.location|document\.location)\b
```

## Cors

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(cors|res\.setHeader\(["']Access-Control-Allow-Origin["'])\b
```

## Dos

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(while\s*\(true\)|for\s*\(;;\)|crypto\.pbkdf2Sync|bcrypt\.hashSync|scryptSync|zlib\.inflateSync|JSON\.stringify\(.*(BigInt|circular))\b
```

## ReDOS

```
^(?![ \t]*\/\/)(?![ \t]*\/\*).*?\b(new RegExp|RegExp\(|String\.match|String\.replace|str\.split)\b.*(\+|\*|\{[0-9,}]+)
```