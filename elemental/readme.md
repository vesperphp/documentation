# Elemental, Vesper PHP core

Elemental is the core of Vesper PHP. This folder can be updated in newer versions so making changes within these files is not recommended.

### Pathing and Routes

Every App needs a way to get from one page to the other. With [routes and paths](elemental/Path.md) you can set up a network of pages that do the things you need them to do. Not every page should always be accessable. And this is where [Vault](elemental/Vault.md) kicks in. Every part is customisable by using the App/Filters folder as a way to extend functionality. 

- Model
- [Routes & Paths](Path.md) 
- [Vault](Vault.md)

A lot of things are reusable. We store these in the Service/Workers folder for easy access.

- [Config](Config.md)
- [Hash](Hash.md)
- [Log](Log.md)
- [Re(direct)](Re.md)

### Variables & Functions
- Config - how the config file works, elements explained and customisation options
- [Global Variables](Globals.md)
