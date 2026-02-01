# Full Regular Expression

```regex
^(?![ \t]*//)(?![ \t]*/\*).*?(?:\b(?:Process\.Start|ProcessStartInfo|PowerShell\.Create|PowerShell\.Invoke|CSharpCodeProvider|CodeDomProvider\.CompileAssemblyFromSource|Assembly\.Load(?:From|File)?|Expression\.Compile|DynamicInvoke|AppDomain\.ExecuteAssembly)\b|\b(?:HttpPostedFile|IFormFile|FormFile|FileUpload|Request\.Files|MultipartReader)\b|\b(?:SqlCommand|OdbcCommand|OleDbCommand)\b.*(?:\.Execute(?:Reader|NonQuery|Scalar)|\((?:.*\+|string\.Format|\$"|".*))|\b(?:IMongoCollection<[^>]+>\.Find|BsonDocument\.Parse|Aggregate\([^)]*\$where)\b|\b(?:DirectorySearcher|DirectoryEntry|LdapConnection)\b.*(?:Filter|Search)\b|\b(?:XPathDocument|XPathNavigator|XPathExpression)\b.*(?:Evaluate|Compile|Select)\b|\b(?:BinaryFormatter\.Deserialize|SoapFormatter\.Deserialize|JavaScriptSerializer\.Deserialize(?:Object)?|JsonConvert\.Deserialize(?:Object|Object<.*>|Object\[\])?|JsonConvert\.DeserializeObject|XmlSerializer\.Deserialize|LosFormatter\.Deserialize|ObjectStateFormatter\.Deserialize|NetDataContractSerializer\.Deserialize|DataContractSerializer\.ReadObject|DataContractJsonSerializer\.ReadObject|BinaryMessageFormatter\.Read)\b|\b(?:RazorEngine\.Parse|Razor\.Compile|Microsoft\.AspNetCore\.Mvc\.Razor)\b|\b(?:XmlDocument|XmlReader|XDocument|XmlSerializer)\.(?:Load|Create)\b.*(?:DtdProcessing\s*=\s*DtdProcessing\.Parse)?|\b(?:HttpClient\.(?:GetAsync|PostAsync|SendAsync)|WebRequest\.Create|WebRequest\.GetResponse|HttpWebRequest|WebClient|RestClient|TcpClient)\b|\b(?:File\.(?:Read(?:All(?:Text|Lines))?|Write(?:All(?:Text|Lines))?|Delete|Append(?:All(?:Text|Lines))?|Open|Copy|Move)|Directory\.(?:CreateDirectory|Delete|Move)|FileStream|StreamReader|StreamWriter)\b|\b(?:ZipFile\.ExtractToDirectory|ZipArchiveEntry\.FullName.*Path\.Combine)\b|\b(?:JwtSecurityTokenHandler|JsonWebToken|Microsoft\.IdentityModel\.Tokens|System\.IdentityModel\.Tokens\.Jwt)\b|\b(?:Response\.Redirect|HttpResponse\.Redirect|RedirectToAction|RedirectPermanent|RedirectToRoute)\b|\b(?:Access-Control-Allow-Origin|CorsPolicyBuilder|WithOrigins|AllowAnyOrigin|AddCors)\b|\b(?:Thread\.Sleep|Task\.Delay|while\s*\(true\)|for\s*\(;;\)|Parallel\.ForEach|GC\.Collect)\b|\bRegex\.(?:Match|IsMatch|Replace)\b|new\s+Regex\(@?"[^"]*(?:\+|\*){2,}[^"]*"\))
```

## RCE(Os command unjection, Code Injection)

```
\b(Process\.Start|ProcessStartInfo|PowerShell\.Create|PowerShell\.Invoke|CSharpCodeProvider|CodeDomProvider\.CompileAssemblyFromSource|Assembly\.Load(?:From|File)?|Expression\.Compile|DynamicInvoke|AppDomain\.ExecuteAssembly)\b
```

## File Uploads

```
\b(HttpPostedFile|IFormFile|FormFile|FileUpload|Request\.Files|MultipartReader)\b
```

## Sql Injection

```
\b(SqlCommand|OdbcCommand|OleDbCommand)\b.*(\.Execute(Reader|NonQuery|Scalar)|\((.*\+|string\.Format|\$"|".*\b(?:SELECT|INSERT|UPDATE|DELETE|DROP|ALTER|CREATE|UNION|INTO|FROM|WHERE|ORDER|GROUP|HAVING|LIMIT)\b))
```

## NoSQL Injection

```
\b(IMongoCollection<[^>]+>\.Find|BsonDocument\.Parse|Aggregate\([^)]*\$where)\b
```

## Ldap Injection

```
\b(DirectorySearcher|DirectoryEntry|LdapConnection)\b.*(Filter|Search)\b
```

## XPath Injection

```
\b(XPathDocument|XPathNavigator|XPathExpression)\b.*(Evaluate|Compile|Select)\b
```

## Insecure deserialization

```
\b(BinaryFormatter\.Deserialize|SoapFormatter\.Deserialize|JavaScriptSerializer\.Deserialize(Object)?|JsonConvert\.Deserialize(Object|Object<.*>|Object\[\])?|JsonConvert\.DeserializeObject|XmlSerializer\.Deserialize|LosFormatter\.Deserialize|ObjectStateFormatter\.Deserialize|NetDataContractSerializer\.Deserialize|DataContractSerializer\.ReadObject|DataContractJsonSerializer\.ReadObject|BinaryMessageFormatter\.Read)\b
```

## SSTI

```
\b(RazorEngine\.Parse|Razor\.Compile|Microsoft\.AspNetCore\.Mvc\.Razor)\b
```

## XXE

```
\b(XmlDocument|XmlReader|XDocument|XmlSerializer)\.(Load|Create)\b.*(DtdProcessing\s*=\s*DtdProcessing\.Parse)?
```

## SSRF

```
\b(HttpClient\.(GetAsync|PostAsync|SendAsync)|WebRequest\.Create|WebRequest\.GetResponse|HttpWebRequest|WebClient|RestClient|TcpClient)\b
```

## File/Folder manipulation(read, delete, creation)

```
\b(File\.(Read(All(Text|Lines))?|Write(All(Text|Lines))?|Delete|Append(All(Text|Lines))?|Open|Copy|Move)|Directory\.(CreateDirectory|Delete|Move)|FileStream|StreamReader|StreamWriter)\b
```

## Zip vulns

```
\b(ZipFile\.ExtractToDirectory|ZipArchiveEntry\.FullName.*Path\.Combine)\b
```

## JWT

```
\b(JwtSecurityTokenHandler|JsonWebToken|Microsoft\.IdentityModel\.Tokens|System\.IdentityModel\.Tokens\.Jwt)\b
```

## Open Redirect

```
\b(Response\.Redirect|HttpResponse\.Redirect|RedirectToAction|RedirectPermanent|RedirectToRoute)\b
```

## Cors

```
\b(Access-Control-Allow-Origin|CorsPolicyBuilder|WithOrigins|AllowAnyOrigin|AddCors)\b
```

## Dos

```
\b(Thread\.Sleep|Task\.Delay|while\s*\(true\)|for\s*\(;;\)|Parallel\.ForEach|GC\.Collect)\b
```

## ReDOS

```
\bRegex\.(Match|IsMatch|Replace)\b|new Regex\(@?"[^"]*(\+|\*){2,}[^"]*"\)
```