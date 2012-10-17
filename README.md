# rnotify

`rnotify` provides a way to have notifications sent back to a local
OS X machine while working on a remote server.

While working on a remote Linux or Unix server via an SSH connection,
there's often no easy way for processes on the server to send
notifications back to the user's local machine.  `rnotify` solves
this by providing a pair of scripts that work together to allow
notifications from the server to be displayed in Notification Center.

## Installation

### On the client:

1. Install [Terminal Notifier](https://github.com/alloy/terminal-notifier)
2. Set up `$HOME/.rnotify` with a port and password (shared between
   server and client) and the path to Terminal Notifier:

        port: 12345
        password: reallyreallysecure
        notifier: /Applications/terminal-notifier.app/Contents/MacOS/terminal-notifier

3. Copy this file to the server.

4. Create an SSH tunnel to the server:

        ssh server -R12345:localhost:12345

5. Run `rnotify`

### On the server:

1. Make sure the `$HOME/.rnotify` you copied across from the client is
   in place and `chmod`ed 600.
2. To send a message to the client, run `whine MESSAGE`

