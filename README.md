Drupal Code Inspect Scripts
===========================

Collected configuration and scripts to do 2-level static code analysis for
Drupal GIT repositories in an automated way.

Clone with --recursive to initialize the submodule.

Dependencies:

- http://pear.php.net/package/PHP_CodeSniffer
- http://drupal.org/project/coder module's coder_sniffer configuration
   is added to CodeSniffer

Structure explained
-------------------

```pre-commit``` PHP script that we can use as the real pre-commit hook.
GIT does not have global hooks, so you might want add it to every GIT
repository.

```bashrc-snippet``` shows some GIT command aliases and a possible way to
utilize the phpcs-pre-commit script in a non-restrictive way via the
```gm``` alias. To avoid the costly execution of PHP_Sniffer, it is
possible not use the alias simply. It makes sense for modifying
contrib modules, for legacy codebase and for extremely large commits.

```drupal-sniff``` is a wrapper around phpcs-pre-commit make it more
universal and it allows the user to still approve the status.

```phpcs-pre-commit-config``` to use Drupal rule configuration and to
filter by Drupal-ish file extensions.

Getting started
---------------
Make sure the dependencies are installed and configured.
Replace ```git-hooks/phpcs-pre-commit/config``` with ```phpcs-pre-commit-config```.
Make a symlink from the cloned repository to ```$HOME/.devtools``` and add the
```bashrc-snippet``` to your .bashrc. Copy or symlink the ```pre-commit```
script to all of your GIT repositories where you want automatic PHP syntax
checking.

Now make your first inspected commit:

```ga whatever.module```

```gm "whatever: some superb quality code added, nothing more"```

Fine-tuning
-----------
If for any reason, you'd not want to break the commit process, merely to print
out the result of the inspection, in .bashrc, you can change
export DR_CODEINSPECT_INTERACTIVE=1
to
export DR_CODEINSPECT_INTERACTIVE=0

This way, the output of the sniffer is at the stdout and you may review it.
