---
description: How to set up ProLaser4 to work with SQL database.
---

# 💾 Persistent Records & Tablet

### Introduction

By default, Pro Laser 4 will store the last 100 clocks to the player's machine, which will be loaded on player join.&#x20;

The section below describes a centralized database for tracking clocks server side.&#x20;

### Dependencies

[oxmysql](https://github.com/overextended/oxmysql/) - SQL interface resource. Alternatively you can modify ProLaser4 if you use another resource.

[Documentation for oxmysql](https://overextended.github.io/docs/oxmysql/)

### Setup prolaser4 Database Table

If you do not have an existing database you'd like to use, you can create one, see example below. _Notice:_ this must be the same database you connect to in your server.cfg.

**Example:** \
I use a database called `resources` and my connection string looks like this in my server.cfg:&#x20;

{% code overflow="wrap" %}
```bash
set mysql_connection_string "server=localhost;user=<USERNAME>;password=<PASSWORD>;database=resources;charset=utf8mb4;connectTimeout=60000;acquireTimeout=60000;timeout=60000
```
{% endcode %}

{% hint style="warning" %}
During testing, hangs/server crashes occurred when `connectTimeout=60000;acquireTimeout=60000;timeout=60000`\
was not included, your mileage may vary. I would recommend including these just in case.
{% endhint %}

#### Import SQL / Execute&#x20;

Now with your desired database selected you can execute `setup.sql` included with the resource, it will build a table with columns below.

<details>

<summary>Setup SQL Table Command</summary>

```sql
CREATE TABLE `prolaser4` (
	`rid` INT(11) NOT NULL AUTO_INCREMENT,
	`timestamp` DATETIME NOT NULL,
	`speed` INT(11) NOT NULL DEFAULT '0',
	`distance` FLOAT NOT NULL DEFAULT '0',
	`targetX` FLOAT NOT NULL DEFAULT '0',
	`targetY` FLOAT NOT NULL DEFAULT '0',
	`player` TEXT NOT NULL COLLATE 'latin1_swedish_ci',
	`street` TEXT NOT NULL COLLATE 'latin1_swedish_ci',
	`selfTestTimestamp` DATETIME NOT NULL,
	PRIMARY KEY (`rid`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1;
```

</details>

| Column              | Datatype | Usage                                                                                                                   |
| ------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------- |
| `rid`               | INT      | Record ID / Primary Key                                                                                                 |
| `timestamp`         | DATETIME | Time at which clock occurred.                                                                                           |
| `speed`             | INT      | Estimated speed from clock.                                                                                             |
| `distance`          | FLOAT    | Estimated distance from clock.                                                                                          |
| `targetX`           | FLOAT    | Target entity's GTA X coordinate.                                                                                       |
| `targetY`           | FLOAT    | Target entity's GTA Y coordinate.                                                                                       |
| `player`            | TEXT     | Lidar user's name.                                                                                                      |
| `street`            | TEXT     | Street (and cross street if detected) of target vehicles location.                                                      |
| `selfTestTimestamp` | DATETIME | <p>Time at which the lidar self-test occurred,<br><code>0000-00-00 00:00:00</code> if self-test disabled in config.</p> |

### Logging Configuration

Configure logging settings in `config.lua`. Then use `/lidarrecords` in game to open the tablet and review records.

**Uncomment these two oxmysql lines from fxmanifest:**

<pre class="language-lua"><code class="lang-lua"><strong>...
</strong><strong>dependencies {
</strong><strong>	'oxmysql',		-- uncomment for persistent records &#x26; record management tablet. See docs and configs.
</strong>}
...
server_scripts {
	'@oxmysql/lib/MySQL.lua', -- uncomment for persistent records &#x26; record management tablet. See docs and configs.
<strong>	...
</strong><strong>}
</strong></code></pre>

### Imgur Integration for Record Printing

The Pro Laser 4 uses imgur as an upload endpoint for "printing" lidar records from the tablet. These are more screenshots than prints but, are roleplayed as such. In order to be able to upload these images to imgur you will need to generate an API client ID.

1. Navigate to [https://api.imgur.com/oauth2/addclient](https://api.imgur.com/oauth2/addclient)
2. Register an application, select "_OAuth 2 authorization without a callback URL_"
3. Navigate to: [https://imgur.com/account/settings/apps](https://imgur.com/account/settings/apps)
4. Copy _Client ID_ field.
5. Paste in to config in the following format: `cfg.imgurApiKey = 'Client-ID XXXXXXXXXXXXXXX'` where `XXXXXXXXXXXXXXX` is the client ID you copied in step 4.
6. Restart ProLaser4 and test out your print functionality in the tablet.
