# Spotify Song Tracker for OBS

This web application displays the currently playing track on Spotify, along with album art, track information, and progress.

## Getting Started

To use this project, you'll need to obtain the following credentials from Spotify:

- accessToken
- refreshToken
- clientId
- clientSecret

### Step 1: Create a Spotify Developer Account

If you haven't already, create a Spotify Developer account at [Spotify for Developers](https://developer.spotify.com/).

### Step 2: Create a Spotify Application

1. Log in to your Spotify Developer account.
2. Go to the [Dashboard](https://developer.spotify.com/dashboard/applications).
3. Click on "Create an App" and fill out the necessary information.
4. Note down the Client ID and Client Secret generated for your app.

### Step 3: Obtain Authorization Code

1. Open a web browser and navigate to the following URL:
   ```plaintext
   https://accounts.spotify.com/authorize?client_id=your_client_id&response_type=code&redirect_uri=your_redirect_uri&scope=user-read-playback-state user-read-currently-playing
   ```

   Replace `your_client_id` with your Client ID and `your_redirect_uri` with your Redirect URI configured in your Spotify Developer Dashboard.

2. The user will log in and authorize your application. After authorization, Spotify will redirect the user to your Redirect URI with a `code` parameter in the URL. It will look something like this:
   ```plaintext
   your_redirect_uri?code=authorization_code
   ```

3. Copy the `authorization_code` from the URL.

### Step 4: Exchange Authorization Code for Access and Refresh Tokens

Use the following `curl` command to exchange the authorization code for an Access Token and a Refresh Token:

```bash
curl -X "POST" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d "grant_type=authorization_code&code=authorization_code&redirect_uri=your_redirect_uri&client_id=your_client_id&client_secret=your_client_secret" \
     https://accounts.spotify.com/api/token
```

Replace `authorization_code`, `your_redirect_uri`, `your_client_id`, and `your_client_secret` with your actual authorization code, Redirect URI, Client ID, and Client Secret respectively.


### Step 4: Configure the Application

Replace the placeholders in `spotify_current_track.html` with your obtained credentials:

```javascript
const accessToken = 'accessToken';  Replace with your Spotify Access Token. More info on README
const refreshToken = 'refreshToken';  Replace with your Spotify Refresh Token. More info on README
const clientId = 'clientId';  Replace with your Spotify Client ID from https://developer.spotify.com/
const clientSecret = 'clientSecret';  Replace with your Spotify Client Secret from https://developer.spotify.com/
```

## Running the Application

Open `spotify_current_track.html` in a web browser. The application will fetch and display the currently playing track from your Spotify account.

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.
