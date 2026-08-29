---
layout: post
title: Configuration Management
excerpt_separator:  <!--more-->
---

Over the years working in IT Operations and System Administration, I've relied on configuration management tools like Ansible to keep server configurations consistent, repeatable, and version-controlled. 

<!--more-->

System administrators can use configuration management tools to set up an IT system, such as a server, then build and maintain other servers with the same settings. Great for automation.

Without configuration management, an administrator would have to maintain configurations manually (which is not very efficient).

Some examples of configuration management tools are Ansible, Puppet, Chef and Saltstack. 

### Important Areas of Configuration Management

- **Inventory** - a list of the assets (servers) being managed, often grouped by role or environment, so playbooks and manifests know which hosts to target.
- **Playbooks / Manifests** - the files that define the desired state of a system and the tasks needed to get there (Ansible calls these playbooks, Puppet/Chef call them manifests/recipes).
- **Roles** - a way of organizing related tasks, files, and templates into reusable units, so common configurations (e.g. "webserver" or "database") can be applied across multiple playbooks.
- **Scripts** - custom logic used to handle tasks that aren't covered by built-in modules, often called from a playbook or manifest.
- **Templates** - files with placeholders that get filled in with variables at run time, used to generate configuration files consistently across servers.

