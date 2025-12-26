# ntfy Home Assistant Add-on

[![GitHub Release][releases-shield]][releases]
[![License][license-shield]](LICENSE.md)

Self-hosted notification service add-on for Home Assistant.

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
[license-shield]: https://img.shields.io/github/license/michalchecinski/hassio-ntfy-sh-addon.svg
[releases-shield]: https://img.shields.io/github/release/michalchecinski/hassio-ntfy-sh-addon.svg
[releases]: https://github.com/michalchecinski/hassio-ntfy-sh-addon/releases

## About

This repository contains the Home Assistant add-on for [ntfy](https://ntfy.sh/), a simple HTTP-based pub-sub notification service.

## Installation

1. Add this repository to your Home Assistant add-on store:
   ```
   https://github.com/Wuest3nFuchs/hassio-ntfy-sh-addon
   ```

2. Install the ntfy add-on from the add-on store

3. Configure and start the add-on

## Add-ons

This repository contains the following add-on:

### [ntfy](./ntfy)

![Addon Stage][stage-shield]
![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports armhf Architecture][armhf-shield]
![Supports armv7 Architecture][armv7-shield]
![Supports i386 Architecture][i386-shield]

[stage-shield]: https://img.shields.io/badge/stage-stable-green.svg

Self-hosted notification service that allows you to send push notifications to your phone or desktop via simple HTTP POST requests.

## Support

Got questions? Please check:

- [Open an issue](https://github.com/michalchecinski/hassio-ntfy-sh-addon/issues) for bugs and feature requests
- [ntfy documentation](https://docs.ntfy.sh/) for general ntfy usage
- [Home Assistant Community](https://community.home-assistant.io/) for general Home Assistant support

## Contributing

This is an active open-source project. We are always open to people who want to
use the code or contribute to it.

We have set up a separate document containing our
[contribution guidelines](CONTRIBUTING.md).

Thank you for being involved! :heart_eyes:

## License

MIT License

Copyright (c) 2024

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
