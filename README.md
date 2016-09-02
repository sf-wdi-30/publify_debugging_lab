# Rails Legacy App

> This Rails application has been intentionally broken!

In this lab you will dive into a mature rails application and attempt to fix some reported bugs. This lab will stretch your debugging skills and your ability to navigate a large rails project. It will also simulate a real-world scenario: contributing to an open source project.

We encourage you work together and tackle it in pairs.


### What's Publify?
You will be forking & cloning an open source (MIT LICENSE) blogging platform called Publify.

Publify is a simple but full featured web publishing software. It's built
around a blogging engine and a small message system connected to Twitter.

Publify follows the principles of the IndieWeb, which are self hosting your Web
site, and Publish On your Own Site, Syndicate Everywhere.

Publify has been around since 2004 and is the oldest Ruby on Rails open source
project alive.

#### Features

- A classic multi user blogging engine
- Short messages with a Twitter connection
- Text filters (Markdown, Textile, SmartyPants, @mention to link, #hashtag to link)
- A widgets system and a plugin API
- Custom themes
- Advanced SEO capabilities
- Multilingual : Publify is (more or less) translated in English, French,
  German, Danish, Norwegian, Japanese, Hebrew, Simplified Chinese, Mexican
  Spanish, Italian, Lithuanian, Dutch, Polish, Romanian…

#### Resources

- [Publify Repo](https://github.com/publify/publify/issues)
- [Publify blog](http://blog.publify.co)
- [Publify on Twitter](https://twitter.com/getpublify)
- IRC: \#publify on irc.freenode.net

[![Build Status](https://travis-ci.org/publify/publify.png?branch=master)](https://travis-ci.org/publify/publify)
[![Code Climate](https://codeclimate.com/github/publify/publify.png)](https://codeclimate.com/github/publify/publify)
[![Dependency Status](https://gemnasium.com/publify/publify.png)](https://gemnasium.com/publify/publify)

## Getting Started: Installing Publify Locally

To install Publify you need the following:

- [x] Ruby >= 2.2.5
- [x] Ruby On Rails >= 4.2.0
- [x] A database engine, MySQL, PgSQL or SQLite3

- [x] A compatible JavaScript installation for asset compilation. See [the execjs readme](https://github.com/sstephenson/execjs#readme) for details.
- [ ] ImageMagick

#### Setup ImageMagick Dependency
Make sure that you have ImageMagick installed (used by mini_magick).

Check for imagemagick:
```bash
$ which convert
# /path/to/bin/convert
```

Install it if it's missing (this can take a few minutes):
```bash
$ brew update
$ brew link
$ brew install imagemagick
```

#### Setup Rails Application
Fork & Clone the Publify repo.

Make a note of your ruby version:

```bash
ruby -v
```

Install gem dependencies:

```bash
$ bundle install
```

> Please keep in mind that a *warning* is not the same as an *error*. Make sure to fix any _errors_ you see immediately, and make a note of _warnings_ for future reference.

Setup your database & run your server:

```bash
$ rake db:setup # important that we seed here!
$ rake db:migrate
$ rails server
```

You can now launch you browser and access 127.0.0.1:3000.

You will be prompted to supply a blog title and email:

<img width="382" alt="setup blog screenshot" src="https://cloud.githubusercontent.com/assets/1489337/12763124/9cbd3a5e-c9a7-11e5-97e3-e39e6098adf3.png">

You will be signed in and issued a username and password:

<img width="380" alt="setup example login info screenshot" src="https://cloud.githubusercontent.com/assets/1489337/12763208/0440d834-c9a8-11e5-9c81-05a4b60e9722.png">

#### Seed your blog with posts & tags
```bash
$ rake db:seed # populate your user with posts
# => Seeded 24 articles...
```

#### Look around!
* Visit your blog homepage at `localhost:3000/`
* Go to the `/admin` backend and poke around (it's similar to wordpress).
* Create your first blog post!

##The Bugs

A number of issues have been added to the main github repo. Please fix each bug on its own branch (e.g. `fix_sidebar_styles`).

> Make sure to visit the `issues` section of this repo for more detailed bug descriptions + screenshots.

####Issue \#1: Inconsistent Sidebar Styles
* All titles in the sidebar should have `monospace` style font
* All bullets should be circles.

####Issue \#8: Post tags are shown as "object"
The list of tags associated with a given blog post always display "tags object, object, object".

####Issue \#7: Sign-in form displays raw span html in input fields
The http://localhost:3000/users/sign_in page shows `<span class=` in the input fields, and other HTML "debris" below them.

####Issue \#2: Top Month Always Empty (Archive Sidebar)
* When I click on the top-most month in the Archive Sidebar it says "No posts found...".
* When I create a post in the _current month_ (e.g. February) it displays a link in the sidebar for _next month_ (e.g. March), and says "No posts found..."

####Issue \#3: Months sorted incorrectly (Archive Sidebar)
The sort order of months in the Archive Sidebar is off, with January 2015 appearing directly above December 2015:

### Resolving the Issue
Please fix each bug on its own branch (e.g. `fix_sidebar_styles`).

When you're finished with a bug, create a pull request from your fork back to the main repo.

> Before you push, make sure to run `rubocop` to lint your ruby code and ensure it meets the standards established by this project.

<img width="1239" alt="example pull request" src="https://cloud.githubusercontent.com/assets/1489337/12763002/f2f3a6b6-c9a6-11e5-9e62-cff790c1a89a.png">

> Make sure to reference the issue you are resolving! (You can even close an issue from inside your commit message!)

## Helpful Hints
* Use **Rubber Duck Debugging** -- Make sure you understand the issue!
* Use frequent **Sanity Checks**
    - What are you testing / what are you expecting?
* **Follow the trail**
    - How do you work backwards from the view to the server?
    - How do you find specific files in your rails application?
    - How do you find specific keywords or method calls?
* Sometimes you need to **resart the server** if the views you are working with are being cached.
