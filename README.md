# Caedo Framework - Minimum Viable Example

This is the Minimum Viable Example of the Caedo PHP Framework.  If you are looking to learn about CAEDO, the Caedo Example is where I suggest you start.  It is loaded with lots of working pages that can be used to understand how CAEDO works.  This project is best to be used when you understand CAEDO enough that you're interested in giving it a real try, but want to have a place to start from.  

The Caedo PHP Framework Example Project is located here: https://github.com/kananlanginhooper/Caedo_Example

The Caedo PHP Framework Core Project is located here: https://github.com/kananlanginhooper/Caedo

# Using the Caedo

The easiest way to use Caedo is by using composer.  Composer is already installed in this example.  I suggest you run `composer update` to make sure you're running on the newest version.  I will try and keep this updated also.


# What I can change, and what I should change

I'm not going to repeat everything I've written in other places here.  If you're looking for the full run down, check out the example project.

 ##VENDOR is where composer will install it's projects.  I changed this from the default 'vendor'.  I feel this, plus the ## make it more clear that this is not to be touched or deleted.
 
 ##CAEDO.inc is also a very important file.  Since CAEDO has some functions that overlap with composer, such as autoloading and such, we included the ##CAEDO.inc file instead of the standard `/vendor/autoload.php`.  We do out class loading in a different way, and a way that I prefer.  It's more friendly towards an active project where most of the files will be unique instead of pulled from other projects or libraries.  It would be very limiting to require that every file of your entire project be placed in a single folder.  CAEDO allows for much for flexibility, place your class files in ANY folder under `__LOCAL_USER_CLASSES`, CAEDO will find them.
 
 I have included some JS and CSS in `__LOCAL_USER_CLASSES`.  You can remove this.  In fact you can remove everything in this folder if you need to.  Just place new classes and page templates in here.
 
 All of the config needed to get CAEDO live on a server or localhost is in `__CAEDO_CONFIG`.  There is a file for DB setup and also for site setup.  Site is always needed, DB is only needed if you are using a database (which this example does not). 
 
 This is a short excerpt from config.Site.inc:
 
`$SiteConfig = new clsSiteConfig('localhost', 'default', '', true, 'caedo', false, '', false, '', 'file', '/tmp', true, true, true);`

`clsSiteConfigs::AddSiteConfig($SiteConfig);`

`// clone for IP access`

`$SiteConfig = clone $SiteConfig;`

`$SiteConfig->Url = '127.0.0.1';`

`clsSiteConfigs::AddSiteConfig($SiteConfig);`


What this does is setup localhost.  So if you run this project on localhost it should work.  The first line sets up 'localhost', the lines following clone and add a new site for '127.0.0.1'.
You can clone and add more sites using this method.  

`clsSiteConfigs::$DefaultSite = 'localhost';`

The last line in the file sets up the default site.  This is what you should use the URL cannot be parsed to any site.
 
 