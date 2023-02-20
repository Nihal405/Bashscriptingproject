# Bashscriptingproject
This is a Bash script that creates a backup of specified directories and logs the result. 
The purpose of this script is to create backups of specified directories and log the results of each backup. It does this by setting up several variables at the beginning of the script, creating the necessary directories, and then using tar and rsync to perform the backups and copy them to the destination. The script also performs some cleanup tasks to remove old backups and temporary files.

Here's a more detailed breakdown of the script:

The script starts with a shebang line (#!/bin/bash) that specifies the interpreter to be used when executing the script.

The script sets several variables at the beginning, including the backup directory, the directories to be backed up, the backup destination, and the log file.

The script checks if the backup directory exists, and if it doesn't, it creates it using the mkdir command.

The script generates a timestamp using the date command and creates a subdirectory within the backup directory using the timestamp. This subdirectory will contain the backup files.

The script then iterates through the directories to be backed up using a for loop. For each directory, it creates a backup file using the tar command and logs the result in the log file. The tar command compresses the directory using the z flag, creates an archive using the c flag, and writes the output to a file with a name based on the directory name and timestamp.

After backing up all the directories, the script uses rsync to copy the backup files to the backup destination. The rsync command uses the a flag to preserve file permissions and timestamps, the v flag to show progress, and the z flag to compress the data.

The script logs the result of the backup copy to the log file.

The script then uses the find command to locate and remove backups older than 7 days in the backup directory. It does this by finding directories with a depth of 1 (i.e., not searching recursively), of type d (i.e., directories), and with a modification time greater than 7 days ago.

Finally, the script removes the temporary backup subdirectory.

Overall, this script provides a simple way to perform backups of specified directories and to keep track of the results using a log file. It also provides some basic cleanup functionality to remove old backups and temporary files. However, it's worth noting that this script may not be suitable for all backup scenarios, and more complex backup strategies may require additional functionality.
