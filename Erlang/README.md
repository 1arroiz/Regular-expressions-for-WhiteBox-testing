# Full Regular Expression without false positives(mostly)

```regex
^(?![ \t]*%).*?(?:\b(?:os:cmd|open_port|erlang:apply|rpc:call|erl_eval:exprs|c:cd|c:c|c:ls|c:nl|c:q)\b|\b(?:file:write_file|file:open|file:copy|filelib:ensure_dir)\b|\b(?:epgsql:squery|odbc:sql_query|emysql:execute)\b.*(?:\+|"\s*\|)|\b(?:mongodb:find|mongodb:update|mongodb:delete|mongo:do|couchbeam:open_db|couchbeam:save_doc)\b.*(?:\$where|\$\w+)|\b(?:eldap:search|eldap:simple_bind|eldap:open)\b.*(?:\+|"\s*\|)|\b(?:xmerl_xpath:string|xmerl_xpath:query|xmerl_scan:string)\b.*(?:\+|"\s*\|)|\b(?:binary_to_term)\b|\b(?:erlydtl:render|mustache:render|bbmustache:render)\b|\b(?:xmerl_scan:file|xmerl_scan:string|erlsom:parse)\b|\b(?:httpc:request|ibrowse:send_req|hackney:request|lhttpc:request|gun:request)\b|\b(?:file:(?:open|read_file|write_file|delete|rename|make_dir|make_link|list_dir|read_link|change_time))\b|\b(?:zip:extract|erl_tar:extract|erl_tar:open)\b|\b(?:jose_jwt:sign|jose_jwt:verify|jose_jwt:decode)\b|\b(?:cowboy_req:reply|cowboy_req:set_resp_header)\b.*(?:Location)|\b(?:cowboy_req:set_resp_header)\b.*(?:Access-Control-Allow-Origin)|\b(?:lists:seq|lists:duplicate|timer:sleep|receive\s+after|spawn_link|spawn_opt)\b|\b(?:re:run|re:compile)\b.*(?:\+|(\.\*){2,}|(\\d\+){2,}))
```

## RCE(Os command unjection, Code Injection)

```
^(?![ \t]*%).*\b(os:cmd|open_port|erlang:apply|rpc:call|erl_eval:exprs|c:cd|c:c|c:ls|c:nl|c:q)\b
```

## File Uploads

```
^(?![ \t]*%).*\b(file:write_file|file:open|file:copy|filelib:ensure_dir)\b
```

## Sql Injection

```
^(?![ \t]*%).*\b(epgsql:squery|odbc:sql_query|emysql:execute)\b.*(\+|"\s*\||SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|TRUNCATE)
```

## NoSQL Injection

```
^(?![ \t]*%).*\b(mongodb:find|mongodb:update|mongodb:delete|mongo:do|couchbeam:open_db|couchbeam:save_doc)\b.*(\$where|\$\w+)
```

## Ldap Injection

```
^(?![ \t]*%).*\b(eldap:search|eldap:simple_bind|eldap:open)\b.*(\+|"\s*\|)
```

## XPath Injection

```
^(?![ \t]*%).*\b(xmerl_xpath:string|xmerl_xpath:query|xmerl_scan:string)\b.*(\+|"\s*\|)
```

## Insecure deserialization

```
^(?![ \t]*%).*\b(binary_to_term)\b
```

## SSTI

```
^(?![ \t]*%).*\b(erlydtl:render|mustache:render|bbmustache:render)\b
```

## XXE

```
^(?![ \t]*%).*\b(xmerl_scan:file|xmerl_scan:string|erlsom:parse)\b
```

## SSRF

```
^(?![ \t]*%).*\b(httpc:request|ibrowse:send_req|hackney:request|lhttpc:request|gun:request)\b
```

## File/Folder manipulation(read, delete, creation)

```
^(?![ \t]*%).*\b(file:(open|read_file|write_file|delete|rename|make_dir|make_link|list_dir|read_link|change_time))\b
```

## Zip vulns

```
^(?![ \t]*%).*\b(zip:extract|erl_tar:extract|erl_tar:open)\b
```

## JWT

```
^(?![ \t]*%).*\b(jose_jwt:sign|jose_jwt:verify|jose_jwt:decode)\b
```

## Open Redirect

```
^(?![ \t]*%).*\b(cowboy_req:reply|cowboy_req:set_resp_header)\b.*(Location)
```

## Cors

```
^(?![ \t]*%).*\b(cowboy_req:set_resp_header)\b.*(Access-Control-Allow-Origin)
```

## Dos

```
^(?![ \t]*%).*\b(lists:seq|lists:duplicate|timer:sleep|receive\s+after|spawn_link|spawn_opt)\b
```

## ReDOS

```
^(?![ \t]*%).*\b(re:run|re:compile)\b.*(\+|(\.\*){2,}|(\\d\+){2,})
```