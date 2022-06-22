
# Live response gives Security Operations Teams instantaneous access to a device (also referred to as a machine) using a remote shell connection. This gives you the power to do in-depth investigative work and take immediate response actions to promptly contain identified threats in real time.

All the commands here stated are part of Microsoft's official documentation. 
https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/live-response?view=o365-worldwide

Also, the powershell scripts on the library are quite useful to obtain more results. You can upload a script to the library

#### Put a file in the library

Live response has a library where you can put files into. The library stores files (such as scripts) that can be run in a live response session at the tenant level.
Live response allows PowerShell scripts to run, however you must first put the files into the library before you can run them.
You can have a collection of PowerShell scripts that can run on devices that you initiate live response sessions with.

#### To upload a file in the library

- Click Upload file to library.
- Click Browse and select the file.
- Provide a brief description.
- Specify if you'd like to overwrite a file with the same name.
- If you'd like to be, know what parameters are needed for the script, select the script parameters check box. In the text field, enter an example and a description.
- Click Confirm.
- (Optional) To verify that the file was uploaded to the library, run the library command.

### Commands list

| Command  | Description  | Windows and Windows Server  | MacOS  | Linux  |
|---|---|---|---|---|
| cd  | Changes the current directory.  | Y  | Y  | Y  |
| cls  | Clears the console screen.  | Y  | Y  | Y  |
| connect  | Initiates a live response session to the device.  | Y  | Y  | Y  |
| connections  | Shows all the active connections.  | Y  | N  | N  |
| dir  | Shows a list of files and subdirectories in a directory.  | Y  | Y  | Y  |
| drivers  | Shows all drivers installed on the device.  | Y  | N  | N  |
| fg `<command ID>`  | Place the specified job in the foreground, making it the current job.  NOTE: fg takes a 'command ID` available from jobs, not a PID  | Y  | Y  | Y  |
| fileinfo  | Get information about a file.  | Y  | Y  | Y  |
| findfile  | Locates files by a given name on the device.  | Y  | Y  | Y  |
| getfile 'file_path_here'  | Downloads a file.  | Y  | Y  | Y  |
| help  | Provides help information for live response commands.  | Y  | Y  | Y  |
| jobs  | Shows currently running jobs, their ID and status.  | Y  | Y  | Y  |
| persistence  | Shows all known persistence methods on the device.  | Y  | N  | N  |
| processes  | Shows all processes running on the device.  | Y  | Y  | Y  |
| registry  | Shows registry values.  | Y  | N  | N  |
| scheduledtasks  | Shows all scheduled tasks on the device.  | Y  | N  | N  |
| services  | Shows all services on the device.  | Y  | N  | N  |
| startupfolders  | Shows all known files in startup folders on the device.  | Y  | N  | N  |
| status  | Shows the status and output of specific command.  | Y  | N  | N  |
| trace  | Sets the terminal's logging mode to debug.  | Y  | Y  | Y  |
| analyze  | Analyses the entity with various incrimination engines to reach a verdict.  | Y  | N  | N  |
| collect  | Collects forensics package from machine  | N  | Y  | Y  |
| isolate  | Disconnects the device from the network while retaining connectivity to the Defender for Endpoint service  | N  | Y  | N  |
| release  | Releases a device from network isolation  | N  | Y  | N  |
| run  | Runs a PowerShell script from the library on the device.  | Y  | Y  | Y  |
| library  | Lists files that were uploaded to the live response library.  | Y  | Y  | Y  |
| putfile  | Puts a file from the library to the device. Files are saved in a working folder and are deleted when the device restarts by default.  | Y  | Y  | Y  |
| remediate  | Remediates an entity on the device. The remediation action will vary depending on the entity type:  File: delete  Process: stop, delete image file  Service: stop, delete image file  Registry entry: delete  Scheduled task: remove  Startup folder item: delete file  NOTE: This command has a prerequisite command. You can use the -auto command in conjunction with remediate to automatically run the prerequisite command.  | Y  | Y  | Y  |
| scan | Runs an antivirus scan to help identify and remediate malware. | N | Y | Y |
| undo  | Restores an entity that was remediated.  | Y  | Y  | Y  |

