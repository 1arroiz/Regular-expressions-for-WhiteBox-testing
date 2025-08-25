# Full Regular Expression

```regex
^(?![ \t]*#).*(prepare\s*\(|prepare\s+|selectall_arrayref\s*\(|selectall_arrayref\s+|selectrow_array\s*\(|selectrow_array\s+|execute\s*\(|execute\s+|sprintf\s*\(|sprintf\s+|open\s*\(|open\s+|close\s*\(|close\s+|read\s*\(|read\s+|sysread\s*\(|sysread\s+|write\s*\(|write\s+|syswrite\s*\(|syswrite\s+|print\s*\(|print\s+|unlink\s*\(|unlink\s+|rename\s*\(|rename\s+|copy\s*\(|copy\s+|move\s*\(|move\s+|chmod\s*\(|chmod\s+|chown\s*\(|chown\s+|mkdir\s*\(|mkdir\s+|rmdir\s*\(|rmdir\s+|opendir\s*\(|opendir\s+|readdir\s*\(|readdir\s+|closedir\s*\(|closedir\s+|stat\s*\(|stat\s+|lstat\s*\(|lstat\s+|utime\s*\(|utime\s+|truncate\s*\(|truncate\s+|binmode\s*\(|binmode\s+|seek\s*\(|seek\s+|tell\s*\(|tell\s+|mkpath\s*\(|mkpath\s+|make_path\s*\(|make_path\s+|remove_tree\s*\(|remove_tree\s+|rmtree\s*\(|rmtree\s+|system\s*\(|system\s+|exec\s*\(|exec\s+|`.*`|qx\/|eval\s*\(|eval\s+|require\s+|require\s*\(|do\s*\(|do\s+|kill\s*\(|kill\s+|fork\s*\(|fork\s+|LWP::UserAgent|HTTP::Tiny|IO::Socket::INET|Net::HTTP|Net::HTTPS|AnyEvent::HTTP|WWW::Mechanize|XML::Parser|XML::LibXML|XML::Simple::XMLin|XML::Twig|XML::SAX::ParserFactory|MongoDB::Collection->find|MongoDB::Collection->find_one|MongoDB::Collection->insert_one|MongoDB::Collection->update_one|MongoDB::Collection->remove|MongoDB::Database->run_command|MongoDB::|Storable::thaw|Storable::retrieve|FreezeThaw::thaw|Data::Dumper::eval|Data::Serializer::deserialize|Sereal::Decoder->decode|deserialize\s*\(|deserialize\s+|serialize\s*\(|serialize\s+|evalq\s*\(|evalq\s+|Template->process|Text::Template->fill_in|Text::MicroTemplate->render|HTML::Template->param|Archive::Zip|Archive::Tar|IO::Uncompress::Unzip|CGI::upload|HTTP::Body|Plack::Request->upload|Mojo::Upload|use\s+|use\s*\(|load\s+|load\s*\(|include|Net::LDAP->search|Net::LDAP->bind|Net::LDAP::LDIF|XML::XPath|XML::LibXML::XPathContext|XML::XPath::NodeSet|Crypt::JWT|JSON::WebToken|Mojo::JWT|Authen::JWT|redirect\s*\(|redirect_to\s*\(|\$q->redirect|\$c->res->redirect|Access-Control-Allow-Origin|Access-Control-Allow-Credentials|while\s*\(.*\)\s*{.*}|for\s*\(.*\)\s*{.*}|sleep\s*\(|alarm\s*\(|threads::create|\(\.\*\)\+|\(\.\*\)\*|\[[^\]]+\]\+|\[[^\]]+\]\*|\(\.\+\)\+|\(\.\+\)\*|\b(?:SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|CREATE|UNION|INTO|FROM|WHERE|ORDER|GROUP|HAVING|LIMIT)\b)
```

## RCE(Os command unjection, Code Injection)

```
open\(|open |system\(|system |exec\(|exec |`.*`|qx\/|eval\(|eval |require |require\(|do\(|do |kill\(|kill |fork\(|fork
```

## File Uploads

```
CGI::upload|HTTP::Body|Plack::Request->upload|Mojo::Upload
```

## File Inclusion

```
require |require\(|do\(|use |use\(|load |load\(|include
```

## Sql Injection

```
/(?:prepare\s*\(|selectall_arrayref\s*\(|selectrow_array\s*\(|execute\s*\(|sprintf\s*\(|do\s*\(|\b(?:SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|CREATE|UNION|INTO|FROM|WHERE|ORDER|GROUP|HAVING|LIMIT)\b)/i
```

## NoSQL Injection

```
MongoDB::Collection->find|MongoDB::Collection->find_one|MongoDB::Collection->insert_one|MongoDB::Collection->update_one|MongoDB::Collection->remove|MongoDB::Database->run_command|MongoDB::
```

## Ldap Injection

```
Net::LDAP->search|Net::LDAP->bind|Net::LDAP::LDIF
```

## XPath Injection

```
XML::XPath|XML::LibXML::XPathContext|XML::XPath::NodeSet
```

## Insecure deserialization

```
Storable::thaw|Storable::retrieve|FreezeThaw::thaw|Data::Dumper::eval|Data::Serializer::deserialize|Sereal::Decoder->decode|deserialize\(|deserialize |serialize\(|serialize
```


## SSTI

```
evalq\(|evalq |Template->process|Text::Template->fill_in|Text::MicroTemplate->render|HTML::Template->param
```


## XXE

```
XML::Parser|XML::LibXML|XML::Simple::XMLin|XML::Twig|XML::SAX::ParserFactory
```


## SSRF

```
LWP::UserAgent|HTTP::Tiny|IO::Socket::INET|Net::HTTP|Net::HTTPS|AnyEvent::HTTP|WWW::Mechanize
```

## File/Folder manipulation(read, delete, creation)

```
open\(|open |close\(|close |read\(|read |sysread\(|sysread |write\(|write |syswrite\(|syswrite |print\(|print |unlink\(|unlink |rename\(|rename |copy\(|copy |move\(|move |chmod\(|chmod |chown\(|chown |mkdir\(|mkdir |rmdir\(|rmdir |opendir\(|opendir |readdir\(|readdir |closedir\(|closedir |stat\(|stat |lstat\(|lstat |utime\(|utime |truncate\(|truncate |binmode\(|binmode |seek\(|seek |tell\(|tell |mkpath\(|mkpath |make_path\(|make_path |remove_tree\(|remove_tree |rmtree\(|rmtree
```

## Zip vulns

```
Archive::Zip|Archive::Tar|IO::Uncompress::Unzip
```

## JWT

```
Crypt::JWT|JSON::WebToken|Mojo::JWT|Authen::JWT
```

## Open Redirect

```
redirect\(|redirect_to\(|$q->redirect|$c->res->redirect
```

## Cors

```
Access-Control-Allow-Origin|Access-Control-Allow-Credentials
```

## Dos

```
while\s*\(.*\)\s*{.*}|for\s*\(.*\)\s*{.*}|sleep\(|alarm\(|fork\(|threads::create
```

## ReDOS

```
\(\.\*\)\+|\(\.\*\)\*|\[[^\]]+\]\+|\[[^\]]+\]\*|\(\.\+\)\+|\(\.\+\)\*
```