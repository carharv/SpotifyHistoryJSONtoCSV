# SpotifyHistoryJSONtoCSV
Python script to convert your Spotify privacy data listening history JSON files to one CSV file. 

The goal of this scipt is to extract the relevant details from my listening history and output a csv. The csv can then be imported into <a href="https://github.com/krateng/maloja">Maloja, a self-hosted scrobble database.</a>

However, this script can also be used to easily merge multiple Spotify JSON files and analyze them with Python. 

### CSV Formatting

Maloja has a feature that was designed to import listening history from a CSV exported from this <a href="https://benjaminbenben.com/lastfm-to-csv/"> LastFM to CSV converter.</a> This is a great feature that also opens the door to importing listening history from any source as long as it is in the same CSV format that the aforementioned converter uses. 

The format we want to get our listening history is the following:
<br>`ArtistName,Album,TrackName,day shortMonthAbbr hh:mm`
<br>`Kanye West,808s & Heartbreak,Heartless,22 Mar 2022 17:55`

### Getting your streaming history from Spotify

#### Privacy data

- Request your **privacy data** at Spotify to have access to your history for the past year [here](https://www.spotify.com/us/account/privacy/).
- Gather your files starting with `StreamingHistoryX.json`.

#### Full privacy data (recommended)

> Full privacy data can be obtained by emailing **privacy@spotify.com** and requesting your data since the creation of the account.

- Request your data by email.
- Gather your files starting with `endsongX.json`.

### Spotify JSON Structure

Each object in the JSON file provided by Spotify consists of the following fields:

|Field|Description|
| --- |       --- |
|ts|This field is a timestamp indicating when the track stopped playing in UTC (Coordinated Universal Time). The order is year, month and day followed by a timestamp in military time|
|username|This field is your Spotify username.|
|platform|This field is the platform used when streaming the track (e.g. Android OS, Google Chromecast).|
|ms_played|This field is the number of milliseconds the stream was played.|
|conn_country|This field is the country code of the country where the stream was played (e.g. SE - Sweden).|
|ip_addr_decrypted|This field contains the IP address logged when streaming the track.|
|user_agent_decrypted|This field contains the user agent used when streaming the track (e.g. a browser, like Mozilla Firefox, or Safari)|
|master_metadata_track_name|This field is the name of the track.|
|master_metadata_album_artist_name|This field is the name of the artist, band or podcast.|
|master_metadata_album_album_name|This field is the name of the album of the track.|
|spotify_track_uri|A Spotify URI, uniquely identifying the track in the form of “spotify:track:base-62 string” A Spotify URI is a resource identifier that you can enter, for example, in the Spotify Desktop client’s search box to locate an artist, album, or track.|
|episode_name|This field contains the name of the episode of the podcast.|
|episode_show_name|This field contains the name of the show of the podcast.|
|spotify_episode_uri|A Spotify Episode URI, uniquely identifying the podcast episode in the form of “spotify:episode:base-62 string” A Spotify Episode URI is a resource identifier that you can enter, for example, in the Spotify Desktop client’s search box to locate an episode of a podcast.|
|reason_start|This field is a value telling why the track started (e.g. “trackdone”)|
|reason_end|This field is a value telling why the track ended (e.g. “endplay”).|
|shuffle|This field has the value True or False depending on if shuffle mode was used when playing the track.|
|skipped|This field indicates if the user skipped to the next song|
|offline|This field indicates whether the track was played in offline mode (“True”) or not (“False”).|
|offline_timestamp|This field is a timestamp of when offline mode was used, if used.|
|incognito_mode|This field indicates whether the track was played in incognito mode (“True”) or not (“False”).|

### Using the python script

I recommend using <a href="colab.research.google.com">Google Colab.</a> I added both the Google Colab notebook, *SpotifyHistorytoCSV.pynb*, and the raw python code, *SpotifyHistorytoCSV.py*.

1. Upload the notebook to Google Colab.
2. Upload the Spotify JSON files directly to the */content/* directory (the default directory when you click the file icon that contains the *sample_data*          folder. Or create a new folder in the content directory to upload them to such as */content/json/*. It doesn't matter where you put them as long as you specify their directory path in the script.
3. Run the script.
4. Download the CSV file that is output to the default */content/* directory.
