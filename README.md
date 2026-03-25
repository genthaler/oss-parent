# OSS Parent

A Maven pom project to store some commonly used configuration, especially for publishing Java OSS artifacts.

Some of the configuration will be inherited by including this project as a parent, some will need to be copied.

Please see the [Project Page](http://genthaler.github.io/oss-parent).

There's also the [Issues](https://github.com/genthaler/oss-parent/issues) page.

## Releasing

This project is configured for Sonatype Central Portal publishing via the `central-release` Maven profile.

Prerequisites:

- A Sonatype Central Portal account with access to the `com.github.genthaler` namespace
- A Central Portal user token stored in `~/.m2/settings.xml` under server id `central`
- A local GPG secret key available to `gpg`

Example `~/.m2/settings.xml` entry:

```xml
<settings>
  <servers>
    <server>
      <id>central</id>
      <username>YOUR_PORTAL_TOKEN_USERNAME</username>
      <password>YOUR_PORTAL_TOKEN_PASSWORD</password>
    </server>
  </servers>
</settings>
```

Release command:

```bash
mvn -Pcentral-release -Dgpg.keyname=YOUR_GPG_KEY_FINGERPRINT deploy
```

Snapshots are published to Sonatype Central snapshots. Non-snapshot releases are published through the Central Portal publish flow.

You can discover the local fingerprint to use with:

```bash
gpg --list-secret-keys --keyid-format LONG
```
