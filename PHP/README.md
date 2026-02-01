# Full Regular Expression

```regex
^(?![ \t]*(#|//)).*?(?:\b(?:shell_exec|exec|system|passthru|popen|proc_open|pcntl_exec|eval|assert|create_function|preg_replace|ReflectionMethod|include|include_once|require|require_once)\b|\b(?:\$_FILES|\$_POST\['file'\]|move_uploaded_file|is_uploaded_file)\b|\b(?:include|include_once|require|require_once)\s*\(?.*(?:\$_(?:GET|POST|REQUEST|COOKIE)|GLOBALS)\b|\b(?:mysql_query|mysqli_query|mysqli::query|pg_query|odbc_exec|db_query|PDO->query|PDO->exec|PDO->prepare|->query)\b.*(?:\$_(?:GET|POST|REQUEST|COOKIE)|".*\$.*")|\b(?:\$collection->(?:find|findOne|update|remove|aggregate)|MongoClient|MongoDB\\BSON\\toJSON)\b.*(?:\$_(?:GET|POST|REQUEST|COOKIE)|\$.+)|\b(?:ldap_search|ldap_list|ldap_read|ldap_bind)\b.*(?:\$_(?:GET|POST|REQUEST|COOKIE)|\$.+)|\b(?:DOMXPath->query|DOMXPath->evaluate|SimpleXMLElement->xpath)\b.*(?:\$_(?:GET|POST|REQUEST|COOKIE)|\$.+)|\b(?:unserialize|igbinary_unserialize|yaml_parse|msgpack_unpack|simplexml_load_file|simplexml_load_string|DOMDocument->load(?:XML|HTML)?|XMLReader::open|copy|dir|exif_imagetype|exif_read_data|exif_thumbnail|file|file_exists|file_get_contents|fileatime|filectime|filegroup|fileinode|filemtime|fileowner|fileperms|filesize|filetype|fopen|get_meta_tags|getimagesize|gzfile|gzopen|highlight_file|imagecreatefrom(?:bmp|gd2?|gif|jpeg|png|tga|wbmp|webp|xbm|xpm)|imageloadfont|is_(?:dir|executable|file|link|readable|writable|writeable)|lstat|md5_file|mime_content_type|opendir|parse_ini_file|php_strip_whitespace|read_exif_data|readfile|readgzfile|scandir|sha1_file|show_source|stat|touch|unlink)\b|\b(?:preg_replace\s*\(.*e.*\)|Smarty->fetch|Twig->render|Blade::compileString)\b|\b(?:simplexml_load_string|simplexml_load_file|DOMDocument->load(?:XML|HTML)?|DOMDocument->loadXML|XMLReader::open|SimpleXMLElement)\b|\b(?:file_get_contents|fopen|curl_exec|curl_multi_exec|curl_setopt|stream_socket_client|fsockopen)\b.*(?:http|https|ftp)\b|\b(?:fopen|fread|fwrite|file_get_contents|file_put_contents|unlink|rename|copy|move_uploaded_file|move_upload_file|mkdir|rmdir|scandir|opendir|readdir|closedir|chmod|chown|fclose|file_exists|is_file|md5_file|include|include_once|require|require_once)\b|\b(?:ZipArchive->extractTo|Phar::(?:load|open)|phar://)\b|\b(?:Firebase\\JWT\\JWT::encode|Firebase\\JWT\\JWT::decode|Lcobucci\\JWT|Namshi\\JOSE)\b|\b(?:header\((?:['"])(?:Location|location|Refresh|refresh):.*\$_(?:GET|POST|REQUEST|COOKIE))\b|\b(?:header\("Access-Control-Allow-Origin:.*"\)|header\("Access-Control-Allow-Credentials:.*"\))\b|\b(?:while\s*\(true\)|for\s*\(;;\)|sleep\(|usleep\(|set_time_limit\(|preg_match\(.+\+.+\)|str_repeat\()\b|\b(?:preg_match|preg_replace|preg_grep|preg_split)\b.*(?:\(\.\*\)\+|\(\.\*\)\*|\(\.\+\)\+|\(\.\+\)\*))
```

## RCE(Os command unjection, Code Injection)

