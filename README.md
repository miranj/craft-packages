Craft 2 Packages
================
Packagist server for [Craft CMS] 2 plugins, because why should Craft 2 miss out on
all the [composer][] goodness?

[composer]:https://getcomposer.org/
[craft cms]:https://craftcms.com/



Usage
-----
1.  Create a `composer.json` file in the root folder of your Craft CMS 2 project.

2.  Add the following to your `composer.json`
    ```
    {
      "repositories": [{
        "type": "composer",
        "url": "https://craft2packages.miranj.in/"
      }]
    }
    ```

3.  Use the standard `composer require <vendor>/<package>` command to add & install plugins
    that you wish to use with this project. You might have to specify a version constraint
    such as `"1.*"` to ensure you don't install a newer, Craft 3 version of the plugin.
    ```
    composer require aelvan/imager-craft:"1.*"
    ```



Acknowledgments
---------------
- Derrick Grigg for inspiration and much of the hard work in creating [a composer workflow for Craft 2](https://dgrigg.com/blog/setting-up-a-craftcms-website-and-plugins-with-composer)
- Pixel & Tonic for Craft CMS
- [Composer][]
- [Satis](https://github.com/composer/satis)
