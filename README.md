# Rolex, a better watch

Rolex is a tool for OS X and Linux users to run commands when files change.

Rolex was created after trying two different solutions for running the less compiler:

 - The Unix 'watch' command was slow, since it polls files every few seconds. This isn't needed on OS X or Linux as those OS's have mechanisms to monitor files and get notified when they change
 - CodeKit has a great UI and did lots more besides less, but it was unstable for a very long time, continually trying to monitor the .git directory, hitting OS X's 10,000 files limit and crashing. This was raised to the CodeKit author/vendor and ignored twice.

I wanted something as simple as the 'watch' solution, but:

 - Using the inbuilt capabilities of modern Unix to run events on file save
 - Taking care of file renames in the process

# Usage:

    Run rolex [fileToMonitor] [commandToRun] [searchText] [replaceText]

But if you're running less, there are some handy defaults.

    $ rolex less/style.less

Is the same as:

    $ rolex less/style.less lessc less css

The app will now start monitoring the files specified:

    Watching "less/style.less". When changed, will output to "css/style.css"

Upon those files being saved, the command will run:

    Running command: lessc less/style.less > css/style.css
    Success.

If the command fails (eg, your .less file is malformed), your terminal will beep. Fix the file and save again.