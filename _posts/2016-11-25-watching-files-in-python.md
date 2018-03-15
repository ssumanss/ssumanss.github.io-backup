---
layout: post
title: Watching Files in Python
date: 2016-11-25 18:42
tags: Python
category: Python
slug: watching-files-in-python
summary: Often in development we want to activate a set of commands when a file system of project folder changes. 
---

Often in development we want to activate a set of commands when a file system. We can use a python library `watchdog` for this. 

## Installation 
To install `watchdog` we can use `pip` like most of python library 

    :::shell 
    pip install watchdog
    
## Setup
A simple program that keeps watch on changes in a folder recursively, means each files in subfolder as well is the follwing

    #!python 
    import os 
    import sys 
    import time  
    from watchdog.observers import Observer  
    from watchdog.events import PatternMatchingEventHandler  

    class MyHandler(PatternMatchingEventHandler):
        patterns = ["*.py", "*.md"]
        
        def process(self, event):
            """
            event.event_type 
                'modified' | 'created' | 'moved' | 'deleted'
            event.is_directory
                True | False
            event.src_path
                path/to/observed/file
            """
            # the file will be processed there
            print(event.src_path, event.event_type) 
            os.system("write your command here.")

        def on_modified(self, event):
            self.process(event)

        def on_created(self, event):
            self.process(event)    
        
    if __name__ == '__main__':
        args = sys.argv[1:]
        path=args[0] if args else '.'
        observer = Observer()
        observer.schedule(MyHandler(), path, recursive=True)
        observer.start()

        try:
            while True:
                time.sleep(1)
        except KeyboardInterrupt:
            observer.stop()

        observer.join()


Save the above script in a file `watcher.py` in root of project. Now activate the watcher simply by 

    :::shell
    python watcher.py [optional path of directory]

Now whenever any file mentioned in patterns will change, the command in `process` function will executed automatically. 
    
    
## Refrences:
1. [Github Repo](https://github.com/gorakhargosh/watchdog/)
2. [Watching a directory for file changes with Python](http://brunorocha.org/python/watching-a-directory-for-file-changes-with-python.html)
    
    
    
