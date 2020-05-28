### Useful and Common RSYNC commands  ###

Rysnc is a popular and useful file copy and file syncing utility common to most Linux/Unix installations..

## Basic Synax ##

Syntax of rsync command:

Local Sync: # `rsync {options} {Source} {Destination}`

Remote Sync pull: `# rsync {options}  <User_Name>@<Remote-Host>:<Source-File-Dir>  <Destination>`

Remote Sync Push: `# rsync  <Options>  <Source-Files-Dir>   <User_Name>@<Remote-Host>:<Destination>`

Some of the commonly used options in rsync command are listed below:
```
-v, –verbose                             Verbose output
-q, –quiet                                  suppress message output
-a, –archive                              archive files and directory while synchronizing ( -a equal to following options -rlptgoD)
-r, –recursive                           sync files and directories recursively
-b, –backup                              take the backup during synchronization
-u, –update                              don’t copy the files from source to destination if destination files are newer
-l, –links                                   copy symlinks as symlinks during the sync
-n, –dry-run                             perform a trial run without synchronization
-e, –rsh=COMMAND            mention the remote shell to use in rsync
-z, –compress                          compress file data during the transfer
-h, –human-readable            display the output numbers in a human-readable format
–progress                                 show the sync progress during transfer
```


## Basic File copy Synax ##

Copy files from source to destination  location. Location can be local folders or remote servers

`# rsync options source destination`
or 
`rsync -zvh backup.tar /tmp/backups/`

## Copy local direcotries ##
The following command will transfer or sync all the files of from one directory to a different directory in the same machine. Here in this example, /root/rpmpkgs contains some rpm package files and you want that directory to be copied inside /tmp/backups/ folder.

`rsync -avzh /root/rpmpkgs /tmp/backups/`

##  Copy/Sync Files and Directory to or From a Server ##

Copy a Directory from * Local Server **TO  a Remote Server**

`rsync -avz -progress /var/www/ root@10.0.1.90:/var/www`

Copy **FROM  a Remote SErver** TO a local folder

`rsync -avzh root@10.0.1.90:/home/tarunika/rpmpkgs /tmp/myrpms`

## Rsync of SSH ##

With rsync, we can use SSH (Secure Shell) for data transfer, using SSH protocol while transferring our data you can be ensured that your data is being transferred in a secured connection with encryption so that nobody can read your data while it is being transferred over the wire on the internet.

`rsync -avzhe ssh root@192.168.0.100:/root/install.log /tmp/`


## Show Progress While Transferring Data with rsync ##

To show the progress while transferring the data from one machine to a different machine, we can use ‘–progress’ option for it. It displays the files and the time remaining to complete the transfer.

`rsync -avzhe ssh --progress /home/rpmpkgs root@192.168.0.100:/root/rpmpkgs`


## Automatically Delete source Files after successful Transfer ##
So, will you wait for transfer to complete and then delete those local backup file manually? Of Course NO. This automatic deletion can be done using ‘–remove-source-files‘ option.

`rsync --remove-source-files -zvh backup.tar /tmp/backups/`


