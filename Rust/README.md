# Full Regular Expression

```regex
^(?![ \t]*//).*\b(std::process::Command(::new)?\s*\(|Command::new\(|spawn\(|status\(|output\(|libloading::Library::new|dlopen::sym|wasmtime::.*(instantiate|execute|call)|wasmer::.*(instantiate|execute|call)|actix_multipart|actix_web::web::Payload|multipart::server|multer|rocket::fs::TempFile|axum::extract::Multipart|rusqlite::Connection::(execute|prepare)|postgres|tokio_postgres::Client::(query|prepare|execute)|mysql(::|::prelude::).*query|sqlx::query|diesel::sql_query|diesel::dsl::sql|SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|CREATE|TRUNCATE|mongodb::Collection::<[^>]+>::(find|find_one|update_one|update_many|aggregate|delete_one|delete_many)|mongodb::bson::doc!|ldap3::LdapConn|ldap3::LdapConnAsync|ldap3::LdapHandle|sxd_xpath::(Factory|XPath|Context)|select::document|roxmltree::Document|serde_json::from_(str|slice|reader)|ron::from_str|serde_yaml::from_str|toml::from_str|bincode::deserialize|postcard::from_bytes|rmp_serde::from_(read|slice)|ciborium::from_reader|tera::Tera::render|handlebars::Handlebars::render|askama::Template::render|maud::PreEscaped|quick_xml::Reader::from_(reader|file|str)|xml_rs::EventReader::new|xmltree::Element::parse|sxd_document::parser::parse|reqwest::(blocking::)?Client::(get|post|put|delete|request)|ureq::(get|post|request)|hyper::Client::request|isahc::prelude::RequestExt|surf::(get|post)|std::net::TcpStream::connect|std::fs::(write|remove_file|rename|copy|create_dir(_all)?|remove_dir(_all)?|read_dir|metadata|OpenOptions::new)|std::fs::File::create|std::io::(Read|Write)|std::path::Path(::new)?|std::os::unix::fs::PermissionsExt::set_mode|zip::read::ZipArchive::<.*>::new|zip::ZipArchive::<.*>::new|ZipArchive::by_index|ZipArchive::extract|tar::Archive::new|tar::Archive::unpack|jsonwebtoken::(encode|decode)|jsonwebtoken::TokenData|frank_jwt|jwt_simple::prelude|actix_web::HttpResponse::Found\(\)\.append_header\(\(.*LOCATION.*\)|rocket::response::Redirect::to|warp::redirect|axum::response::Redirect::to|actix_cors::Cors|tower_http::cors::CorsLayer|rocket_cors::Cors|warp::cors|std::thread::sleep|tokio::time::sleep|loop\s*\{|while\s+true|rayon::join|tokio::spawn|futures::stream::FuturesUnordered|fancy_regex::Regex::(new|is_match|captures)|onig::Regex(::new)?|onig::Regex::(search|find)|onig_sys)\b
```

## RCE(Os command unjection, Code Injection)

```
\b(std::process::Command(::new)?\s*\(|Command::new\(|spawn\(|status\(|output\()|\b(libloading::Library::new|dlopen::sym)\b|\b(wasmtime|wasmer)::.*(instantiate|execute|call)\b
```

## File Uploads

```
\b(actix_multipart|actix_web::web::Payload|multipart::server|multer|rocket::fs::TempFile|axum::extract::Multipart)\b
```

## Sql Injection

```
\b(rusqlite::Connection::execute|rusqlite::Connection::prepare|postgres|tokio_postgres::Client::(query|prepare|execute)|mysql(::|::prelude::).*query|sqlx::query|diesel::sql_query|diesel::dsl::sql)\b.*(\+|format!\(|write!\(|push_str\(|to_string\(|\{.*\})|\b(SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|CREATE|TRUNCATE)\b
```

## NoSQL Injection

```
\b(mongodb::Collection::<[^>]+>::(find|find_one|update_one|update_many|aggregate|delete_one|delete_many)|mongodb::bson::doc!)\b.*(\$where|\$\w+)
```

## Ldap Injection

```
\b(ldap3::LdapConn|ldap3::LdapConnAsync|ldap3::LdapHandle)\b.*(search|with_controls|simple_bind|sasl_bind)
```

## XPath Injection

```
\b(sxd_xpath::Factory|sxd_xpath::XPath|sxd_xpath::Context|select::document|roxmltree::Document)\b.*(evaluate|value|select|xpath)
```

## Insecure deserialization

```
\b(serde_json::from_(str|slice|reader)|ron::from_str|serde_yaml::from_str|toml::from_str|bincode::deserialize|postcard::from_bytes|rmp_serde::from_(read|slice)|ciborium::from_reader)\b
```

## SSTI

```
\b(tera::Tera::render|handlebars::Handlebars::render|askama::Template::render|maud::PreEscaped)\b
```

## XXE

```
\b(quick_xml::Reader::from_(reader|file|str)|xml_rs::EventReader::new|xmltree::Element::parse|sxd_document::parser::parse)\b
```

## SSRF

```
\b(reqwest::(blocking::)?Client::(get|post|put|delete|request)|ureq::(get|post|request)|hyper::Client::request|isahc::prelude::RequestExt|surf::(get|post)|std::net::TcpStream::connect)\b
```

## File/Folder manipulation(read, delete, creation)

```
\b(std::fs::(read|read_to_string|write|remove_file|rename|copy|create_dir(_all)?|remove_dir(_all)?|read_dir|metadata|OpenOptions::new)|std::fs::File::(open|create)|std::io::(Read|Write)|std::path::Path(::new)?|std::os::unix::fs::PermissionsExt::set_mode)\b
```

## Zip vulns

```
\b(zip::read::ZipArchive::<.*>::new|zip::ZipArchive::<.*>::new|ZipArchive::by_index|ZipArchive::extract|tar::Archive::new|tar::Archive::unpack)\b
```

## JWT

```
\b(jsonwebtoken::(encode|decode)|jsonwebtoken::TokenData|frank_jwt|jwt_simple::prelude)\b
```

## Open Redirect

```
\b(actix_web::HttpResponse::Found\(\)\.append_header\(\(.*LOCATION.*\)|rocket::response::Redirect::to|warp::redirect|axum::response::Redirect::to)\b
```

## Cors

```
\b(actix_cors::Cors|tower_http::cors::CorsLayer|rocket_cors::Cors|warp::cors)\b
```

## Dos

```
\b(std::thread::sleep|tokio::time::sleep|loop\s*\{|while\s+true|rayon::join|tokio::spawn|futures::stream::FuturesUnordered)\b
```

## ReDOS

```
\b(fancy_regex::Regex::(new|is_match|captures)|onig::Regex(::new)?|onig::Regex::(search|find)|onig_sys)\b
```