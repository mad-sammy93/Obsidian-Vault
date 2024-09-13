
```
# In all environments, the following files are loaded if they exist,

# the latter taking precedence over the former:

#

# * .env contains default values for the environment variables needed by the app

# * .env.local uncommitted file with local overrides

# * .env.$APP_ENV committed environment-specific defaults

# * .env.$APP_ENV.local uncommitted environment-specific overrides

#

# Real environment variables win over .env files.

#

# DO NOT DEFINE PRODUCTION SECRETS IN THIS FILE NOR IN ANY OTHER COMMITTED FILES.

#

# Run "composer dump-env prod" to compile .env files for production use (requires symfony/flex >=1.2).

# https://symfony.com/doc/current/best_practices.html#use-environment-variables-for-infrastructure-configuration

  

ROOT_FOLDER=hubble2

LOCALE=nl

  

###> symfony/framework-bundle ###

APP_ENV=dev

APP_SECRET=6e04f7dec8dedfd352284be09e030ea6

APP_URL="https://acceptance.hubblefleet.nl"

###< symfony/framework-bundle ###

  

###> symfony/mailer ###

MAILER_DSN=smtp://hubble_mail:1025

###< symfony/mailer ###

  

MESSENGER_TRANSPORT_DSN=doctrine://default

  

###> doctrine/doctrine-bundle ###

# Format described at https://www.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/configuration.html#connecting-using-a-url

# IMPORTANT: You MUST configure your server version, either here or in config/packages/doctrine.yaml

#

# DATABASE_URL="sqlite:///%kernel.project_dir%/var/data.db"

#DATABASE_URL="mysql://root:123@127.0.0.1:3306/hubble2?serverVersion=5.7"

DATABASE_URL=mysql://root:123@hubble_db:3306/hubble

# For dockerized project

# DATABASE_URL=mysql://db_user:db_password@mysql_conatainer_name:port/database_name

###< doctrine/doctrine-bundle ###

  

###> lexik/jwt-authentication-bundle ###

JWT_SECRET_KEY=%kernel.project_dir%/config/jwt/private.pem

JWT_PUBLIC_KEY=%kernel.project_dir%/config/jwt/public.pem

JWT_PASSPHRASE=123456

JWT_TTL=900

TRUSTED_PROXIES=127.0.0.1

WEBHOOK_KEY=ph4gEJx3hI6aKEwIHtNViw

  

DAMAGE_API_URL=''

DAMAGE_API_KEY=''

ADMIN_EMAIL=''

WEB_HOST='https://hubble2-redesign.hubblefleet.nl'

###< lexik/jwt-authentication-bundle ###

######################

#######################

  

#### CO2 PORTAL ####

CO2_APP_URL='http://localhost:4000'

CO2_SSO_PROCESS='sso'
```