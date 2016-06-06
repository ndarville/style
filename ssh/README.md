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

Testing
-------
Test your configuration with [Filippo Valsorda’s tool][tool] by typing `ssh whoami.filippo.io` in your terminal. If you aren’t identified, you’ve set up your configuration correctly
