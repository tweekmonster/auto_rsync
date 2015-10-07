# auto_rsync
Automatically rsync a directory watched by [fswatch](https://github.com/emcrisostomo/fswatch) on OS X

Reasons you would want to use this:

- You are using a Mac.
- You want your files to magically appear on a server after you save them.
- Your project produces a copious amount of data that your computer can't
  handle, but it isn't practical to work on the remote server that can handle
  it. You also don't want to make a bunch of tiny commits that showcases your
  battle with dyslexia.
- The cloud confuses you.
- You are an awful person that edits files through an SFTP client and you want
  your colleagues to shut the hell up about it.
- You are lazy and think rsync is tedious to setup.

## Installation

- Install [fswatch](https://github.com/emcrisostomo/fswatch#getting-fswatch)
- Put the `auto_rsync` script somewhere in your `$PATH`.

## Usage

If you want to work in `~/Development/project` and you want it to be synced to
the remote server `example.com` at `/srv/project`, you would run:

`auto_rsync -n my_project -r "example.com:/srv/project" -w ~/Development/project`

When you modify a file in your local project directory, it will be rsync'd to
the remote server and a noise will be made to let you know it happened. After
a few weeks of this happening you will develop a Pavlovian response to this
noise. Try to make the most out of it.

## Notes

- `-h` will show you some extra options.
- auto_rsync will generate launchd plist files and load itself as a Launch
  Agent. It will be stored in `~/Library/LaunchAgents`. If you rename, move, or
  delete the auto_rsync script, the magic will disappear and all that will be
  left is a pile of error messages.
- auto_rsync will automatically exclude `.git` from being sync'd to the server.
  You shouldn't be making commits from the remote which will be overwritten
  anyways.
- The local directory being rsync'd will always have a trailing slash appended
  to it. If you know what this means and you don't like it, you should be a
  skilled enough smarty pants to tweak the script.
