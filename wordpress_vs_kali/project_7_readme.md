# Project 7 - WordPress Pentesting

Time spent: **8** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Authenticated Stored Cross-Site Scripting (XSS) / CVE-2016-1564
  - [ ] Summary: Cross-site scripting vulnerability in wp-includes/class-wp-theme.php which allows remote attacker to inject arbitrary code.
    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.4.1
  - [ ] GIF Walkthrough: ![Screenshot] (gif/2-wp)
  - [ ] Steps to recreate: Login as admin and create a new post with a malicious link http://www.example.com/wp-admin/customize.php?theme=<svg onload=alert(2 )>
  - [ ] Affected source code: https://core.trac.wordpress.org/changeset/36185
    - [Link 1] https://wpvulndb.com/vulnerabilities/8358
1. (Required) Authenticated Shortcode Tags Cross-Site Scripting (XSS) / CVE-2015-5714
  - [ ] Summary: Malicious JavaScript code is tagged along with the shortcodes and links due to mishandling of unclosed HTML elements during processing of shortcode tags
    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.3
  - [ ] GIF Walkthrough: ![Screenshot] (gif/3-wp)
  - [ ] Steps to recreate: Create a new post with following content : [caption width='1' caption='<a href="' ">]</a><a href="onmouseover='alert(1)'">
  - [ ] Affected source code: https://core.trac.wordpress.org/browser/branches/4.1/src/wp-includes/post.php
    - [Link 1] https://wpvulndb.com/vulnerabilities/8186
1. (Required) Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds / CVE-2015-6535
  - [ ] Summary: YouTube url embedding is tagged along with a malicious JavaScript code which allows remote administrators to inject arbitrary web script or HTML via the Profile name field
    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.2.13
  - [ ] GIF Walkthrough: ![Screenshot] (gif/4-wp)
  - [ ] Steps to recreate:  Create a new post with Contributor or higher privileges and add the content [embed src='https://youtube.com/embed/12345\x3csvg onload=alert(1)\x3e'][/embed]. Other user loads the page and script is executed
  - [ ] Affected source code: https://core.trac.wordpress.org/browser/branches/4.1/src/wp-includes/media.php
1. (Optional) User enumeration using wpscan
  - [ ] Summary: wpscan will produce the list of usernames registered with the WordPress blog
    - Vulnerability types: User enumeration
    - Tested in version: 4.2.2
  - [ ] GIF Walkthrough: ![Screenshot] (gif/1-wp)
  - [ ] Steps to recreate:  Run WPScan with the following command wpscan --url http://wpdistillery.vm/ --enumerate u
  - [ ] Affected source code: https://github.com/WordPress/WordPress/blob/4.2-branch/wp-login.php
    - [Link 1] https://www.wpwhitesecurity.com/wordpress-username-disclosure-vulnerability/
    

## Assets

List any additional assets, such as scripts or files
https://wpvulndb.com/vulnerabilities/


## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work
When I first created the post it was throwing following error when I tried to access it.
The requested URL /hello-world/ was not found on this server.
Solution is to go to Settings -> Permalinks -> Save changes using the admin profile

## License

    Copyright [2019] [Anjana Kamath Miyar]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
