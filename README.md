# pushbullet

A small python script to interface with
[Pushbullet](http://www.pushbullet.com).

I wrote this because the existing python library for pushbullet did
not support the v2 API.

## Requirements

The _requests_ library is required.  Use your OS defined method for
including python libraries or *pip install requests*.

## Authentication

This is not a registered app and as such does not use OAuth2 to
authenticate to Pushbullet.  It requires the use of an API key.

You can obtain an API Key (sometimes known as an Access Token) on your
Pushbullet [Account Settings](https://www.pushbullet.com/#settings/account) page.

Specify the API Key on the command line as *--api-key <API_KEY>* or
add it to your _${HOME}/.netrc_:

```shell
    machine pushbullet.com login EMAIL password API_KEY
```

One advantage of using a .netrc entry is that the login field in the
pushbullet.com entry will be used as the default destination.

Remember to set restrictive permissions for your .netrc.  Anyone who
can see your API Key has access to your Pushbullet account.

## Destinations

Destinations can be an e-mail address, a device name, a device
identifier, a channel name or a channel identifier.

You can only push to your private channels.

To list all your devices use

```shell
    # pushbullet --devices
```

To list all your channels (including public channels you are
subscribed to):

```shell
    # pushbullet --channels
```

## Examples

Most of these examples assume your .netrc is set up

### Push a note to all your devices

```shell
    # pushbullet --title Hello --note World
```

### Push a note to your friend

```shell
    # pushbullet --dest my.friend@email.us --title Hello --note World
```

### Push a file to a specific device

```shell
    # pushbullet --dest 'Nexus 9' --title "A pretty picture" --file IMG0001.JPG
```

### Push a URL to a channel

```shell
    # pushbullet --dest mychannel --title "Look at this" --link "https://a.funny.url.com"
```

# Author

Jeffrey C Honig <jch@honig.net>

