# File-repo - simple asset management system.

## Workflow

* development methodology - Kanban, probably most effective with pair programming, or really small team;
* branch code scheme - [Git Flow](http://nvie.com/posts/a-successful-git-branching-model/);
* releases every day.

## Technologies

* base framework Ruby on Rails 4.2.4, ruby 2.2.1 or fresh 2.2.3;
* database: I prefer postgresql;
* authentication gems: clearence, sorcery or authlogic, it's depend from future features and users preferences;
* file upload: carrierwave;
* image manipulation: mini_magick;
* image manipulation must be done in background, 'cause it always take a time, so Active Job or/and sidekiq
for background tasks;
* search engine will depend from database and needs. Probably most effective way for this simple application will be using
internal database search, like ilike %pattern%. But if we will need more advanced search for example with specific
Levenshtein distance we will need use full-text search engine like ElasticSearch or Sphinx;
* web server to serve assets and proxy requests to application: nginx;
* application server: cluster of unicorns;
* monitoring and automatic restart of service if something goes wrong: monit;
* deployment: capistrano.

## Not described questions

* What the security? We upload files and store it 'as is' or we have to encrypt it in style of [OwnCloud](https://owncloud.org/)?
* If we have to share assets between users, probably we need to have some kind of access rules. For example user can have a
team, and potentially can share his uploaded asset to nobody (private files), team, just a selected user(s) or everyone.
That's really important, 'cause search results must be filtered according to user access rights.
* Something was called 'Category' is just a tag for every asset. And as I can imagine asset can has many tags.
Some of them (like kind by file extension) can be assigned automatically. All other can be assign by user (with
autocomplete functionality to avoid tag duplication and misspelling).

