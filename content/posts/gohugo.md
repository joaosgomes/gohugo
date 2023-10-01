+++
title = 'HUGO First Steps'
date = 2023-10-01T00:28:15+01:00
ReadingTime = 10
Truncated = true
Content = 'HUGO'
draft = false
+++

## HUGO

### The world’s fastest framework for building websites

Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

### Installing on Windows

#### Assumptions

We’ll call your website example.com for the purpose of this tutorial.

- You will use C:\Hugo\Sites as the starting point for your site.
- You will use C:\Hugo\bin to store executable files. 
- Setup Your Directories

You’ll need a place to store the Hugo executable, your content (the files that you build), and the generated files (the HTML that Hugo builds for you).

- Open Windows Explorer.
- Create a new folder: C:\Hugo (assuming you want Hugo on your C drive – it can go anywhere.)
- Create a subfolder in the Hugo folder: C:\Hugo\bin.
- Create another subfolder in Hugo: C:\Hugo\Sites.
  
##### Technical users

- Download the latest zipped Hugo executable from the Hugo Releases page.

- Extract all contents to your "C:\Hugo\bin" folder.

- The hugo executable will be named as hugo_hugo-version_platform_arch.exe. Rename that executable to hugo.exe for ease of use.

- In CMD or your preferred CLI, add the hugo.exe executable to your PATH by navigating to C:\Hugo\bin (or the location of your hugo.exe file) and use the command set PATH=%PATH%;C:\Hugo\bin. If the hugo command does not work after a reboot, you may have to run the command prompt as administrator.

```goat
      .               .                .               .--- 1          .-- 1     / 1
     / \              |                |           .---+            .-+         +
    /   \         .---+---.         .--+--.        |   '--- 2      |   '-- 2   / \ 2
   +     +        |       |        |       |    ---+            ---+          +
  / \   / \     .-+-.   .-+-.     .+.     .+.      |   .--- 3      |   .-- 3   \ / 3
 /   \ /   \    |   |   |   |    |   |   |   |     '---+            '-+         +
 1   2 3   4    1   2   3   4    1   2   3   4         '--- 4          '-- 4     \ 4

```
