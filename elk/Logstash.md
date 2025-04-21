### Intro

- **Data pipeline**
    
- **L in ELK**
    
- **Builded Using Jruby !** Why?
    
- **Collect → Process → Send data**
###  Pipeline Stages

- **Input**: File, Kafka, Syslog, etc.
    
- **Filter**: Parse, Clean, Transform (e.g., Grok)
    
- **Output**: Elasticsearch, Kafka, File, Stdout
### Pipeline Example :

```ruby
input {
  file {
    path => "/path/to/your/nginx/access.log"
    start_position => "beginning"
  }
}

filter {
  grok {
    match => {
      "message" => '%{IP:client_ip} - - \[%{HTTPDATE:timestamp}\] "%{WORD:method} %{URIPATH:request} HTTP/%{NUMBER:http_version}" %{NUMBER:response_code} %{NUMBER:bytes}'
    }
  }

  date {
    match => ["timestamp", "dd/MMM/yyyy:HH:mm:ss Z"]
    target => "timestamp"
  }
}

output {
   elasticsearch {
     hosts => ["http://localhost:9200"]
     index => "nginx-logs"
   }
}
