---
title: gitlab-runner
date: 2023-08-23 11:28:43
tags: server
---

```bash
docker run --rm -v /srv/gitlab-runner/config:/etc/gitlab-runner gitlab/gitlab-runner register \
--non-interactive \
--executor "docker" \
--docker-image alpine:latest \
--url "http://andrewandbecky.top:30000/" \
--registration-token "YR6LxsAsd6VF9X8CbLz2" \
--description "first-register-runner" \
--tag-list "docker,shared" \
--run-untagged="true" \
--locked="false" \
--access-level="not_protected" 

```

