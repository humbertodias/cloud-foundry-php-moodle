# Moodle on CF

Publishing last version of moodle on Cloud Foundry.

# Prerequires

1. CF account
2. CF Client

# How to deploy

Clone

```
https://github.com/humbertodias/cloud-foundry-php-moodle.git
```
Inside

```
cd cloud-foundry-php-moodle
```

Clone Moodle

```
git clone --depth=1 -b MOODLE_33_STABLE git://git.moodle.org/moodle.git
```

Services

```
cf create-service elephantsql turtle elephant-sql-service
cf create-service sendgrid free sendgrid-service
```

Static Configuration

```
cp manifest.yml moodle/
cp -R bp-config/. moodle/.bp-config
```

Data

```
cd moodle
mkdir moodledata
```

Deploy

```
cf login -a api.run.pivotal.io
cf push --no-start
```


Dynamic Configuration

```
cp config-dist.php config.php
cf env moodle-app
```


Start

```
cf start moodle-app
```


# Started

```

```