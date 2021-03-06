# :key:License Server:key:
A simple application for license key verification written in Golang.

## Deployment
- **Requirement**
    - Mysql / Sqlite3 / PostgreSQL
- **Deploy**
    - setup your db,webserver(i.e: nginx)
    - use repo `etc/license-server.service` file and change your needs
    - copy `etc/license-server.service` file to `/etc/systemd/system/license-server.service` or your os 
      systemd service config directory
    - Now enable service and start
    ```bash
       systemctl enable license-server.service
       systemctl start license-server.service
       systemctl status license-server.service
    ```
    - Stop the server
    ```bash
       systemctl stop license-server.service
    ```
    - use repo `etc/license-server.conf` file and change your needs
    - copy `etc/license-server.conf` file to `/etc/nginx/site-available` or your os 
      web server vhost config directory
    - now restart webserver ```service nginx restart```


## Development

- **Requirement**
    - Go >= 1.13
    - Mysql / Sqlite3 / PostgreSQL
    - dep [Dependency management for Go](https://golang.github.io/dep/)

- Clone the repo
    ```
    git clone https://github.com/hrshadhin/license-server.git
    cd license-server
    ```
- copy `.env.example` file to `.env` and change configuration according to your need.

- **Install dependency** `dep ensure`
- **Run** `go run main.go`
- **Test** `go test -v`
- **Build & Run**
    ```
    make 
    ./bin/license-server
    ```

- **:zap:N.B.:zap:**
   By default server run on `127.0.0.1:8000` you can specify the host and port also.
   ``` 
    ./bin/license-server -host=0.0.0.0 -port=8080
    ./bin/license-server -host=0.0.0.0
    ./bin/license-server -port=8080
   ```

## Cross Platform Build
- Cross compilation is hard, and docker is help us in that way! Install docker and pull
    docker image `docker pull karalabe/xgo-latest` and install a go package `go get github.com/karalabe/xgo`
- For build most of the platforms binary use 
    ```
    xgo github.com/hrshadhin/license-server
    ```
- Or specific platform
    ```
    xgo --targets=linux/amd64 github.com/hrshadhin/license-server 
    ```
- After build is finished you should have all platforms binary in your
current directory.
- More build details find [here](https://github.com/karalabe/xgo)
    
## API Docs
[Check docs directory](docs)

# :telescope: Need more help? 
Send an e-mail to H.R. Shadhin via [dev@hrshadhin.me](mailto:dev@hrshadhin.me)

# License
[MIT](https://github.com/hrshadhin/license-server/blob/master/LICENSE)
