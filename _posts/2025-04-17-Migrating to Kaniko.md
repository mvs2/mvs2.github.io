---
title: "Migrating to Kaniko for Secure CI/CD Image Builds"
date: 2025-04-17
categories:
  - CI/CD
  - DevOps
  - Containers

tags:
  - GitLab
  - Kaniko
  - Security
  - CI/CD
  - Docker
  - Automation
---

We recently transitioned a production pipeline from using Docker-in-Docker (DinD) to [Kaniko](https://github.com/GoogleContainerTools/kaniko), primarily for security and compliance reasons. Our CI/CD system is GitLab, and our internal DevOps team mandated a move away from DinD due to the elevated privileges and potential for container breakout.

Kaniko builds container images in userspace and doesn't require privileged access, which made it a solid replacement. However, switching wasn't completely plug-and-play.

## Key Wins

- **Security**: No need to run the CI pipeline with `--privileged`, greatly reducing risk.
- **Speed**: With cached layers and registry-side cache optimization, build times ended up comparable.
- **Auditability**: Because we dynamically generate our Dockerfiles during the pipeline run, we avoid relying on outdated static images.
- **Simplified Maintenance**: We stopped using `.tar.gz` Galaxy collections and instead built `requirements.yml` into the image cleanly.

## A Real Fix We Had to Make

One common sticking point was unsupported Dockerfile syntax. Kaniko doesn't support experimental Docker features like `RUN --mount=type=cache`, which we had been using in local Docker builds.

**Original (not Kaniko-compatible):**

```dockerfile
RUN --mount=type=cache,target=/root/.cache \
    pip install -r requirements.txt

```

Modified for Kaniko:
```dockerFile
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
```
RUN pip install --no-cache-dir -r requirements.txt

While this introduced slightly more image bloat, it provided reproducibility and compatibility within our security constraints. Other changes included installing Galaxy collections directly in the Dockerfile and eliminating manual downloads of .tar.gz collections.
Prompt Engineering as a Tool

On more than one occasion, we used prompt engineering with ChatGPT to unblock tricky parts of the migration. Whether it was decoding obscure Kaniko error logs, rewriting Dockerfile logic, or troubleshooting GitLab pipeline variables, AI-assisted problem-solving gave us the momentum we needed to stay on track.
Lessons Learned:
- Kaniko required line-by-line reviews for Dockerfile compatibility.
- Dynamically generating Dockerfiles in the pipeline helped avoid reliance on outdated base images
- ansible-runner was skipped in favor of explicit package installation.
- Debugging Kaniko builds required additional echo logging and trial/error.
- Using requirements.txt, requirements.yml, and bindep.txt gave us consistent, transparent builds.

## Final Thoughts

The end result is a secure, repeatable image build process that stays within policy and doesn’t rely on elevated privileges or Docker sidecars. The work took time but was ultimately worth it. Now we’re helping other teams adapt the pattern.

If you’re making a similar move or need a sanity check, feel free to reach out.