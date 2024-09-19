# tgx
Python Web App which indexes a telegram chat, channel or group and serves its files for download.

## Deploy Guide

- **Clone to local machine.**

```bash
git clone https://github.com/GutengMorgen/tgx

cd tgx
```

- **Create and activate virtual environment.**

```bash
python3 -m venv venv

source venv/bin/activate
```

- **Install dependencies.**

```bash
pip3 install -U -r requirements.txt
```

- **Environment Variables.**

| Variable Name                        | Value                                                                                                                                                          |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `API_ID` (required)                  | Telegram api_id obtained from <https://my.telegram.org/apps>.                                                                                                  |
| `API_HASH` (required)                | Telegram api_hash obtained from <https://my.telegram.org/apps>.                                                                                                |
| `INDEX_SETTINGS` (required)          | See the below description.                                                                                                                                     |
| `SESSION_STRING` (required)          | String obtained by running `$ python3 app/generate_session_string.py`. (Login with the telegram account which is a participant of the given channel (or chat). |
| `PORT` (optional)                    | Port on which app should listen to, defaults to 8080.                                                                                                          |
| `HOST` (optional)                    | Host name on which app should listen to, defaults to 0.0.0.0.                                                                                                  |
| `DEBUG` (optional)                   | Give `true` to set logging level to debug, info by default.                                                                                                    |
| `BLOCK_DOWNLOADS` (optional)         | Enable downloads or not. If any value is provided, downloads will be disabled.                                                                                 |
| `RESULTS_PER_PAGE` (optional)        | Number of results to be returned per page defaults to 20.                                                                                                      |
| `TGINDEX_USERNAME` (optional)        | Username for authentication, defaults to `''`.                                                                                                                 |
| `PASSWORD` (optional)                | Password for authentication, defaults to `''`.                                                                                                                 |
| `SHORT_URL_LEN` (optional)           | Url length for aliases                                                                                                                                         |
| `SESSION_COOKIE_LIFETIME` (optional) | Number of minutes, for which authenticated session is valid for, after which user has to login again. defaults to 60.                                          |
| `SECRET_KEY` (optional)              | 32 characters long string for signing the session cookies, required if authentication is enabled.                                                              |

- **Setting value for `INDEX_SETTINGS`**

This is the general format, change the values of corresponding fields as your requirements. You can copy paste this as is to index all the channels available in your account.

**Remember to remove spaces.**

```json
{
  "index_all": true,
  "index_private": false,
  "index_group": false,
  "index_channel": true,
  "exclude_chats": [],
  "include_chats": []
}
```

> - `index_all` - Whether to consider all the chats associated with the telegram account. Value should either be `true` or `false`.
> - `index_private` - Whether to index private chats. Only considered if `index_all` is set to `true`. Value should either be `true` or `false`.
> - `index_group` - Whether to index group chats. Only considered if `index_all` is set to `true`. Value should either be `true` or `false`.
> - `index_channel` - Whether to index channels. Only considered if `index_all` is set to `true`. Value should either be `true` or `false`.
> - `exclude_chats` - An array/list of chat id's that should be ignored for indexing. Only considered if `index_all` is set to `true`.
> - `include_chats` - An array/list of chat id's to index. Only considered if `index_all` is set to `false`.

- **Run app.**

```bash
python3 -m app
```

## API

Here's the api description. [API](https://github.com/odysseusmax/tg-index/wiki/API)

## Contributions

Contributions are welcome.

## Credits

[tg-index](https://github.com/odysseusmax/tg-index) ==> [TgindexPro](https://github.com/rayanfer32/TgindexPro) ==> [tgx](https://github.com/GutengMorgen/tgx)

## License
Code released under [The GNU General Public License](LICENSE).
