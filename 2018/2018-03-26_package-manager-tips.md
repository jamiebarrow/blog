# 2018-03-26 Package manager tips

tags: npm, package manager, tips, yarn

Initially I was just going to post about how to install npm packages while offline, but in case I ever come back to update this page with more tips or package manages, this post is now titled "Package manager tips".

#### npm tips

1. [Configure initial values](https://blog.risingstack.com/nodejs-at-scale-npm-best-practices/) for `npm init -y`

   - 
      ```shell
      npm config set init.author.name YOUR_NAME
      npm config set init.author.email YOUR_EMAIL
      npm config set init.license UNLICENSED
      ```

1. Installing a package [offline](https://stackoverflow.com/questions/43064107/how-to-install-npm-package-while-offline)

   - versions older than npm 5, use the [local-npm package](https://addyosmani.com/blog/using-npm-offline)
   - 
      ```
      npm install --prefer-offline
      ```

1. Update a package, e.g. [Angular CLI](https://github.com/angular/angular-cli#updating-angular-cli)

   - 
      ```shell
      npm uninstall -g @angular/cli
      npm cache verify
      ```
      for before npm5:
      ```shell
      npm cache clean
      ```
   - 
      ```shell
      npm install -g @angular/cli@latest
      ```

#### yarn tips

1. Configure initial values for `yarn init -y`

     - 
         ```shell
         yarn config set init-author-name YOUR_NAME
         yarn config set init-author-email YOUR_EMAIL
         yarn config set init-license UNLICENSED
         ```
