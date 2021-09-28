# Updating the Site
The VNOJ is under active development, so occasionally you may wish to update. This is a fairly simple process.

!>  The VNOJ development team makes no commitment to backwards compatibility. It's possible that an update migration
    might add, change, or delete data from your install. Always back up before attempting an update. <br> <br>
    If in doubt, feel free to [contact us on Discord](https://discord.gg/TDyYVyd).

First, switch to the site virtual environment, and pull the latest changes.

```
(vnojsite) $ git pull origin master
```

It's possible dependencies have changed since the last time you updated, so install any missing ones now.

```
(vnojsite) $ pip3 install -r requirements.txt
```

The database schema might also have changed, so update it.

```
(vnojsite) $ python3 manage.py migrate
(vnojsite) $ python3 manage.py check
```

Finally, update any static files that may have been changed.

```
(vnojsite) $ ./make_style.sh
(vnojsite) $ python3 manage.py collectstatic
(vnojsite) $ python3 manage.py compilemessages
(vnojsite) $ python3 manage.py compilejsi18n
```

That's it! You may wish to condense the above steps into a script you can run at a later time.
