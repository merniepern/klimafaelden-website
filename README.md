# Klimafaelden website

Welcome to the GitHub repository of the Klimafaelden website.

## Getting started

If you are a new developer and wish to start contributing to this project, please read this README **to its end** *before* starting production. 

It will give an introduction to the infrastructure as well as a step-by-step guide on how to set up a local development environment, easily copy the latest version of the website from production to your local environment, make changes locally and publish your changes to the live website.

### Setting up a local development environment

It is highly recommended to set up a local development environment (LDE) when making substantial changes to the website, especially when it involves changes to the theme or changing the entire theme.

As the process of setting up an LDE will differ significantly depending on your choice of operating system, no exhaustive description can be given here.

Generally speaking, it is necessary to set up a combination of an operating system, a webserver, a relational database and PHP to create a local dev. environment. For example Linux, Apache, MariaDB and PHP (LAMP Stack). More information in the resources below.

**Resources**

* [Guide to set up a LAMP stack on ArchLinux](https://computingforgeeks.com/how-setup-wordpress-on-arch-linux/)
* [ArchWiki wordpress page](https://wiki.archlinux.org/title/Wordpress#Installation), which includes a very good guide on how to set up a local development environment.
* [Guide to set up a WAMP stack on Windows.](https://www.wpbeginner.com/wp-tutorials/how-to-install-wordpress-on-your-windows-computer-using-wamp/) The creator of this repository did not follow this guide, so quality can not be guaranteed
* [Guide to set up a MAMP stack on MacOS.](https://www.wpbeginner.com/wp-tutorials/how-to-install-wordpress-locally-on-mac-using-mamp/) Again, quality can not be assured, for the same reason.

### Copying the current production website to a local environment

The Wordpress Duplicator plug-in makes it very easy to copy a Wordpress website from one environment to another environment, hence its recommended to use this after having set up your LDE. 

Even though the Duplicator plug-in *should* override any exisiting Wordpress installation in the folder it is set to run, it is still recommended **not** to initiate the Wordpress installation process in your LDE after having set it up. This is to be entirely sure no residual data from the old installation persists in the installation created by Duplicator.

A guide on how to migrate a live wordpress site to a LDE use Duplicator can be found [**here**](https://www.wpbeginner.com/wp-tutorials/how-to-move-live-wordpress-site-to-local-server/).

### Making changes locally

Please create a separate branch to keep track of the changes you make locally and only merge this feature branch into the main branch when it is ready to be deployed. A CI/CD script *should* take care of automatic deployment of the main branch to production. More on this later.

To encourage this workflow, the main branch is protected from being pushed to and only allows merging through a pull request. Administrators of this project can obviously overrule these restrictions and lone developers will most probably be approving their own pull request. Hence these restrictions should be regarded more as encouragements for best practice than robust systems to prevent bogus code from being pushed to production.

You will most probably be able to limit the changes you make to the `wp-content/themes/` and `wp-content/plugins/` folders. If not, update the `.gitignore` file accordingly. **Be careful when modifying the `.gitignore` file, as publishing for instance the `wp-config.php` file could results in the production database password being exposed to the world. A subsequent removal of this password from the entire Git history would be a PITA, preferably avoided.**

### Publishing your changes to production

