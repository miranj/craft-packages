Craft 2 Packages
================
Packagist server for [Craft CMS] 2 plugins, because why should Craft 2 miss out on
all the [Composer][] goodness?

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


Contributing
------------
Don’t see a plugin you want to use listed? Feel free to [request inclusion][issue], or better yet, add it yourself by [submitting a pull request][pull].
Here's how:

1.  First, make sure that the Craft 2 version of the plugin you wish to add isn't already available
    via [Packagist][]. Some popular plugins (e.g. [SEOmatic][]) have been Composer installable
    all this while, so there is no need to duplicate them here.

2.  Add a new plugin inside `satis.yml` under `repositories:` with the following structure:
        
          aelvan/imager-craft:                      # <vendor>/<package-name>
            type: package
            package:
            - name: aelvan/imager-craft             # <vendor>/<package-name>
              description: Image transforms.        # Short description
              homepage: https://github.com/…        # Plugin home page
              version: 1.6.4                        # Latest Craft 2 supported version
              source:
                type: git
                reference: 1.6.4                    # Git reference (usually a tag)
                url: https://github.com/…           # Repository URL

3.  Figure out the installation method. There are two broad types:
    
    1.  Plugins where the repository's root folder goes directly into `/craft/plugins/`.
        We can make use of Composer's native `craft-plugin` installer for this variant.
        Add the following to the `package` definition:
        
            type: craft-plugin
            require:
              composer/installers: "~1.0"
            extra:                          # optional
                installer-name: imager      # needed if plugin folder name differs from package name

        
    2.  A subfolder inside the plugin repository needs to go into `/craft/plugins/`.
        We make use of a Composer plugin to copy the correct folder from the `vendor`
        directory to `/craft/plugins/`. Add the following to the `package` definition:
        
            require:
              sasedev/composer-plugin-filecopier: "^1.1"
            extra:
              filescopier:
                source: vendor/aelvan/imager-craft/imager   # vendor/<vendor>/<package>/<subfolder>
                destination: craft/plugins/imager           # craft/plugins/<subfolder>

You will find plenty of examples already inside `sats.yml` for the variants described above,
and for things like adding multiple versions of a plugin.

Refer to the [official Composer repositories docs][repo docs] for all the supported options and variations.

[packagist]:https://packagist.org/
[seomatic]:https://packagist.org/packages/nystudio107/seomatic
[pull]:https://help.github.com/articles/creating-a-pull-request-from-a-fork/
[issue]:https://github.com/miranj/craft-packages/issues/new
[repo docs]:https://getcomposer.org/doc/05-repositories.md#package-2



Built With
----------
- [Composer][]
- [Satis](https://github.com/composer/satis)



Acknowledgments
---------------
- [Derrick Grigg][dg] for inspiration and much of the hard work in creating [a Composer workflow for Craft 2](https://dgrigg.com/blog/setting-up-a-craftcms-website-and-plugins-with-composer)
- [Pixel & Tonic](https://pixelandtonic.com/) for Craft CMS

[dg]:https://twitter.com/derrickgrigg
