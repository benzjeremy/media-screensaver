# media-screensaver v1.5

Pre-release: this project is still in development.

## A personal note from Jeremy Benz

> I decided we needed to rename Spotify Screensaver to media-screensaver to avoid potential intellectual-property and trademark issues. The previous name directly referenced Spotify AB's brand. I wanted to make this change early, before it could lead to legal trouble. Same project, new name — thank you for sticking with it.
>
> — Jeremy Benz, project creator

## Changes

- Renamed the application, module, desktop identity, repository, website and documentation.
- Replaced the application icons with an original project-specific design.
- Kept existing local storage paths and legacy decryption compatible. New encrypted data uses PBKDF2-HMAC-SHA256 with 1,000,000 iterations.
- Local session tokens now use 32 random bytes and fail closed if randomness is unavailable.

## Installation

- [Linux AMD64](https://github.com/benzjeremy/media-screensaver/releases/download/v1.5/media-screensaver-v1.5-linux-amd64.tar.gz)
- [Windows AMD64](https://github.com/benzjeremy/media-screensaver/releases/download/v1.5/media-screensaver-v1.5-windows-amd64.zip)
- [Website](https://media-screensaver.benzjeremy.pp.ua/) · [Manual](https://wiki.benzjeremy.pp.ua/media-screensaver/)
- Source: `go install github.com/benzjeremy/media-screensaver@v1.5`

## Compatibility

Existing data remains in its legacy directory. After saving new encrypted data, older application versions cannot read that new ciphertext. Back up the local data before downgrading.

## License

GNU GPL-3.0.
