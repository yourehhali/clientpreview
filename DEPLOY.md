# Temporary Dokploy preview

This folder is a static HTML/CSS site. The included Dockerfile serves it with
Nginx; no Node.js build step is required.

## Dokploy setup

1. Push this folder to a Git repository that Dokploy can access.
2. In Dokploy, create an application from that repository and select the branch
   you want to preview.
3. Set the application base directory to `Refonte` if this folder is inside a
   larger repository. If the repository root is this folder, leave the base
   directory at its default.
4. Choose Dockerfile as the build type, use `Dockerfile`, and set the exposed
   container port to `80`.
5. Add a preview domain, enable HTTPS, and deploy.

The Nginx configuration sends `X-Robots-Tag: noindex, nofollow, noarchive` to
discourage search indexing. This does not restrict access. If the preview
should be private, enable authentication at the Dokploy/proxy layer before
sharing the URL.

Remove the preview application from Dokploy when the review is complete.
