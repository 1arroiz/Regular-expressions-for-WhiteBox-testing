# Full Regular Expression without false positives(mostly)

```regex
^(?![ \t]*#).*?(?:\b(?:system|exec|spawn|popen|IO\.(?:popen|read|readlines|foreach|write|binwrite|binread)|Open3\.(?:popen\d?|capture\d?)|`[^`]*`|%x\([^)]*\)|eval|instance_eval|class_eval|module_eval|open\s*\("|open\s*\('|open\s*\(\s*"\||open\s*\(\s*'\|)\b|\b(?:ActionDispatch::Http::UploadedFile|Rack::Multipart::UploadedFile|params\[:file\]|CarrierWave|Shrine|ActiveStorage)\b|\b(?:ActiveRecord::Base\.connection\.execute|find_by_sql|where|order|pluck|select)\b.*(?:\+|#\{|%|\?)|\b(?:(?:safe_)?constantize|qualified_const_get|const_get|Object\.const_get|Module\.const_get|Kernel\.const_get)\b.*(?:params\[|request\.|cookies\[|session\[|ENV\[|class_name|method_name)|\b(?:send|public_send|__send__)\b.*(?:params\[|request\.|cookies\[|session\[|ENV\[|method_name)|\b(?:Mongoid\..*|collection\.(?:find|aggregate|update|delete))\b.*(?:\$where|\$\w+)|\b(?:Net::LDAP\.new|Net::LDAP::Entry|Net::LDAP::Filter)\b|\b(?:REXML::Document|Nokogiri::XML|XPath)\b.*(?:search|at_xpath|xpath)\b|\b(?:Marshal\.load|YAML\.load|Psych\.load|Oj\.load|JSON\.load)\b|\b(?:ERB\.new|ERB#result|Liquid::Template\.parse|Mustache\.render|Tilt::Template\.new)\b|\b(?:REXML::Document\.new|Nokogiri::XML|Ox\.parse)\b|\b(?:Net::HTTP\.start|Net::HTTP\.get|Net::HTTP\.post|Net::HTTP\.get_response|URI\.open|OpenURI\.open_uri|RestClient\.(?:get|post|put|delete)|Faraday\.(?:get|post|put|delete))\b|\b(?:File\.(?:read|write|delete|open|chmod|chown|rename|unlink|expand_path|syswrite)|Dir\.(?:mkdir|rmdir|delete|entries|foreach)|IO\.(?:read|write|binread|binwrite|syswrite|gets|getс|popen|pread|readline|readlines|foreach))\b|\b(?:Zip::File\.open|Zlib::GzipReader\.open|Zlib::GzipWriter\.open|Archive::Tar::Minitar)\b|\b(?:JWT\.encode|JWT\.decode|JsonWebToken|Knock::AuthToken)\b|\b(?:redirect_to|redirect_back|redirect_to:|response\.redirect)\b|\b(?:rack-cors|Access-Control-Allow-Origin|Rails\.application\.config\.middleware\.use\s+Rack::Cors)\b|\b(?:loop\s+do|while\s+true|sleep|Thread\.new\s+do|fork|Process\.spawn)\b|\b(?:Regexp\.new\([^)]*(?:\+|\*|\{[0-9,]+\})[^)]*\)|string\s*=~\s*\/(.+)(?:\+|\*|\{[0-9,]+\})\/))
```

## RCE(Os command unjection, Code Injection)

```
\b(system|exec|spawn|popen|IO\.(popen|read|readlines|foreach|write|binwrite|binread)|Open3\.(popen\d?|capture\d?)|`[^`]*`|%x\([^)]*\)|eval|instance_eval|class_eval|module_eval|open\s*\("|open\s*\('|open\s*\(\s*"\||open\s*\(\s*'\|)\b
```

## File Uploads

```
\b(ActionDispatch::Http::UploadedFile|Rack::Multipart::UploadedFile|params\[:file\]|CarrierWave|Shrine|ActiveStorage)\b
```

## Sql Injection

```
\b(ActiveRecord::Base\.connection\.execute|find_by_sql|where|order|pluck|select)\b.*(\+|#{|%|\?)|\b(SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|CREATE|TRUNCATE)\b
```

## NoSQL Injection

```
\b(Mongoid\..*|collection\.(find|aggregate|update|delete))\b.*(\$where|\$\w+)
```

## Ldap Injection

```
\b(Net::LDAP\.new|Net::LDAP::Entry|Net::LDAP::Filter)\b
```

## XPath Injection

```
\b(REXML::Document|Nokogiri::XML|XPath)\b.*(search|at_xpath|xpath)\b
```

## Insecure deserialization

```
\b(Marshal\.load|YAML\.load|Psych\.load|Oj\.load|JSON\.load)\b
```

## Unsafe reflection

```
\b(?:(?:safe_)?constantize|qualified_const_get|const_get|Object\.const_get|Module\.const_get|Kernel\.const_get)\b.*(?:params\[|request\.|cookies\[|session\[|ENV\[|class_name|method_name)|\b(?:send|public_send|__send__)\b.*(?:params\[|request\.|cookies\[|session\[|ENV\[|method_name)
```

## SSTI

```
\b(ERB\.new|ERB#result|Liquid::Template\.parse|Mustache\.render|Tilt::Template\.new)\b
```

## XXE

```
\b(REXML::Document\.new|Nokogiri::XML|Ox\.parse)\b
```

## SSRF

```
\b(Net::HTTP\.start|Net::HTTP\.get|Net::HTTP\.post|Net::HTTP\.get_response|URI\.open|OpenURI\.open_uri|RestClient\.(get|post|put|delete)|Faraday\.(get|post|put|delete))\b
```

## File/Folder manipulation(read, delete, creation)

```
\b(File\.(read|write|delete|open|chmod|chown|rename|unlink|expand_path|syswrite)|Dir\.(mkdir|rmdir|delete|entries|foreach)|IO\.(read|write|binread|binwrite|syswrite|gets|getс|popen|pread|readline|readlines|foreach))\b
```

## Zip vulns

```
\b(Zip::File\.open|Zlib::GzipReader\.open|Zlib::GzipWriter\.open|Archive::Tar::Minitar)\b
```

## JWT

```
\b(JWT\.encode|JWT\.decode|JsonWebToken|Knock::AuthToken)\b
```

## Open Redirect

```
\b(redirect_to|redirect_back|redirect_to:|response\.redirect)\b
```

## Cors

```
\b(rack-cors|Access-Control-Allow-Origin|Rails\.application\.config\.middleware\.use\s+Rack::Cors)\b
```

## Dos

```
\b(loop\s+do|while\s+true|sleep|Thread\.new\s+do|fork|Process\.spawn)\b
```

## ReDOS

```
\bRegexp\.new\([^)]*(\+|\*|\{[0-9,}])[^)]*\)|string\s*=~\s*/(.+)(\+|\*|\{[0-9,}])/
```