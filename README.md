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
utilize the phpcs-pre-commit script in a non-restrictive way.

```drupal-sniff``` is a wrapper around phpcs-pre-commit make it more
universal and it allows the user to still approve the status.

```phpcs-pre-commit-config``` to use Drupal rule configuration and to
filter by Drupal-ish file extensions.

Getting started
---------------
Replace ```git-hooks/phpcs-pre-commit/config``` with ```phpcs-pre-commit-config```.
Make a symlink from the cloned repository to ```$HOME/.devtools``` and add the
```bashrc-snippet``` to your .bashrc. Copy or symlink the ```pre-commit```
script to all of your GIT repositories where you want automatic PHP syntax
checking.
