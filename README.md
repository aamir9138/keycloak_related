## Backup and restore in keycloak running on docker container

### Backup

1. go to docker CLI.
2. change to the folder `opt/keycloak/bin`
3. here we have keycloak shell script. we will use this script to do the export
4. Then run this command `./kc.sh export --dir /opt/keycloak/tmp/allusers.json --users same_file`.
5. Then go to the folder `cd /opt/keycloak/tmp`
6. `ls` you will see the file `allusers.json`.
7. now we need to bring this out of the docker container.
8. for that we need to copy it.
9. `docker ps` in terminal
10. `docker cp <containerId>:<source path i.e /opt/keycloak/tmp/allusers.json> <destination path>`

### Restore

1. in `users` delete all users
2. to import go to `realm settings`. on top right `partial import` select the users from the `allusers.json` folder and import it.

### Readme file in themes folder

Themes are used to configure the look and feel of login pages and the account management console.

Custom themes packaged in a JAR file should be deployed to the `${kc.home.dir}/providers` directory. After that, run
the `build` command to install them before starting the server.

You are also able to create your custom themes in this directory, directly. Themes within this directory do not require
the `build` command to be installed.

When running the server in development mode using `start-dev`, themes are not cached so that you can easily work on them without a need to restart
the server when making changes.

See the theme section in the [Server Developer Guide](https://www.keycloak.org/docs/latest/server_development/#_themes) for more details about how to create custom themes.

## Overriding the built-in templates

While creating custom themes, especially when overriding templates, it may be useful to use the built-in templates as
a reference. These can be found within the theme directory of `../lib/lib/main/org.keycloak.keycloak-themes-21.0.1.jar`, which can be opened using any
standard ZIP archive tool.
