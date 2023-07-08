# ServiceBundle

## Authentication

* Headers
* JWT

### Usage

```yaml
security:
    providers:
        users:
            entity:
                class: 'App\Entity\User'
                property: 'email'
    firewalls:
        dev:
            pattern: ^/(_(profiler|wdt)|css|images|js)/
            security: false
        main:
            lazy: true
            provider: users
            custom_authenticators:
                - Beerfranz\ServiceBundle\Security\HeaderAuthenticator
                - Beerfranz\ServiceBundle\Security\JwtAuthenticator

    access_control:
        - { path: ^/, roles: ROLE_ASSET_ADMIN }
        - { path: ^/asset_definitions, roles: ROLE_ARCHITECT_ADMIN }
```
