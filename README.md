# matrix-send
A script to send a message to a Matrix room.

---

**Syntax:** `matrix-send <message> <room id>`

**For example:** `matrix-send "Hello world\!" aBcDeFgHiJkLmNoP:matrix.org`

---

`matrix-send` is a simple script to interact with a Matrix homeserver in order to send a message to a room.

If you don't understand, `matrix-send` is an oversimplified Matrix client.

It is mainly designed for automation. I use it on my Matrix room.

`matrix-send` doesn't have support for end-to-end encryption, and never will.

## Get started

In order to start using `matrix-send` you need a config file. To copy the configuration to .config, clone this repository and type:

    make config

The configuration has now been copied to ~/.config, so open the file ~/.config/matrix-send.conf with your favourite text editor.

You will see three "directives"; configuration options that take an argument. Directives' syntax look like so:

    Directive Argument

Modify the `Homeserver` directive to match your homeserver's Matrix URL. If you're using matrix.org you can leave it as default.

If you're not using matrix.org, one way you can find your homeserver's Matrix URL is by typing your homeserver's address into Element. Click Continue, and hover over your homeserver's address that popped up. The Matrix URL should be showing.

Set the `Username` directive to your username, and the `Password` directive to your password.

You might not want to put your password in plain text, so you could do something like this instead:

    Password $(gpg -d ~/.matrix_pass.gpg)

This will open `gpg` to decrypt a file with your password inside. You will need to set this up first.

After you've finished changing these, your configuration should look like this (without the comments):

    Homeserver matrix-client.matrix.org  # or your homeserver
    Username jeremy  # or your name
    Password mysupersecurepassword  # or your password

After you have these three directives set, you're ready to start.

Additional directives can be found in [config.md](https://github.com/jtbx/matrix-send/blob/main/config.md).

---

To install, run `sudo make install` in the cloned repository's directory.

    sudo make install

Now, using your Matrix client, make a room, and find the Room ID. On Element, right click your room, and click Advanced. Your Room ID is under "Internal Room ID".

Your Room ID will start with a '!'. Remove this symbol from the start and copy the new ID.

To send a message to your chosen room, type `matrix-send` followed by your message (in speech marks) and then your Room ID. For example:

    matrix-send "Hi\!" asdfasdfasdfasdf:matrix.org

And that will send the message "Hi!" to the Matrix room asdfasdfasdfasdf:matrix.org.

Also, if you type exclamation marks '!' in a message, some shells misinterpret that as an event. To fix this, I put a backslash `\` before the exclamation mark.
