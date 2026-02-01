# Full Regular Expression without false positives(mostly)

```regex
^(?![ \t]*#).*?(?:open\(|open |system\(|system |exec\(|exec |`.*`|qx\/|eval\(|eval |require |require\(|do\(|do |kill\(|kill |fork\(|fork|CGI::upload|HTTP::Body|Plack::Request->upload|Mojo::Upload|use |use\(|load |load\(|include|(?:prepare\s*\(|selectall_arrayref\s*\(|selectrow_array\s*\(|execute\s*\(|sprintf\s*\(|do\s*\()|MongoDB::Collection->find|MongoDB::Collection->find_one|MongoDB::Collection->insert_one|MongoDB::Collection->update_one|MongoDB::Collection->remove|MongoDB::Database->run_command|MongoDB::|Net::LDAP->search|Net::LDAP->bind|Net::LDAP::LDIF|XML::XPath|XML::LibXML::XPathContext|XML::XPath::NodeSet|Storable::thaw|Storable::retrieve|FreezeThaw::thaw|Data::Dumper::eval|Data::Serializer::deserialize|Sereal::Decoder->decode|deserialize\(|deserialize |serialize\(|serialize|evalq\(|evalq |Template->process|Text::Template->fill_in|Text::MicroTemplate->render|HTML::Template->param|XML::Parser|XML::LibXML|XML::Simple::XMLin|XML::Twig|XML::SAX::ParserFactory|LWP::UserAgent|HTTP::Tiny|IO::Socket::INET|Net::HTTP|Net::HTTPS|AnyEvent::HTTP|WWW::Mechanize|close\(|close |read\(|read |sysread\(|sysread |write\(|write |syswrite\(|syswrite |print\(|print |unlink\(|unlink |rename\(|rename |copy\(|copy |move\(|move |chmod\(|chmod |chown\(|chown |mkdir\(|mkdir |rmdir\(|rmdir |opendir\(|opendir |readdir\(|readdir |closedir\(|closedir |stat\(|stat |lstat\(|lstat |utime\(|utime |truncate\(|truncate |binmode\(|binmode |seek\(|seek |tell\(|tell |mkpath\(|mkpath |make_path\(|make_path |remove_tree\(|remove_tree |rmtree\(|rmtree|Archive::Zip|Archive::Tar|IO::Uncompress::Unzip|Crypt::JWT|JSON::WebToken|Mojo::JWT|Authen::JWT|redirect\(|redirect_to\(|\$q->redirect|\$c->res->redirect|Access-Control-Allow-Origin|Access-Control-Allow-Credentials|while\s*\(.*\)\s*\{.*\}|for\s*\(.*\)\s*\{.*\}|sleep\(|alarm\(|threads::create|\(\.\*\)\+|\(\.\*\)\*|\[[^\]]+\]\+|\[[^\]]+\]\*|\(\.\+\)\+|\(\.\+\)\*)
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