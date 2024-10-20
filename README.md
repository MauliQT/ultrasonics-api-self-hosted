![](https://raw.githubusercontent.com/XDGFX/ultrasonics-api/master/.github/ultrasonics-api-logo.svg)

---

## **Important**

The offical API isn't working anymore and had some issues with deployment and ease of use. This [mauliqt/ultrasonics-api](https://github.com/MauliQT/ultrasonics-api-self-hosted) alongside with [mauliqt/ultrasonics](https://github.com/MauliQT/ultrasonics-tidal) is working but with some issues, i havent been able to fix yet.


## The api proxy for ultrasonics.

This is the source code for the ultrasonics-api proxy server. It's purpose is to store private api keys for services such as Spotify, Deezer, and Last.fm, while providing an endpoint for ultrasonics to access those apis.


## **Installation** Use 
Either make the image using the `Dockerfile`, or pull from the inofficial repo: `MauliQT/ultrasonics-api`.

Recommended usage: `docker-compose`
```yaml
version: "3.7"
services:
  ultrasonics-api:
    image: mauliqt/ultrasonics-api:1.1
    container_name: ultrasonics-api
    restart: unless-stopped

    ports:
      - 8003:8003

    environment:
      - PUID=${PUID}
      - PGID=${PGID}

      - SPOTIFY_CLIENT_ID=abc
      - SPOTIFY_CLIENT_SECRET=xyz
      - SPOTIFY_REDIRECT_URI=http://localhost:8003/api/spotify/auth/

      - LASTFM_API_KEY=xyz

      - DEEZER_APP_ID=abc
      - DEEZER_APP_SECRET=xyz
      - DEEZER_REDIRECT_URI=https://localhost:8003/api/deezer/auth
```

## **Environment Variables**
These environment variables can be applied to your Heroku instance, or saved in a `.env` file in this directory.

If you don't use a service, you can remove it's environment variables.

Most services require you to get an api key / secret by creating an account and setting up an application. Documentation for each service can be found below.

<br/>

### Finding API Keys
| App     | Link                                                                                                                  | Notes                                                           |
| ------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Spotify | [https://developer.spotify.com](https://developer.spotify.com/documentation/web-api/quick-start/#set-up-your-account) | Refer to "Set Up Your Account" and "Register Your Application". |
| Last.fm | [https://www.last.fm/api](https://www.last.fm/api/account/create)                                                     |                                                                 |
| Deezer  | [https://developers.deezer.com/myapps/](https://developers.deezer.com/myapps/)                                        |                                                                 |
<br/>

### `.env` file
```
FLASK_APP=ultrasonics_api

USE_REDIS=False
REDIS_URL=[Only if USE_REDIS=True]

SPOTIFY_CLIENT_ID=abc
SPOTIFY_CLIENT_SECRET=xyz

LASTFM_API_KEY=abc

DEEZER_APP_ID=abc
DEEZER_APP_SECRET=xyz
```