```
\b(shell_exec|exec|system|passthru|popen|proc_open|pcntl_exec|eval|assert|create_function|preg_replace|ReflectionMethod|include|include_once|require|require_once|`[^`]*`)\b
```

## File Uploads

```
\b(\$_FILES|\$_POST\['file'\]|move_uploaded_file|is_uploaded_file)\b
```

## File Inclusion

```
\b(include|include_once|require|require_once)\s*\(?.*(\$_(GET|POST|REQUEST|COOKIE)|GLOBALS)\b
```

## Sql Injection

```
\b(mysql_query|mysqli_query|mysqli::query|pg_query|odbc_exec|db_query|PDO->query|PDO->exec|PDO->prepare|->query)\b.*(\$_(GET|POST|REQUEST|COOKIE)|".*\$.*")|\b(SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|TRUNCATE|CREATE)\b
```

## NoSQL Injection

```
\b(\$collection->(find|findOne|update|remove|aggregate)|MongoClient|MongoDB\\BSON\\toJSON)\b.*(\$_(GET|POST|REQUEST|COOKIE)|\$.+)
```

## Ldap Injection

```
\b(ldap_search|ldap_list|ldap_read|ldap_bind)\b.*(\$_(GET|POST|REQUEST|COOKIE)|\$.+)
```

## XPath Injection

```
\b(DOMXPath->query|DOMXPath->evaluate|SimpleXMLElement->xpath)\b.*(\$_(GET|POST|REQUEST|COOKIE)|\$.+)
```

## Insecure deserialization

```
\b(unserialize|igbinary_unserialize|yaml_parse|msgpack_unpack|simplexml_load_file|simplexml_load_string|DOMDocument->load(XML|HTML)?|XMLReader::open|copy|dir|exif_imagetype|exif_read_data|exif_thumbnail|file|file_exists|file_get_contents|fileatime|filectime|filegroup|fileinode|filemtime|fileowner|fileperms|filesize|filetype|fopen|get_meta_tags|getimagesize|gzfile|gzopen|highlight_file|imagecreatefrom(bmp|gd2?|gif|jpeg|png|tga|wbmp|webp|xbm|xpm)|imageloadfont|is_(dir|executable|file|link|readable|writable|writeable)|lstat|md5_file|mime_content_type|opendir|parse_ini_file|php_strip_whitespace|read_exif_data|readfile|readgzfile|scandir|sha1_file|show_source|stat|touch|unlink)\b
```

## SSTI

```
\b(preg_replace\s*\(.*e.*\)|Smarty->fetch|Twig->render|Blade::compileString)\b
```

## XXE

```
\b(simplexml_load_string|simplexml_load_file|DOMDocument->load(XML|HTML)?|DOMDocument->loadXML|XMLReader::open|SimpleXMLElement)\b
```

## SSRF

```
\b(file_get_contents|fopen|curl_exec|curl_multi_exec|curl_setopt|stream_socket_client|fsockopen)\b.*(http|https|ftp)\b
```

## File/Folder manipulation(read, delete, creation)

```
\b(fopen|fread|fwrite|file_get_contents|file_put_contents|unlink|rename|copy|move_uploaded_file|move_upload_file|mkdir|rmdir|scandir|opendir|readdir|closedir|chmod|chown|fclose|file_exists|is_file|md5_file|include|include_once|require|require_once)\b
```

## Zip vulns

```
\b(ZipArchive->extractTo|Phar::(load|open)|phar://)\b
```

## JWT

```
\b(Firebase\\JWT\\JWT::encode|Firebase\\JWT\\JWT::decode|Lcobucci\\JWT|Namshi\\JOSE)\b
```

## Open Redirect

```
\b(header\((['"])(Location|location|Refresh|refresh):.*\$_(GET|POST|REQUEST|COOKIE))\b
```

## Cors

```
\b(header\("Access-Control-Allow-Origin:.*"\)|header\("Access-Control-Allow-Credentials:.*"\))\b
```

## Dos

```
\b(while\s*\(true\)|for\s*\(;;\)|sleep\(|usleep\(|set_time_limit\(|preg_match\(.+\+.+\)|str_repeat\()\b
```

## ReDOS

```
\b(preg_match|preg_replace|preg_grep|preg_split)\b.*(\(\.\*\)\+|\(\.\*\)\*|\(\.\+\)\+|\(\.\+\)\*)
```