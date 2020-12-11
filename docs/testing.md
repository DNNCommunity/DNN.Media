# Testing Releases of the DNN Media Module  

There aren't any built-in tests yet. In general, feel free to follow the guidelines below to test.  Steps and use cases specific to each extension will be found below too.

1. Install and/or upgrade the extension
2. Test all of the available features
3. [Create an issue for any issues you find](/issues.html)

## Test Cases

The following tests should be performed prior to considering this module to be ready for release.

### Installation/Upgrade

- Module passes all checks in [EVS](http://evs.dnnsoftware.com)
- Install module cleanly on traditional instance of minimum supported version of DNN
- Install module cleanly on Azure instance of minimum supported version of DNN
- Upgrade module from previous version on traditional instance of minimum supported version of DNN
- Upgrade module from previous version on Azure instance of minimum supported version of DNN
- Module can be added to the page without server- and client-side error messages
- Uninstalling the module removes all module files and database schema without error
- There are no exceptions logged after install, upgrade, and add to page

### General Usage

- Able to select a file from the file system to display, such as an image.
- Choose embed and paste in the embed code from any website.
- Choose website URL and add a YouTube page URL (not embed code), then see it displayed on the next page load.  Repeat for Vimeo, Flickr, and Hulu.