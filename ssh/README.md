SSH
===
SSH comes with a big privacy hole by default. To fix that

* Edit `~/.ssh/config`
* Include the following

    ```
    Host github.com
      PubkeyAuthentication yes
      IdentityFile ~/.ssh/id_rsa # Or whatever you named your key
    Host *
      UseRoaming no
      PubkeyAuthentication no
      IdentitiesOnly yes
    ```

Remember to put `github.com` before `*`, if you don’t want to get an error.

Keychains and remembering passwords
-----------------------------------
Two things have been changed in a recent macOS update.

The keychain dialogue is gone:

> Prior to macOS Sierra, ssh would present a dialog asking for your passphrase and would offer the option to store it into the keychain. This UI was deprecated some time ago and has been removed.

And ssh-agent doesn't load keys by default, which may be the reason you keep getting prompts to enter your password:

> OpenSSH will no longer load keys into ssh-agent automatically. This aligns the macOS behavior with that of the upstream OpenSSH project.

You can re-enable these behaviours by following the instructions in the [technical note][].

Testing
-------
Test your configuration with [Filippo Valsorda’s tool][tool] by typing `ssh whoami.filippo.io` in your terminal. If you aren’t identified, you’ve set up your configuration correctly


[tool]: https://blog.filippo.io/ssh-whoami-filippo-io/
[technical note]: https://developer.apple.com/library/content/technotes/tn2449/_index.html#//apple_ref/doc/uid/DTS40017589
