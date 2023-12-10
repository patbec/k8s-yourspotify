# k8s-yourspotify  <img width="10%" align="right" src="./docs/logo.svg"></img>


A deployment to host the application [yourspotify](https://github.com/Yooooomi/your_spotify) on Kubernetes.

![Preview](./docs/website-preview-dark.png#gh-dark-mode-only)
![Preview](./docs/website-preview-light.png#gh-light-mode-only)

## Preparation

The application requires a Spotify application and a valid SSL certificate.

### Spotify

[Click here](https://developer.spotify.com/dashboard) to create a new Spotify application to get `Client_ID` and `Client_Secret`.

The values `Redirect URIs` and `APIs used` are required:

| Setting          | Example value                                                            |
| ---------------- | ------------------------------------------------------------------------ |
| App name         | `Your Spotify`                                                           |
| App description  | `My Spotify history.`                                                    |
| Website          | `https://yourspotify.k8s.thinkbox.center`                                |
| Redirect URIs    | `https://yourspotify-backend.k8s.thinkbox.center/oauth/spotify/callback` |
| Bundle IDs       | ` `                                                                      |
| Android packages | ` `                                                                      |
| APIs used        | ` Web API`                                                               |

Replace the values `spotify_public` and `spotify_secret` in the `yourspotify-secrets` object.

### SSL Certificate

A valid SSL certificate is required for this service, this part is not included in the example. Replace the defined domain with your own in the deplyoment.

> A wildcard certificate can be created and defined with the parameter `--default-ssl-certificate=default/wildcard-certificate` on the nginx-ingress-controller.

### Database

The mongo database requires `AVX` in a [newer version](https://github.com/turnkeylinux/tracker/issues/1724), this is not easily possible in Kubernetes. For this reason, the latest version is not used here.

## History

The Spotify WebApi only returns the listening history of the last day. To import your previous history, a backup of your user data must be requested directly from Spotify.

This can be done [here](https://www.spotify.com/de/account/privacy/) and can take up to 30 days.

- Select the checkbox **Extended streaming history**

After some time you will receive a download link from Spotify, you can import this data into yourspotify.


## Sources

[Click here](https://github.com/Yooooomi/your_spotify) to get more information on the official project page. [your_spotify](https://github.com/Yooooomi/your_spotify) is developed by [Timothee Boussus](https://github.com/Yooooomi).