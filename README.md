# Project 7 - WordPress Pentesting

Time spent: **8** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Shortcodes: allow unclosed HTML elements in attributes
  - [ ] Summary: Allows malformed HTML elements to execute JS in the browser when creating or editing pages or posts using plain text editor.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.5
![GIF Walkthrough 1](https://thumbs.gfycat.com/RegalCoarseFinch-size_restricted.gif)
  - [ ] Steps to recreate: 
          1. Create new page with any title
          2. Insert the following: `TEST!!![caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">XSS 💀</a>`
          3. View page and mouseover to see alert
  - [ ] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/f72b21af23da6b6d54208e5c1d65ececdaa109c8)

2. (Required) User enumeration using wpscan
  - [ ] Summary: Due to the different login error messages, we can determine whether or not a user account exists on the WordPress install. Using wpscan we can quickly enumerate all usernames since our install does not limit log in attempts
    - Vulnerability types: User Enumeration
    - Tested in version: 4.2
    - Fixed in version: n/a
![GIF Walkthrough 2](https://thumbs.gfycat.com/RightBlueDuiker-size_restricted.gif)
  - [ ] Steps to recreate: 
    1. In Kali terminal run: `wpscan --url http://wpdistillery.vm --enumerate u`
  - [ ] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/blob/4.2-branch/wp-login.php)

3. (Required) Vulnerability Name or ID
  - [ ] Summary: Using a wordlist of common passwords and enumerating the users as we did previously, we can brute force passwords and retrieve login information for any user who chooses to use an insecure password.
    - Vulnerability types: Login Vulnerability
    - Tested in version: 4.2
    - Fixed in version: 
![GIF Walkthrough 3](https://thumbs.gfycat.com/PolishedConventionalBlackfish-size_restricted.gif)
  - [ ] Steps to recreate: 
    1. In Kali terminal run `wpscan --url http://wpdistillery.vm --wordlist /usr/share/wordlists/rockyou.txt --username admin`
  - [ ] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/blob/4.2-branch/wp-login.php)
 


## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [Giphy Capture](https://giphy.com/apps/giphycapture).


## License

    Copyright [2018] [Fahad Ashraf]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
