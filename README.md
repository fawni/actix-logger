# actix-logger

drop-in replacement for the default actix web logger middleware 

simply changes the log level to `Warn` on redirection messages and client errors, and `Error` on server errors.

## Example

```rs
use actix_web::{App, HttpServer};
use actix_logger::Logger;

#[tokio::main]
async fn main() -> actix_web::Result<()> {
    twink::log::setup();

    HttpServer::new(|| {
        App::new().wrap(Logger::default().service(/* */))
    })
    .bind(("127.0.0.1", 8080))?
    .run()
    .await
}
```