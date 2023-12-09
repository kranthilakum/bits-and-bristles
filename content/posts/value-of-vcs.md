---
title: "The value of version control systems"
date: 2020-10-10T09:55:46+05:30
draft: false
categories:
- "version-control"
tags:
- "programming"
- "version-control"
- "git"
---

Software engineering projects tend to grow into large and complex entities over a period of time, with new change requests flowing in regularly. Maintaining such projects often become difficult without the use of software tools that support versioning software artifacts.


Version control software is an invaluable tool for managing software engineering projects. It is surprising that some do not realize this until late into the development process. At one time, I have come across a team who have been working on software code by storing many copies of a program with slightly different names. Without any version control, collaborating with the team on new changes introduced was laborious. The team had started the project without any version control in place. They considered setting up and using the version control as an unwanted effort in the already tight project schedule. As the project proceeded, the number of similar files increased fourfold; collaboration became difficult and the project unmanageable. Eventually, the team recognized the need for a version control and moved to Git source control. In the end, they removed all the unnecessary and stale files from the project and the developers coded and collaborated happily.


At one company, the employees had been using Subversion software for the last five years to version their software artifacts. However, the management had planned to migrate to Git version control due to its support for decentralization. With Git, you do not necessarily rely on a central repository to store all the versions of a project’s files. Instead, every developer “clones” a copy of a repository and has the full history of the project on their own hard drive. I was responsible to introduce Git version control software to the entire organization, smoothly migrate the existing Subversion repositories to Git, and train its employees to effectively use Git in their regular development activities. After the migration, the employees were able to work.


Version control software was originally developed to maintain and coordinate the development of complex software projects such as Linux kernel development. Modern version control system such as Git is based on a distributed repository hosted in a remote server that stores all versions of a collection of project related files. Members of a project team can retrieve (checkout) a copy of these files into their local workstations, make changes, and then check them back into the upstream server. At any point of time, an individual who is connected to the remote server through a network can checkout the latest working copy of the project.


Version control software is invaluable for collaborative projects, for three reasons. First, it provides a form of a backup. Every time a new change is submitted to the server, a snapshot of our working directory is stored in the remote repository. In the event of corruption or lose of your project files, the entire repository until the most recent version can be cloned to your local workstation.


Second, it provides a historical record of the project evolution. Typically, software programs will evolve throughout the project life-cycle. During this course of time, many developers contribute to the same piece of software and tracking down bugs introduced by a developer would become easier since the version control system keeps track of all software revisions. Using version control, it is also possible to move back in time to an exact moment where a certain change has been introduced into the software code and execute the code to produce a desired result. In Git, you can “tag” a particular state of the repository and easily retrieve that state later in the future.


Third, it provides collaboration among the members of the project. The project collaborators can work simultaneously on a collection of files, such as programs and documentation. If two individuals edit the same file in parallel, then the version control software will automatically merge the two versions and flag lines that were edited by both people.
Although the basic idea of version control software seems straightforward, using a system such as Git and Subversion effectively requires some discipline. Version control software is most useful when it is used regularly. It is important to check in new changes at least once in a day. This ensures that your historical record is complete and that a recent backup is always available to every project member. If you are in the midst of editing code, and you have caused a regularly working program to no longer work, it is possible to check those changes on a separate “branch” of the project. Once the new functionality is implemented, then the branch can be merged back into the main branch of the project. Then, your changes be made available to other members of the project team.


Version control should only be used for files that you edit by hand. Automatically generated files, such as any compiled programs, files generated during the build process and binary files, do not belong under version control. These files tend to be large or change often as you recompile or build the project multiple times, so checking them into the repository wastes disk space, because they will be duplicated in the repository and in every working copy of the project. It is a common practice to tell the version control system to ignore such files from tracking every time you recompile or build the project.

Github
Linkedin
StackOverflow
Twitter
Facebook