# Creating a new API client

In your wallabag account, you can create a new API client at this URL http://localhost:8000/developer/client/create.

Just give the redirect URL of your application and create your client.
If your application is a desktop one, put whatever URL suits you the most.

You get information like this:

```
Client ID: 1_3o53gl30vhgk0c8ks4cocww08o84448osgo40wgw4gwkoo8skc

Client secret: 636ocbqo978ckw0gsw4gcwwocg8044sco0w8w84cws48ggogs4
```

# Obtaining a access token

For each API call, you'll need an access token (ie. `access_token` key after requesting a token).

## Using user client information (recommended way)

Let's create it with this command (replace `client_id` and `client_secret` with their values):

```bash
http POST http://localhost:8000/oauth/v2/token \
    grant_type=client_credentials \
    client_id=1_3o53gl30vhgk0c8ks4cocww08o84448osgo40wgw4gwkoo8skc \
    client_secret=636ocbqo978ckw0gsw4gcwwocg8044sco0w8w84cws48ggogs4
```

Or using cURL:

```bash
curl -s "https://localhost:8000/oauth/v2/token?grant_type=client_credentials&client_id=1_3o53gl30vhgk0c8ks4cocww08o84448osgo40wgw4gwkoo8skc&client_secret=636ocbqo978ckw0gsw4gcwwocg8044sco0w8w84cws48ggogs4"
```

You'll have this in return:

```http
HTTP/1.1 200 OK
Cache-Control: no-store, private
Connection: close
Content-Type: application/json
Date: Tue, 05 Apr 2016 08:44:33 GMT
Host: localhost:8000
Pragma: no-cache

{
    "access_token": "YjM4ZWVmNDJiNmIxNTEzOTU5ZGFhNjU0NjMyOGZmOTdhOTgxZTM1NDFkZTQzY2FhM2Q3MjhlYmU5Y2YwZDFjMw",
    "expires_in": 3600,
    "token_type": "bearer",
    "scope": null
}
```

## Using user login / password (deprecated way)

Let's create it with this command (replace `client_id`, `client_secret`, `username` and `password` with their values):

```bash
http POST http://localhost:8000/oauth/v2/token \
    grant_type=password \
    client_id=1_3o53gl30vhgk0c8ks4cocww08o84448osgo40wgw4gwkoo8skc \
    client_secret=636ocbqo978ckw0gsw4gcwwocg8044sco0w8w84cws48ggogs4 \
    username=wallabag \
    password=wallabag
```

Or using cURL:

```bash
curl -s "https://localhost:8000/oauth/v2/token?grant_type=password&client_id=1_3o53gl30vhgk0c8ks4cocww08o84448osgo40wgw4gwkoo8skc&client_secret=636ocbqo978ckw0gsw4gcwwocg8044sco0w8w84cws48ggogs4&username=wallabag&password=wallabag"
```

You'll have this in return:

```http
HTTP/1.1 200 OK
Cache-Control: no-store, private
Connection: close
Content-Type: application/json
Date: Tue, 05 Apr 2016 08:44:33 GMT
Host: localhost:8000
Pragma: no-cache

{
    "access_token": "ZGJmNTA2MDdmYTdmNWFiZjcxOWY3MWYyYzkyZDdlNWIzOTU4NWY3NTU1MDFjOTdhMTk2MGI3YjY1ZmI2NzM5MA",
    "expires_in": 3600,
    "refresh_token": "OTNlZGE5OTJjNWQwYzc2NDI5ZGE5MDg3ZTNjNmNkYTY0ZWZhZDVhNDBkZTc1ZTNiMmQ0MjQ0OThlNTFjNTQyMQ",
    "scope": null,
    "token_type": "bearer"
}
```
