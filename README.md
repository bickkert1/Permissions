<div id="top"></div>


<!-- ABOUT THE PROJECT -->
## About The Project

This module is made for Laravel applications. it exists of Laravel Sanctum with some own tweaks. one of those tweaks is the middleware named GuardMiddlware.
the function of the middleware is to check if the persons access token has certain permissions. it also contains a file where u can store the permission names (../config/permissions).
Just split the permissions with an ENTER. the permissions are loaded in the config/permissions.php file under the key "permissions". u also see 3 other keys:  aliases, groups and roles.
aliases isn't necessary, it is used to make permissions like members.addMembers better readable for the end user.

<p align="right">(<a href="#top">back to top</a>)</p>

### Groups and Roles
groups isn't necessary either, it is used to make a preconfigured set of roles.
roles isn't necessary either, it is used to make a preconfigured set of groups.
both are implemented in the system so its easy to use. all u need to do is add a row in this configuration: "role/group name" => "["permission/group 1", "permission/group 2" ...]".

<p align="right">(<a href="#top">back to top</a>)</p>

### Commands
there is also a new command (access:token <command>) one of the very usefull commands is fill it is used to give existing users a key with some basic Permissions.
one of the other commands is remove, this removes all keys from all users

<p align="right">(<a href="#top">back to top</a>)</p>

### Guards
There are a few possible guards: @guard, @anyGuard, @notGuard, @multiGuard, @viewOnly, @elseguard and @endguard.

* All the guard directives should be used in combination with @endguard, in case u want to u could also use @elseguard before using @endguard.

* @guard: This will only show a selected piece of HTML/PHP from the blade if the user has a certain permisison.             :: @guard(permission)
* @anyGuard: This has the same function as @guard, but it check if the user has any of the given permissions.               :: @anyGuard(permission1 permission2 ...)
* @multiGuard: this also has the same function as @guard, but will chekc if the user has both of the permissions            :: @multiGuard(permission1 permission2 ...)
* @notGuard: Unlike @guard this will check if the user doesn't have the given permissions                                   :: @notGuard(permission)
* @viewOnly: Use this to check if the user has the viewOnly "permission" if that is true, it will print disabled            :: @viewOnly
* @elseGuard: Use this in combination with any of the "guards", this will show if the user doesn't meet the requirements    :: @elseguard
* @endgaurd: This will end the guards box (the part that is guarded), use this at the end of the HTML code u want to guard  :: @endguard

### GHttp
The GHttp class is a new class wich is used instead of Http, it will always give the right token with the requests.
In some cases it is aliased as Http to make it easy to read.
Below is a list of supported functions (Like in the Http class) and how to use them.

* Get   :: GHttp::get($url, $data)
* Post  :: GHttp::post($url, $data)
* Put   :: GHttp::put($url, $data)

### The Permissions class
I also added a Permissions class with some basic functions to check the permissions. These functions are also used by the guards,
GHttp and is usable in for example Controllers. Below are some functions that can be used inside Controllers. These can be called like this: Permissions::[function]()

* getTokens($user_id) :: This will get all the tokens of the user with the given user_id
* getCurrentToken()   :: This will get the token of the logged in user (this makes use of Auth::user())

There are other functions but these are mainly used in the guards, GHttp and the pre made middleware.

### file locations

* Permissions             :: platform/dashboard/config/permissions
* Permissions.php         :: platform/dashboard/config/permissions.php
* GuardMiddlware          :: platform/[dashboard/backend/api]/app/Http/Middleware
* GuardServiceProvider    :: platform/dashboard/app/providers/GuardServiceProvider
* GHttp                   :: platform/dashboard/app/GHttp.php
* Permissions.php (class) :: platform/dashboard/app/Permission.php

### Built With
* [Laravel](https://laravel.com)
* [Laravel/sanctum] (https://laravel.com/docs/8.x/sanctum)
<p align="right">(<a href="#top">back to top</a>)</p>


<!-- CONTACT -->
## Contact

Biko Schouten - biko@famschouten.com

<p align="right">(<a href="#top">back to top</a>)</p>
