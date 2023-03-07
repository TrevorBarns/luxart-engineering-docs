---
description: How to set up ProLaser4 to work with SQL database.
---

# 💾 Persistent Records & Tablet

### Introduction

By default, Pro Laser 4 will store the last 100 clocks to the clients machine, which will be restored on relog.&#x20;

The section below describes a centralized database for tracking clocks server side. Notice: records push to the database intermittently as follows. Players submit all records to server every minute, then the server pushes those records to database every 5 minutes.

### Dependencies

[oxmysql](https://github.com/overextended/oxmysql/) - SQL interface resource. Alternatively you can modify ProLaser4 if you use another resource.

[Documentation for oxmysql](https://overextended.github.io/docs/oxmysql/)

### Setup prolaser4 Database Table

If you do not have an existing database you'd like to use, you can create one, see example below. Notice: this must be the same database you connect to in your server.cfg.

**Example:** \
****I use a database called `resources` and my connnection string looks like this in my server.cfg:&#x20;

{% code overflow="wrap" %}
```bash
set mysql_connection_string "server=localhost;user=USERNAME;password=PASSWORDdatabase=resources;charset=utf8mb4
```
{% endcode %}

#### Import SQL / Execute&#x20;

Now with your desired database selected you can execute `setup.sql` included with the resource, it will build a table with columns below.

<details>

<summary>Setup SQL Table Command</summary>

```sql
CREATE TABLE `prolaser4` (
	`ID` INT(11) NOT NULL AUTO_INCREMENT,
	`timestamp` DATETIME NULL DEFAULT NULL,
	`speed` INT(11) NOT NULL DEFAULT '0',
	`dist` FLOAT NOT NULL DEFAULT '0',
	`targetX` FLOAT NOT NULL DEFAULT '0',
	`targetY` FLOAT NOT NULL DEFAULT '0',
	`player` TEXT NOT NULL COLLATE 'latin1_swedish_ci',
	`street` TEXT NOT NULL COLLATE 'latin1_swedish_ci',
	PRIMARY KEY (`ID`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
AUTO_INCREMENT=0;
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
</strong>     'oxmysql',		-- uncomment for persistent records &#x26; record management tablet. See docs and configs.
}
...
server_scripts {
     '@oxmysql/lib/MySQL.lua', -- uncomment for persistent records &#x26; record management tablet. See docs and configs.
	'UTIL/sv_*.lua',
	'UTIL/semver.lua'
}
</code></pre>
