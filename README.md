# KCC Travis CI Documentation

<br>

##### Contents:

1. [.travis.yml breakdown](https://github.com/wdzajicek/travis-docs/#travisyml-breakdown)
2. [Encrypting Notification Emails](https://github.com/wdzajicek/travis-docs/#encrypting-notification-emails)
3. [Encrypting and Calling Environment Variables](https://github.com/wdzajicek/travis-docs/#encrypting-and-calling-environment-variables)

<br>

## .travis.yml breakdown:

    language: ruby
    rvm:
    - 2.5.0
    sudo: false
    addons:
    apt:
      packages:
      - ncftp

### before_install:

gemfile.sh Creates the Gemfile for travis to use. Install npm v6.1.0:

    before_install:
    - chmod +x _scripts/gemfile.sh
    - _scripts/gemfile.sh
    - npm i -g npm@6.1.0

### install:

npm install, bundle install, jekyll gem installs:

    install:
    - npm install
    - bundle install
    - gem install jekyll
    - gem install jekyll-feed
    - gem install jekyll-sitemap

### Defining Branches

With CloudCannon's publishing workflow, the publish branch is the only one  that gets built.

    branches:
    only:
    - publish

### Notification settings with encrypted emails

#### See [Encrypting Notification Emails](https://github.com/wdzajicek/travis-docs/#encrypting-notification-emails)

    notifications:
    email:
      recipients:
      - secure: gK8tke5tvf+kn0QCQz8mBdEKDcxgtOKHSkS55k6GGSyGOSBh0wlWVYP0S3pgmJ9zGu6y6y0gBkwhA12t3SbhMXEPeKUnAdBJrss+MJdHk6Z3mhb9BhO/kyKxhkS+oTYrTBXndINEVa0JKrpwVcE3s9b+PWn7B59jKWrcXiZ4a7BMgfyXM+pKi+sJwRnRGBDsa2kbBz1S7slkb1P7t8xN+/JTM+vArHn0Pb0cXmfeW4/9llqTMMHkuscULDrcnkhgQuHWXi4SX9kk42dj9+ga2tI1vkfSuUg0m3BKc3N+wNkPt9NJoXXEJbkfbrOkKKJ8tbKHooi1bNbcwlI9Axmu5QTWQkwCAEtvbbroXch2zzEIg3gOuaFxbCwRjEUEkHP5jWLgIA4gH70ZRgRLEL31AkoRXXgZMjKvHV/IhonGzAz25jdRPf6uReMGnjwjyDDLTSSacI0yAwSI8No4MDMs3VuXRP9+6pbg01bwOc1DijTbpfu0zKHuOm2jSTErZdhNPDA2m673lbyt4AbqGqXWigWFAPLnB5SBNS63O7IluYu8SwS0rh6oQppsJF6RNB7EQ4VSuvYYJ2a0NZbT7QZ47hJrbkNFfBsa+vBXKYtZZ2gaBqGGkGNA7VGhob2Hd8Y0GKl0gEBRH7UgpxRhpw3IMwE/1Csn8mYxKhlEXm5wi/c=
      - secure: ThPSgqgVNLGilY8sUdKvEQmGuQocuoVuoRYdjaH6pojpsREXlNb5Yv8MlWLWRTY+JvhZcFAmE+B4e5lUT6PCgKoeidM94tzhuRj+wI3c88Y+HHe6P1p+hnQH5aVGNQTchxLF3Bdio412d2KLqhvO1+fWGLIsw12EuoMezGsuCfOCkR3fR2G7dn7IKiJEtwluee4eY59bPI90ucYRTJdZAHYg13JsBWo+D40hpuPYnqJNAk8uM9XQVGoYU4VWclFm1gfok3hzhIgncgxdIyuDy73f6WZ9hnvv73eo0FJUrn9CPAve+fNhOElpqtBCZlSU7Axe8NyDZZDcXAvakLqCPWmlwgu+UuwoVPaYQNyrzSIePT18tocSa4UYBtXu46kryT4g0oD6CQmZ5tcXcqGQi3K+2OmJjYvy9TeCde3YERRVX8JEudTBkNLccJaSpxr6grIP/+LIyBsnAbKFeq2yrXYCnRmA1iyD603vaed8y37uufH3WGAjZgRVN5dAo0P5feJ1EH9GuTH1YXw44yKcymYtBNX+sgm0MBZTZMCw2metm+JB6Jc3ji4qGxd3Fpe2CtcOLasPZzU0ifvUTpiqaA9/LqeHRev2i/cXxaxvXdbpRWpVzkVKfFkSFDjqQqJUZ2Z52ATD0/qJ/k20+dC2X318HPtI60AKyfUs61ydaho=
      - secure: IOJLMgek9M6Irp3WsTyuDTGzia29Vs0zWzqNg6kGS2oqQAwwdiVATND+2OwYt+zXieS6/0qJm5gq8gQbFohlmqDQ6utLuugvKi6B22DT5yQGzkeMCr5wNlrag11jFS1uULPhRApwCz5ThnYY33Oiaac4csCBNZ5YMpb4pIQugSBkyFob2oMMZlegL/2yXOtjhLkYJxQvJ5D2zpl+3oQFgmHo7n6XY0c0lJY2bFs9ehY2aXGiTw1WheLDiMMoraCSXxSrYskPOzp7c6ywg1CsdnZAy3IxJaCWEDCBEGmgh2Ljnlh0lTeWYIgow4L8TWOYYrQeU8IolfHRlx1hgCTKmildsyVrTmtLbuKVaUYzvYnuZmlHWF4d+OEkW1RCTmx3gb7iQUEZu28QsCHOgFRZPpI8Um+1ApXM3JcJI4r7zF+qduyLkRR6mdYHTDplhs/nttZYlsWGOkQnqIiJWmPQUeYgSuQgz+3sSnVmA8kNEcPlolH7U+299aL7yAw9z/khNLhErsAYqUI/35E3kecIZeLVFfCKFF1pTQedNCxhxu3lgHNROLu0Q7nXxgrpC2OGBoaR9dwvkdS9MW2Lnh8rK9lGeMvcRjhJsXfkhyJaPgJWa99O9vNUbLK9FHU/qlrM1cvhxd+Ch8QRat3PF3wv+sPZFEYjhb32pVCXukl7I0w=
      on_success: never
      on_failure: always

### before_script:

##### install Gulp.js

    before_script:
    - npm install -g gulp-cli

### script:

##### The build script: `$ gulp travis`

the "travis" gulp task creates a production build of the site (production uses asset minification i.e. images, JS, & CSS minified/uglified/compressed.

    script:
    - chmod +x _scripts/build.sh
    - _scripts/build.sh

### after_succes:





##### Deploy!

deploy.sh runs two gulp tasks: cleanFTP and newerFTP. cleanFTP deletes everything from the server folder and newerFTP copies the new passing site build to the server.

deploy.sh also issues a 15 second delay via `$ sleep 15` between the cleanFTP and newerFTP tasks.

    after_success:
    - chmod +x _scripts/deploy.sh
    - _scripts/deploy.sh

### Global Environment Variables

#### See [Encrypting and Calling Environment Variables](https://github.com/wdzajicek/travis-docs/#encrypting-and-calling-environment-variables).

    env:
    global:
    - secure: UXS4WAMKaUFb/WIv0bam2q7T36hNXKTgUVeWSSISyxkU+Rvd5rDpkLNNC21N7NqNBF1DHUPhBMpwoYKjvTVbUfgsF7bBPLOTPAvz9Fyl7kJjkVTzk+usqFOxm5vYiJrogBro1BH7ZJKMmEqrzYIJtw+2KIvE826E6kxMAVyOHMeRiPXHH8fz2mNoE6D9hYgAL2pOOPFZ6VKQOHWqWSimXGEPH0M2vMp8MO5NFlu3rLJs/30LdeUM7evOOzl1iftLYqNgt9H56jlY0ztjYWOsSr6tIYfpWyKcSgSA5ZnAnP3MVDS3/ym5xOfSe7vNfDuGfbBKYBx9NKlwL6MVAFMsqJyBIz14wjvBT1cl6YHh8o+2su3gUvsn6uDIDk7m2T3WPXylN9/+jNvvzN2Cvi2QeSi/m/jZKBfrH6bL+4KAklpgRl69oek891Zfwln1Yu87bWXsHuT7nXcw+gGHg4xifbQu95RRlMYyhTnMZKC0UwTBwUK7uLsH3/GnwLh9Mzi8Hg4NLMMZIZ5kn2eIeb691Y84she/ZwNuvuHM6ThFWm+L9vT7CBkZP5oKJRRVOvgunv0uh1UpybSsdcyLnyx1mbEW/8X0q3zTvSa2euUsFHkBlfNefr4Q26b+93pS5di6ufpGRBuVrBQKHZdsjJD6FVPZg2oOI1vCgyZsWZO0DM4=
    - secure: J5PE3reG8l3IOyFKxqmRpVdiGwa5Uc8uo5ksJptBDB/8Bju/Y+mlbZy6ELIE+nQcFMo0WqBx59qY5h8PPG2NeLBlpkgPWiKecxiOBIHR4WwPV2EFcBvcFwM++k4YcQpB/bghZP5OzzNO1psOnoNM/V3DNgsy1V8BmsnmqpkF1Y3aQZfsIKwpITFaUFhX/9k29l5dQqS4cWJKktUjei3HNhYB6zst2K5cWxqagTbB2PjPWTIw1uQzQR4PR1XZ0gPq5R8KpI2Rey4HAucDnesgBxSSgoo3DppHGId8NdXGVh4CxIHowv6PGZtZ5sF/Q7WZcwbSMDstf+ZZ3A4jcJyReadZUsRnE+H+YPrXIS8GwJZ6c0E9s8hN+1lkEog0gzT0sskD4Psv4Yk2NuP+zrNsfxwf9hrNWlOIM2eTF+5LFr5TlwHHKvkByGxfpkePTQBYc1g02EDxzSQnx/nEqL+c0e2lMskT0adTU/lbUkqtsTD4taxAEyZbAseJ0dkIwl4oPSaLwwpMlMcSy7H4SiJzWpI+sU+XNCyg25oDKn3KjcQIzZC5jce1EtgnKY/Ww1FTPI4tPM2r0mq7TnYOI44cH91TiHlMOg/jOBRSmtlhMHcr6Scsy4LegOfAVlj67x+mEvT/GOzbheLS+QtqmU2XFELWS9KHA+N/C6XGkrqXCzE=
    - secure: ldvzd3QRFAcq/dGFwJHG+EUbmTM88HV3Ou7GHkS5rINCCZz1GXGMHJ2Il9SvpMIorEyy//p7qieaFG+3r+L1DpthLQBKEY5GEPlAgKjeduDQ1wjbWjXJ1llc0B39tZmMXu9xNRoLMjLqtvAl/IgUhCCnl4vvCrMJFtXzzA73HNz9XzFRhhaUF+UXPmGGrj+ABX9C4/ODUsZdFLox0kMiR/wjqkf4TDhLPszQuP49H9OQBqdfc9/7QCnLPYt77gPcpo6FLphdnyufCzdNrectGnU2HM7lStVGtP81EjkR04XjKF+XvBbWuk689kTBPNC1f3R1FcRFds7xXnKlAoTxrFO7Zd47K9GxiAUtG2xInbugHYcY/KN9lA0F35FFdbaksVPiMEYPlHMSKqPSJrviG58jGBhZiQXsAKU1psahLZKAayKeAkDAdWS2P42tNzG5817NSFT9DdWnUrGKgimuescXsuJ5E5J0Y9Dqg5tCi3CgKlU9E0pQEWqaILM0ZS5Vx1rvuZiYnTUWqefdVRrWZ3Z0c9itdu8hJOuBzLBVzzzk9eCkhdS+vVo+dMIpt1ecxX2qpRVUWJvxJ19CDgJPQL7pUb3T09MXx5r3atePwMrKcK18WGFV+PuPVYPPmxsjUXIpg4+/M2cRaRypwU+beENvXycO42+7I+nFzlxF6zA=

<br>

<br>

## Encrypting Notification emails

[Page top](https://github.com/wdzajicek/travis-docs/#kcc-travis-ci-documentation)

to encrypt travis variables use the travis gem and login using Github credentials:

    $ gem install travis
    $ travis login            // this will prompt for Github user/password

### Default notification email example in .travis.yml.

This is how standard email notifications are set in .travis.yml without encryption:

    notifications:
    email:
      recipients:
        - <recipient-1>@gmail.com
        - <recipient-2>@gmail.com

### To encrypt an email.

You must be in a local git repository that travis-ci.org has access to.

    $ travis encrypt "<recipient-1>@gmail.com"

Travis will return something like this:

    Please add the following to your .travis.yml file:

      secure: "XDD3KrR1M5Xmg+wlea4y1o14uhIhV78yAUA96SaQT4KKBRXqixQbo+Mme4ghIRlWyuZ35BReL6h/MO2Gr3xJ1TEsmo/7d+aP+OazwJ4weGX7YEQYuE7RGKQt4LIENQVhbJmUspzoZl/bocas+2PaiS8LT4cKJ58l35kFW4fIONPir4M/4xUqJX5kxvUqww7K+ijipJYAcO2ySeFeMbPL5sMxezBaXNg1sG44s/4RmHJ9tpLlnLJc1X1n0OdxrNPI2KpEQWIyTdve7vtUZb7FJ0UefL1ll9C4fojhIp8Fb3IzS5W3hLiBTys56OvhEcgp0SejCrTD9guxrwJxrZPy5i2T4Ahjg2H7ej7QsvBqh3kIfxKzKFLVvp9jKfiE0zI+lTHWhKcGXHRZTP5qLtAgEaVyKiEVd1wgwrbnv+JPLRT7Gr4CIb9BtTZjPyqAErC1uVcvapvzR19EoIAC+/Z5cyQlkZkXeLx+5c1675WoHae92MzE8xr2lf5t9b9CVk1Hdd47qaoRz172ikddcWOO242v6orxh0QT0ar65L9DqMQ+7IZP+95wn/fd97Et7zMLpkVrzaj8kSUDAi2QvhhSunBCwToe8czAUwZQ160BTicCIZ8LZpjeqZXTvEBGdqgT3Df7dNrsbODY/XiVLmpIHRaUPlcJWiwIjD2WCuGqMAg="

### Copy and paste into .travis.yml

Replace `- <recipient-1>@gmail.com` with `- secure: <long encrypted string>`:

    notifications:
    email:
      recipients:
        - secure: "XDD3KrR1M5Xmg+wlea4y1o14uhIhV78yAUA96SaQT4KKBRXqixQbo+Mme4ghIRlWyuZ35BReL6h/MO2Gr3xJ1TEsmo/7d+aP+OazwJ4weGX7YEQYuE7RGKQt4LIENQVhbJmUspzoZl/bocas+2PaiS8LT4cKJ58l35kFW4fIONPir4M/4xUqJX5kxvUqww7K+ijipJYAcO2ySeFeMbPL5sMxezBaXNg1sG44s/4RmHJ9tpLlnLJc1X1n0OdxrNPI2KpEQWIyTdve7vtUZb7FJ0UefL1ll9C4fojhIp8Fb3IzS5W3hLiBTys56OvhEcgp0SejCrTD9guxrwJxrZPy5i2T4Ahjg2H7ej7QsvBqh3kIfxKzKFLVvp9jKfiE0zI+lTHWhKcGXHRZTP5qLtAgEaVyKiEVd1wgwrbnv+JPLRT7Gr4CIb9BtTZjPyqAErC1uVcvapvzR19EoIAC+/Z5cyQlkZkXeLx+5c1675WoHae92MzE8xr2lf5t9b9CVk1Hdd47qaoRz172ikddcWOO242v6orxh0QT0ar65L9DqMQ+7IZP+95wn/fd97Et7zMLpkVrzaj8kSUDAi2QvhhSunBCwToe8czAUwZQ160BTicCIZ8LZpjeqZXTvEBGdqgT3Df7dNrsbODY/XiVLmpIHRaUPlcJWiwIjD2WCuGqMAg="
        - <recipient-2>@gmail.com

#### Travis can now decrypt your email and send you notifications without making your email publicly available.

<br>

<br>

## Encrypting and Calling Environment Variables

[Page top](https://github.com/wdzajicek/travis-docs/#kcc-travis-ci-documentation)

to encrypt travis variables use the travis gem and login using Github credentials. You must be in a local git repository that travis-ci.org has access to.

    $ gem install travis
    $ travis login            // this will prompt for Github user/password

#### Encrypting Environment Variables and writing to .travis.yml at the same time:

If I wanted to put an FTP username and password in my .travis.yml as an encrypted environment variable. The `--add` flag writes the encrypted string to your .travis.yml file:

    $ travis encrypt FTP_USER="<example user>" --add
    $ travis encrypt FTP_PASSWORD="<example password>" --add

Travis now has access to those encrypted variables. For example you could call the FTP user and password in your deploy script use the dollar-sign followed by the variables name (e.g. `$FTP_USER`)

Example in a deploy.sh file used by travis:


    $ gulp deploy --user $FTP_USER --password $FTP_PASSWORD

<br>

[Page top](https://github.com/wdzajicek/travis-docs/#kcc-travis-ci-documentation)
