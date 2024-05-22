# Go application for Harbour.Space DevOps course

This is a simple Go application that responds to a HTTP GET request with a JSON response.

## Build stages

- Build: This stage compiles the Go application and generates a binary `main`.

- Deploy: This stage stops the service in the `target` machine if it exists, and copies the binary to the `target` machine.

- Run as service: This stage starts the service in the `target` machine and enables it, so it starts on boot, guaranteeing that the API still responds even if the `target` machine is restarted.
