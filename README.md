bugdemo-grails-i18n-reload
==========================

A simple grails2.0.3 project that demonstrates the i18n property file reloading bug

    bugdemo was created with "grails create-app bugdemo"
    bugdemo-inlineplugin was created with "grails create-app bugdemo-inlineplugin"

    then they were tied together by adding
      grails.plugin.location.bugdemoplugin  = "../bugdemo-inlineplugin"
    to bugdemo's BuildConfig.groovy


To demonstrate the bug

    * > cd bugdemo
    * > grails run-app
    * http://localhost:8080/bugdemo
    * edit bugdemo/grails-app/i18n/containerMessages.properties
    * change the value for bugdemo.container.hello.
    * reload -- note your changes are picked up
    * edit bugdemo-inlineplugin/grails-app/i18n/inlinepluginMessages.properties
    * change the value for bugdemo.plugin.hello.
    * reload -- note your changes are NOT picked up
    * Restart the server. now your changes are picked up

I believe that in grails 1.3.7, inline plugin resource file changes were dynamically picked up.
