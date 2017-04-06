# Client Upgrades

- A new node is created in [rewHUB](http://r1iad.hub.rewhosting.com/).
  - The 4.8 server recipe must be used.
  - All new nodes should be made in GCE.

- Programmer copies existing client's files and data to node created in previous step.
  - The `upgrade.php` tool is used to help: https://git.rewhosting.com/rew/upgrade
  - Git is used to perform a merge of the latest framework changes.
- Site live team prepares to make the site live (DNS changes).
  - The `upgrade.php` tool is used for this: https://git.rewhosting.com/rew/_upgrade
- Tutorial for `upgrade.php` tool: http://xerxes/wiki/REW_Upgrade_Tools (TODO: Upgrade wiki with current information)

### Upgrade Process (April 5 2017)

### app path

- `cd ~/app`

### Checkout latest code

- `git remote add 4.8 https://git.rewhosting.com/rew/4.8.git`
- `git fetch 4.8 4.8`
- `git merge 4.8/4.8`

### Install dependencies and build assets

- `composer install && npm install`
- `npm run build-backend`
- `npm run build-elite`

### Configure environment

- `console config:env <skin> [<scheme>] --idx-feed=<feed>` -d<db> -u<user> -p<pass>

### Copy site uploads

- `console server:rsync <user>@<host>:app/httpdocs/uploads/ ~/app/httpdocs/uploads/`

### Export existing site's database

- `console db:export --hostname=<host> -d <db> -u <user> -p<pass>`

### Import to local database

- `console db:import <filename>`

### Patch database to latest
- `console db:patch <commit>`
- `php ~/app/tools/phinx.php migrate`

### Merge client code

- `rm ~/app/vendor -rf`
- `git remote add old`
- `ssh://<user>@<host>:/var/www/vhosts/dev.<domain>/app/.git`
- `git pull --no-commit --no-ff old master`
- `git reset -- ~/app/vendor`
- `composer install`

# Fix git conflicts

- `git merge --continue`