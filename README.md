# Engineering Project Database
A tool for managing and executing multiple complex engineering projects

My day job is an Engineer at a large engineering firm. At any given time, I may be supporting up to a dozen different projects. Within each project, there is a work breakdown structure (WBS) that categorizes multiple tasks that need to be done. To be compliant with customer requirements, I have to keep records of how much time (down to the tenth of an hour) I spend not only on each project, but every task within the project's WBS. Most engineers do this either by (1) keeping a big excel spreadsheet, (2) keeping logs of what they do each day on a scrap piece of paper, or (3) just guessing how much time they spent on different projects at the end of each day. In any case, this creates a fair bit of overhead.

The goal of this project is to build an app based on the model-view-control (MVC) architecture that takes care of a lot of this overhead, so that you spend less time doing non-engineering tasks in a spreadsheet, and more time delivering value to the end customer. 

# Model View Control Architecture

The **model** consists of a SQLite3 database that lives as a file either on your computer, or a shared network drive. The SQLite3 file follows the engineering project database format and has a file extension of "*.epdb". 

The **view** layer is a HTML5 application that is served in the default webbrowser of your operating system. If you're an engineering firm, you're likely running Microsoft Windows, so your WebView is based on MS Edge, which since 2020 has been based on Chromium.

The **control** layer is written in Rust using the Tauri framework. It receives commands from the view layer, and translates them into SQL commands to execute against the model SQLite3 file. The results from the SQL query are formatted as JSON and sent back to the view layer.
