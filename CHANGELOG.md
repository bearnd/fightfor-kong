## Changelog

### v0.5.0

- Story No. 883: Add Let's Encrypt certificate with cron'ed renewal.

### v0.4.0

- Story No. 1111: Switch `fightfor-kong` Git deployment to GitLab.com.
- Story No. 1239: an upstream response is buffered to a temporary file.

### v0.3.0

- Updated `kong` configuration and enabled the CORS plugin.

### v0.2.1

- Removed the `nbf` validation from the JWT as it seems to be erroring out with the Auth0 JWT tokens.

### v0.2.0

Issue No. 301: Route-matching not working:

- Renamed the different routes to match the service name.
- Moved the JWT plugin configuration to the global scope.
- Changed the `mapbox` service route path.

### v0.1.1

- Removed the `nofile` limit increase as it is defined in the `fightfor-kong` systemd service.
- Fixed bug where the `kong.yml` wasn't rendered for production.

### v0.1.0

- Initial release.
