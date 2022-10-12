# Vesper PHP Framework

Welcome to Vesper PHP. This framework is aimed to be an easy to use and lightweight tool in building websites and web apps quickly. As a frontend css (sass) framework it has Bulma pre-installed.

<a href="https://packagist.org/packages/lvesperphp/elemental"><img src="https://img.shields.io/packagist/dt/vesperphp/elemental?style=for-the-badge" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/vesperphp/elemental"><img src="https://img.shields.io/packagist/v/vesperphp/elemental?style=for-the-badge" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/vesperphp/elemental"><img src="https://img.shields.io/packagist/l/vesperphp/elemental?style=for-the-badge" alt="License"></a>

## Elemental 

Elemental is the core of Vesper PHP. This folder can be updated in newer versions so making changes within these files is not recommended.

### Pathing and Routes

Every App needs a way to get from one page to the other. With [routes and paths](Elemental/Path.md) you can set up a network of pages that do the things you need them to do. Not every page should always be accessable. And this is where [Shield](Elemental/Shield.md) kicks in. Every part is customisable by using the App/Filters folder as a way to extend functionality. 

- [Routes & Paths](Elemental/Path.md) 
- [Shield](Elemental/Shield.md)
- [Csrf protection](Elemental/Csrf.md)

### Frontier

[Frontier](Elemental/Frontier.md) is the simple yet elegant templating engine within Vesper PHP that allows you to use PHP in its [html templates](Elemental/Views.md). The template files are compiled into PHP files and cached in a separate folder. With its easy way of requesting the template and adding variables Frontier makes building websites quick really easy.

- [Frontier](Elemental/Frontier.md)
- [Templating](Elemental/Views.md)
- [Flash](Elemental/Flash.md)
- [Glob](Elemental/Glob.md)
- [Hook](Elemental/Hook.md)

### Sequel

[Sequel](Elemental/Sequel/Introduction.md) is a one-stop database managing class to help get information quick and simple. And safe. It uses the PHP PDO class and prepared statements to interact with a MySQL database. No SQL writing required but if you need it, you can do that as well.

- [Introduction](Elemental/Sequel/Introduction.md)
- [Select](Elemental/Sequel/Select.md), [Insert](Elemental/Sequel/Insert.md), [Update](Elemental/Sequel/Update.md), [Delete](Elemental/Sequel/Delete.md), [Model](Elemental/Sequel/Model.md).
- [Pagination](Elemental/Sequel/Pagination.md)
- [Tablier](Elemental/Sequel/Tablier.md)

### Sendry

Email sending handler.

### Service Workers

A lot of things are reusable. We store these in the Service/Workers folder for easy access.

- [Config](Elemental/Config.md)
- [Hash](Elemental/Hash.md)
- [Log](Elemental/Log.md)
- [Re(direct)](Elemental/Re.md)

### Variables & Functions
- Config - how the config file works, elements explained and customisation options
- [Global Variables](Variables/Globals.md)

## App 

Where your app shines in customability. The App folder is for everything custom. This has room for controllers, models, filters, packages among other things.

- Controllers & Models
- Filters
- Packages

## Foundry

A basic command line tool to help you build up your Vesper-PHP app quickly. Let's get [started](Foundry/readme.md).

- Table
- Mock
- Filler


## About Vesper PHP

The aim is to make it as PHP 8 compatible as possible. Refactoring code to create a true PHP 8 app is the goal here. But I've couldn't have done this alone. A lot of Stack Overflow searching, php.net browsing and Googling helped build Vesper. Some credits go out to [ideas I've used and good articles I've read.](credits.md)
