Adding Emails to travis-jobs to be informed about missed builds.

Problem:
    Emails are stored in plain text within .travis.yml


Info:
    General encryption scheme
        https://docs.travis-ci.com/user/encryption-keys/#detailed-discussion
        https://docs.travis-ci.com/user/notifications#configuring-email-notifications

    PIP-Package
        https://pypi.org/project/travis-encrypt/

Comment:
    There is also an official ruby version for encryption.

###########################################################################

1. install pip package
    $ pip install --user travis-encrypt

2. display some help
    $ travis-encrypt --help

3. create notification-entry in .travis.yml
    $ echo ""                             >> .travis.yml
    $ echo "notifications:"               >> .travis.yml
    $ echo "  email:"                     >> .travis.yml

4. add secure-entry for emails
    $ pwd=$(travis-encrypt --password <email> <username> <repository> | \
      grep secure)
        # <email>      ... email-address to be encrypted, e.g. mail@url.com
        # <username>   ... username at github.com
        # <repository> ... repository name at github.com
    $ echo "    - $pwd"                   >> .travis.yml

    # repeat step 4 for each email to be added

5. check .travis.yml
    $ cat .travis.yml

6. done :-)
