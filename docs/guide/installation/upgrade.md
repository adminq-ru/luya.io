# Upgrading LUYA

This page describes how to update an existing LUYA instance to the latest version.

## Composer

Change the LUYA versions for each modules and LUYA itself in your `composer.json`:

```json
"require": {
    "luyadev/luya-module-cms" : "^4.0",
    "luyadev/luya-module-admin" : "^4.0"
}
```

After updating the file, execute the update command of Composer which could take a few minutes.

```sh
composer update
```

Now you got a new Composer lock file, which can be used for other team members to install the new LUYA version.

## Console

After updating with Composer, run the following command to upgrade the database:

```sh
./vendor/bin/luya migrate
```

Now refresh all existing importer components with the LUYA import command:

```sh
./vendor/bin/luya import
```

Sometimes image filters changes and you should reprocess all images in the filemanager:

```sh
./vendor/bin/luya admin/storage/process-thumbnails
```

## Upgrade the application code

Read the CHANGELOG.md to see all new, fixed and breaking features. The **most important** when upgrading into another version is to read the BC Breaks Guides in order to see all changes which have to be done in your application to run the newest version of LUYA.

+ [LUYA Core BC Breaks Guide](https://github.com/luyadev/luya/blob/master/core/UPGRADE.md).
+ [LUYA Admin BC Breaks Guide](https://github.com/luyadev/luya-module-admin/blob/master/UPGRADE.md).
+ [LUYA CMS BC Breaks Guide](https://github.com/luyadev/luya-module-cms/blob/master/UPGRADE.md).