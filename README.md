# Updating HTML Templates using Meteor Up and Meteor

Let's start with some constants:
- App Name = mdregistry
- Deployment tool = Meteor Up (aka mup)
- Javascript Framework = Meteor
- App Hosting = Digital Ocean
- MongoDB Hosting = MongoLabs
- Repo = Bitbucket (Git)

## Step 1
Install the software you need.
- Git - http://git-scm.com/download/mac
- Node - https://nodejs.org/en/download/
- Meteor - https://www.meteor.com/install
- Meteor Up - Once Node is installed simply type the following into your console:
	1. Updgrade NPM by doing `sudo npm i npm -g`
	2. Then install Meteor up by doing `npm i mup -g`

## Step 2
Clone the repo and set up the folder structure you need.
- Next clone the repo for mdregistry by running the following command in your console.

	`git clone https://sscaff1@bitbucket.org/sscaff1/mdregistry.git`
    You should now have a folder `/mdregistry` on your computer. This contains all of the files of the app.
- Make anothe folder in the **same directory** called `mdregistry-deploy`. Both directories `/mdregistry` and `mdregistry-deploy` should be side by side.
- `cd` into `/mdregistry-deploy` and in your console type `mup init`. This will create two files in the directory. Replace the information in these files with the files I provided you.

## Step 3
This step walks your through uploading your changes to the server. Don't follow this set until you actaully change something in the repo.
- `cd` into `mdregistry-deploy` and type in your console `mup deploy --settings settings.json`. That's it after a couple of minutes your changes should be live and online.

## Making changes to MDRegistry
Everything now should be set up. The rest of this guide will talk about the folder structure of mdregistry and briefly touch upon some aspects of Meteor. **All** HTML changes will happen in the client folder. So that's what I'm going to be discussing. Here is the layout of the client folder. This isn't the typical Meteor structure I would use; but since this is also a website, I thought it would be appropriate.

```
|--client
	|--components
    |--js
    |--layout
    	|--footer.html
        |--header.html
        |--layout.html
    |--pages
    |--styles
    main.html
```
The primary folder you want to be concerned with is the pages folder. That folder contains 90% of the HTML that is viewable on the website.

##### Side note about Spacebars
>You will notice that many of the pages do not have a header or footer - it's just the body of the page. That's because I'm taking advantage of Meteor's templating system called _Spacebars_. Like all templating system, Spacebars cut down on repeated code. So if I wanted to insert a hearder on a page and had a template called `header` with Meteor, I would just type `{{> header}}` and whala a header is on my page. Most website use the same header thoughout a site. Now instead of copying and pasting HTML for every page, I simply take advantage of my templating system. 

Each page corresponds to a page on the website. The html files look almost 100% like normal HTML except they are wrapped in a `<template>` tag. The template tag simply names the template. The file name is actually irrelevant. In fact, I can have all my templates in the same file if I wanted to. The current website doesn't use any framework like Bootstrap. Instead it relies on custom styles. The custom styles can be found in the styles folder. The primary stylesheet that the website uses is called styles.css.

Bottom line is, the templates look and behave like regular HTML (because for the most part they are regular HTML) and the CSS behaves like regular CSS. So feel free to change that as you would any site.

When performing changes in Meteor, we want to know what our website is going to look like prior to uploading it. We can't just open up one of the html files. The files are actually being rendered using a layout manager called [Blaze-Layout](https://github.com/kadirahq/blaze-layout). So we have to run meteor. In your console, `cd` into your `mdregistry` directory. Then type `meteor --settings settings.json`. Then go to `localhost:3000` in your web-browser to view the website. If you make a change to any file in the client folder, Meteor will detect the change and automatically refresh the browser for you.
