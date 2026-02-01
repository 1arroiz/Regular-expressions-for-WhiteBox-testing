# Full Regular Expression without false positives(mostly)

```regex
^(?![ \t]*#).*?(?:\b(?:System\.cmd|:os\.cmd|:erlang\.apply|Code\.eval_(?:string|quoted)|:rpc\.call|:erl_eval|:erlang\.load_nif)\b|\b(?:Plug\.Upload|File\.cp|File\.write|File\.mkdir|File\.rename)\b|\b(?:Ecto\.Adhoc|Ecto\.Query|Ecto\.Repo\.query|Ecto\.Repo\.query!|Ecto\.Repo\.transaction)\b.*(?:\+|#\{|\|)|\b(?:Mongo\.find|Mongo\.insert|Mongo\.update|Mongo\.delete|Mongo\.command|mongodb)\b.*(?:\$where|\$\w+)|\b(?::eldap\.search|:eldap\.simple_bind|:eldap\.open)\b|\b(?::xmerl_xpath|string|:xmerl_xpath:query)\b|\b(?::erlang\.binary_to_term|:erlang\.term_to_binary|:erlang\.apply|:erlang\.list_to_term|:erlang\.binary_to_atom|:erlang\.binary_to_existing_atom)\b|\b(?:EEx\.eval_string|EEx\.compile_string|Phoenix\.Template|Plug\.Template)\b|\b(?::xmerl_scan\.string|:xmerl_scan\.file|SweetXml\.parse)\b|\b(?:HTTPoison\.(?:get|post|request)|:httpc\.request|Finch\.build|Mint\.HTTP|:hackney\.request)\b|\b(?:File\.(?:read|read!|write|write!|rm|rm_rf|cp|rename|mkdir|mkdir_p|stat|ls)|Path\.(?:expand|join|absname))\b|\b(?::zip\.extract|:erl_tar\.extract|:erl_tar\.open)\b|\b(?:Joken\.sign|Joken\.verify|Joken\.token|Guardian\.encode_and_sign|Guardian\.decode_and_verify)\b|\b(?:Plug\.Conn\.redirect|Phoenix\.Controller\.redirect)\b|\b(?:CORSPlug|Corsica|Plug\.Conn\.put_resp_header.*"access-control-allow-origin")\b|\b(?::crypto\.strong_rand_bytes|Enum\.map|Stream\.cycle|Stream\.repeatedly|Process\.sleep|receive\s+after)\b|\b(?:Regex\.run|Regex\.match\?|Regex\.scan|Regex\.replace|Regex\.compile)\b.*(?:\*|\+|\{[0-9,]+\}))
```

## RCE(Os command unjection, Code Injection)

```
^(?![ \t]*#).*\b(System\.cmd|:os\.cmd|:erlang\.apply|Code\.eval_(string|quoted)|:rpc\.call|:erl_eval|:erlang\.load_nif)\b
```

## File Uploads

```
^(?![ \t]*#).*\b(Plug\.Upload|File\.cp|File\.write|File\.mkdir|File\.rename)\b
```

## Sql Injection

```
^(?![ \t]*#).*\b(Ecto\.Adhoc|Ecto\.Query|Ecto\.Repo\.query|Ecto\.Repo\.query!|Ecto\.Repo\.transaction)\b.*(\+|\#\{|\||SELECT|INSERT|UPDATE|DELETE|DROP|ALTER)
```

## NoSQL Injection

```
^(?![ \t]*#).*\b(Mongo\.find|Mongo\.insert|Mongo\.update|Mongo\.delete|Mongo\.command|mongodb)\b.*(\$where|\$\w+)
```

## Ldap Injection

```
^(?![ \t]*#).*\b(:eldap\.search|:eldap\.simple_bind|:eldap\.open)\b
```

## XPath Injection

```
^(?![ \t]*#).*\b(:xmerl_xpath|string|:xmerl_xpath:query)\b
```

## Insecure deserialization

```
^(?![ \t]*#).*\b(:erlang\.binary_to_term|:erlang\.term_to_binary|:erlang\.apply|:erlang\.list_to_term|:erlang\.binary_to_atom|:erlang\.binary_to_existing_atom)\b
```

## SSTI

```
^(?![ \t]*#).*\b(EEx\.eval_string|EEx\.compile_string|Phoenix\.Template|Plug\.Template)\b
```

## XXE

```
^(?![ \t]*#).*\b(:xmerl_scan\.string|:xmerl_scan\.file|SweetXml\.parse)\b
```

## SSRF

```
^(?![ \t]*#).*\b(HTTPoison\.(get|post|request)|:httpc\.request|Finch\.build|Mint\.HTTP|:hackney\.request)\b
```

## File/Folder manipulation(read, delete, creation)

```
^(?![ \t]*#).*\b(File\.(read|read!|write|write!|rm|rm_rf|cp|rename|mkdir|mkdir_p|stat|ls)|Path\.(expand|join|absname))\b
```

## Zip vulns

```
^(?![ \t]*#).*\b(:zip\.extract|:erl_tar\.extract|:erl_tar\.open)\b
```

## JWT

```
^(?![ \t]*#).*\b(Joken\.sign|Joken\.verify|Joken\.token|Guardian\.encode_and_sign|Guardian\.decode_and_verify)\b
```

## Open Redirect

```
^(?![ \t]*#).*\b(Plug\.Conn\.redirect|Phoenix\.Controller\.redirect)\b
```

## Cors

```
^(?![ \t]*#).*\b(CORSPlug|Corsica|Plug\.Conn\.put_resp_header.*"access-control-allow-origin")\b
```

## Dos

```
^(?![ \t]*#).*\b(:crypto\.strong_rand_bytes|Enum\.map|Stream\.cycle|Stream\.repeatedly|Process\.sleep|receive\s+after)\b
```

## ReDOS

```
^(?![ \t]*#).*\b(Regex\.run|Regex\.match\?|Regex\.scan|Regex\.replace|Regex\.compile)\b.*(\*|\+|\{[0-9,]+\})
```