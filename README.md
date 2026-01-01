Guacamole (Auto-Updating Fork)
====

**Forked from:** [jason-bean/docker-guacamole](https://github.com/jason-bean/docker-guacamole)

This fork automatically builds and releases new versions of Guacamole whenever Apache releases updates. The original repository is no longer actively maintained, so this fork ensures you always have access to the latest Guacamole versions.

Dockerfile for Apache Guacamole with embedded MariaDB (MySQL) and LDAP authentication.

Guacamole is a clientless remote desktop gateway. It supports standard protocols like VNC and RDP.

## What's Different in This Fork?

- **Automatic Updates**: GitHub Actions checks daily for new Guacamole releases
- **Auto-Build**: Automatically builds and publishes new Docker images when updates are available
- **GitHub Container Registry**: Images pushed to GHCR instead of Docker Hub
- **Version Tracking**: Git tags and GitHub releases for each version
- **Always Current**: No more waiting for manual updates

---
Authors
===

**This Fork:** Skylord123 (auto-updating fork for continuous Guacamole updates)

**Original Work:**
- Based on the work of Zuhkov <zuhkov@gmail.com> and aptalca
- Updated by Jason Bean to the latest version of guacamole (no longer maintained)

---
Building
===

Build from docker file:

```bash
git clone https://github.com/YOUR-USERNAME/docker-guacamole.git
cd docker-guacamole
docker build -t guacamole .
```

Or pull the latest auto-built image from GitHub Container Registry:

```bash
docker pull ghcr.io/YOUR-USERNAME/docker-guacamole:latest
```

**Note:** Replace `YOUR-USERNAME` with your GitHub username. Images are automatically built and published when new Guacamole versions are released.

---
Running
===

Create your guacamole config directory (which will contain both the properties file and the database).

To run using MariaDB for user authentication, launch with the following:

```bash
docker run -d \
  -v /your-config-location:/config \
  -p 8080:8080 \
  -e OPT_MYSQL=Y \
  ghcr.io/YOUR-USERNAME/docker-guacamole:latest
```

Browse to `http://your-host-ip:8080` and login with user and password `guacadmin`

**Note:** Replace `YOUR-USERNAME` with your GitHub username, or use your own built image name.

---
Automated Updates
===

This fork includes automated GitHub Actions workflows that:

1. Check daily for new Apache Guacamole releases
2. Automatically build and push new Docker images when updates are detected
3. Create git tags and GitHub releases for version tracking
4. Keep your Guacamole deployment always up-to-date

See the [workflow setup documentation](WORKFLOW_SETUP.md) for configuration details.

---
Credits
===

Apache Guacamole copyright The Apache Software Foundation, Licensed under the Apache License, Version 2.0.

This docker image is built upon the baseimage made by phusion.

**Fork Chain:**
1. Original work by hall/guacamole
2. Forked by Zuhkov/docker-containers
3. Forked by aptalca/docker-containers
4. Forked by jason-bean/docker-guacamole (no longer maintained)
5. This fork: Auto-updating version with GitHub Actions automation

**Why This Fork Exists:**

The upstream repository (jason-bean/docker-guacamole) is no longer actively maintained. This fork ensures continuous updates by automatically detecting and building new Guacamole releases as they become available from Apache.