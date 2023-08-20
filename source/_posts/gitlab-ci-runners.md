---
title: gitlab_ci runners
date: 2022-08-18 18:01:14
tags: server
---

# Download the binary for your system
```bash
sudo curl -L --output /usr/local/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64
```
# Give it permissions to execute

```bash
sudo chmod +x /usr/local/bin/gitlab-runner
```

# Create a GitLab CI user
```bash
sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash
```
# Install and run as service
```bash
sudo gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
sudo gitlab-runner start
```

```bash
sudo gitlab-runner register --url http://andrewandbecky.top:30000/ --registration-token $REGISTRATION_TOKEN
```