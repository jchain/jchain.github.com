Use pandoc as the markdown backend
----------------------------------
see http://drz.ac/2013/01/03/blogging-with-math/

tagcloud support 
----------------
see https://github.com/tokkonopapa/octopress-tagcloud
I like to disable the counts in tagcloud.

updating octopress
------------------
see http://octopress.org/docs/updating/

    git pull octopress master     # Get the latest Octopress
    bundle install                # Keep gems updated
    rake update_source            # update the template's source
    rake update_style             # update the template's style

Add license asides 
------------------
Go to https://github.com/PProvost/www.peterprovost.org
Download source/_includes/custom/asides/license.html
Modify `default_asides` in _config.yml

Add disclaimer asides 
---------------------
Go to https://github.com/PProvost/www.peterprovost.org
Download source/_includes/custom/asides/disclaimer.html
Modify `default_asides` in _config.yml
