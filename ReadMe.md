# Python Wrapper for Checkvist API

This is a wrapper for the [Checkvist: Open API](https://checkvist.com/auth/api). It includes all calls found in the offical documentation. Please see the source code to clarify arguments and see some basic examples.

The purpose for this project was to create a wrapper that could be used conventionally and with [Pythonista](https://itunes.apple.com/us/app/pythonista/id528579881?mt=8) on iOS. This was the deciding factor for using print statements instead of logging for the optional debugger.

## Installation ##

Currently, the wrapper is only available on gitHub. After using it for a couple more weeks, I submit it to pypi. In order to use the wrapper with an application like Keyboard Maestro, use a shell script action with the following:

    #!/usr/bin/env python
    
    import imp
    import pprint
    pp = pprint.PrettyPrinter(indent=4)
    
    username = '' 		# Enter email address
    remote_key = '' 	# Enter remote key
    
    # Import workaround for Keyboard Maestro
    checkvist = imp.load_source('checkvist', '/Volumes/MacintoshHD/skorzdorfer/unix/bin/checkvist.py')
    
    # Create instance
    cl = checkvist.user_account(username, remote_key, bugger=1)
    
    # To Turn off the Debugger
    # cl = checkvist.user_account(username, remote_key) 
     
    # Send authentication
    cl.send_auth()
    
    # get all all lists
    my_lists = cl.get_lists()
    
## Pythonista

Create a new empty file and paste in checkvist.py. Name the file checkvist

    #!/usr/bin/env python
    import checkvist
    import pprint
    pp = pprint.PrettyPrinter(indent=4)
    
    username = ''
    remote_key = ''
    
    # Create instance
    cl = checkvist.user_account(username, remote_key, bugger=1)
    
    # To Turn off the Debugger
    # cl = checkvist.user_account(username, remote_key)
    
    # Send authentication
    cl.send_auth()
    
    # get all all lists
    my_lists = cl.get_lists()
