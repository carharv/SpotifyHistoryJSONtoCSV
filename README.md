# SpotifyHistoryJSONtoCSV
Python script to convert your Spotify privacy data listening history JSON files to one CSV

The goal of this scipt is to extract the relevant details from my listening history and output a csv. The csv can then be imported into <a href="https://github.com/krateng/maloja">Maloja, a self-hosted scrobble database.</a>

Maloja has a feature that was designed to import listening history from a CSV exported from this <a href="https://benjaminbenben.com/lastfm-to-csv/"> LastFM to CSV converter.</a> This is a great feature that also opens the door to importing listening history from any source as long as it is in the same CSV format that the aforementioned converter uses. 

The format we want to get our listening history is the following:
<br>`ArtistName,Album,TrackName,day shortMonthAbbr hh:mm`
<br>`Kanye West,808s & Heartbreak,Heartless,22 Mar 2022 17:55`

### Privacy data

- Request your **privacy data** at Spotify to have access to your history for the past year [here](https://www.spotify.com/us/account/privacy/).
- Gather your files starting with `StreamingHistoryX.json`.

### Full privacy data (recommended)

> Full privacy data can be obtained by emailing **privacy@spotify.com** and requesting your data since the creation of the account.

- Request your data by email.
- Gather your files starting with `endsongX.json`.
