# Pusher

## Purpose

### What is this?

This is a collection of bash scripts to enhance your deployment process to a server that supports either Git Push (WP Engine) or rsync (any server that offers SSH access).

Specifically if you are using a deployment service like Buddy or Deploybot to centralize your deployments and you have it connected to WP Engine, you probably use SFTP to get the files to the server.

This is extremely slow and can cause extensive periods of downtime while the system pushes each file up. 

Unfortunately WP Engine's git push is not really an option for teams and agencies (due to lack of a central, visible and consistent deployment process).

This is where Pusher comes into play.

Pusher is a bridge between Buddy/Deploybot and WP Engine's git push. You set it up as a standalone server that serves as the central point for the git push to WP Engine.

### How it works
On the ZWP server, for the specific project and environment, there are two directories (each directory is a git repository):
- Repo
- Deploy

The `Repo` directory is synced with the origin/canonical repo and this is where things kick off for a deploy.

The `Deploy` directory is synced with the WP Engine environment and only contains build commits (which includes things like vendor files and compiled assets). Each deploy creates a new commit and the diff between the last commit and the new commit is what gets pushed to WP Engine.