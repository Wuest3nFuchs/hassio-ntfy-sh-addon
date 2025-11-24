# Home Assistant Add-on: ntfy

Self-hosted notification service for sending push notifications to your phone or desktop.

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports armhf Architecture][armhf-shield]
![Supports armv7 Architecture][armv7-shield]
![Supports i386 Architecture][i386-shield]

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg

## About

This add-on runs [ntfy](https://ntfy.sh/) - a simple HTTP-based pub-sub notification service. It allows you to send push notifications to your phone or desktop via scripts from any computer, entirely without signup, cost or setup. Perfect for sending notifications from your Home Assistant automations or scripts running on your server.

## Installation

1. Navigate in your Home Assistant frontend to **Supervisor** -> **Add-on Store**
2. Add this repository URL: `https://github.com/michalchecinski/hassio-ntfy-sh-addon`
3. Find the "ntfy" add-on and click it
4. Click on the "INSTALL" button

## How to use

1. Start the add-on
2. Check the add-on log output to see the result
3. The ntfy web interface will be available on port 8080 (or your configured port)
4. Send notifications via HTTP POST to `http://your-home-assistant:8080/your-topic`

### Example: Sending a notification

```bash
# Send a simple notification
curl -d "Your notification message" http://your-home-assistant:8080/mytopic

# Send with title and tags
curl -H "Title: Important Alert" \
     -H "Tags: warning,skull" \
     -d "Something important happened!" \
     http://your-home-assistant:8080/alerts
```

### Home Assistant Integration

Add to your `configuration.yaml`:

```yaml
notify:
  - name: ntfy
    platform: rest
    resource: http://localhost:8080/home-assistant
    method: POST_JSON
    data:
      message: "{{ message }}"
      title: "{{ title }}"
```

Then use in automations:

```yaml
automation:
  - alias: "Send notification when door opens"
    trigger:
      platform: state
      entity_id: binary_sensor.front_door
      to: 'on'
    action:
      service: notify.ntfy
      data:
        message: "Front door opened"
        title: "Security Alert"
```

## Configuration

Add-on configuration:

```yaml
port: 8080
base_url: ""
auth_file: ""
auth_default_access: "read-write"
cache_file: "/data/cache.db"
log_level: "INFO"
behind_proxy: false
enable_signup: false
enable_login: false
enable_reservations: false
```

### Option: `port`

The port number to run ntfy on. Default is 8080.

### Option: `base_url`

The base URL for your ntfy instance. Leave empty if accessing locally or set to your external URL if behind a reverse proxy.

### Option: `auth_file`

Path to authentication file (relative to /data). Leave empty to disable authentication. When set, you can create users and manage access.

### Option: `auth_default_access`

Default access level for topics. Options:
- `read-write`: Full access (default)
- `read-only`: Can only subscribe
- `write-only`: Can only publish
- `deny-all`: No access

### Option: `cache_file`

Location of the cache database file. Default is `/data/cache.db`.

### Option: `log_level`

Log verbosity level. Options: `TRACE`, `DEBUG`, `INFO`, `WARN`, `ERROR`. Default is `INFO`.

### Option: `behind_proxy`

Set to `true` if running behind a reverse proxy. Default is `false`.

### Option: `enable_signup`

Allow users to sign up for accounts. Default is `false`.

### Option: `enable_login`

Enable user login functionality. Default is `false`.

### Option: `enable_reservations`

Allow users to reserve topic names. Default is `false`.

## Mobile Apps

Download the ntfy mobile app:
- [Android](https://play.google.com/store/apps/details?id=io.heckel.ntfy)
- [iOS](https://apps.apple.com/us/app/ntfy/id1625396347)

Configure the app to use your Home Assistant IP and port (e.g., `http://192.168.1.100:8080`).

## Authentication

To enable authentication:

1. Set `auth_file` to a filename (e.g., `auth.db`)
2. Restart the add-on
3. Use the ntfy CLI to manage users:

```bash
# Access the add-on container
docker exec -it addon_local_ntfy /bin/bash

# Add a user
ntfy user add --config /data/config/server.yml myuser

# List users
ntfy user list --config /data/config/server.yml
```

## Support

For issues with this add-on, please check:
1. The add-on logs in the Home Assistant Supervisor
2. The [ntfy documentation](https://docs.ntfy.sh/)
3. [ntfy GitHub issues](https://github.com/binwiederhier/ntfy/issues)

## License

This add-on is licensed under the Apache 2.0 License.
The ntfy project is licensed under the Apache 2.0 License.