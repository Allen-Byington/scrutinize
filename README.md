# Scrutinize
Shell program to compare Linux OS Configurations

  The impetus behind this is to check multiple hosts in a cluster and ensure they are all configured identically at the operating system level.  There are a good many integration and automation tools out there but none of them will natively do this to make managing a cluster easier.  This is also a valuable tool for troubleshooting as any small difference in the OS config could have substantial repercussions in a running environment.  The thought is to use config files to add to the functionality so not on OS base settings will be checked.  With a properly formatted config file it should be able to check any file on the filesystem and compare it to a template or another host.

Command Line Switches:
  -o output filename pattern  # This pattern will determine the names of the output file(s)
  -a configuration file name  # This will allow you to add more checks via a secondary config file.
  -s                          # This will suppress the standard checks.  Will only work with -a switch.
  -l server list file         # Processes all servers listed in file.  One line per server.
  -h user@hostname            # The host to check against the template.
  -t template filename        # The name of the template file to compare the host(s) against.
  -d user@hostname            # Name of the host to use as a master for direct comparison.  Will not work with -t switch.
  -c template filename        # Name of the file to save as a template for further comparisons.  This will only work with -h switch.

Available Modes:
  Template:  This mode will take a single machine and create a template for use in multiple compares.  The template mode will require a filename parameter.  (Use switches -h, -t and -a)

  Direct Compare:  This mode will compare 2 machines and will take both hosts as command line parameters. (Use switches -o, -a, -h and -d)

  Multiple Compare:  This mode will use the generated template to compare a list of machines.  It will take either the list of hosts on the command line or a file that contains one host per line. (Use switches -o, -a, -l and -t)

Output:
  The output files will contain one line for each setting that is different from the template.  Each line will contain the setting followed by a colon and the configured value.  This will be followed by a space, a pipe symbol another space and then the setting followed by a colon and then the template value.

  The default filename created will be the name of the host that was checked plus a period and the extention of scrutiny.  If multiple hosts are checked there will be a separate file for each host.  If the filename already exists, it will be renamed with a datestamp of the time it was moved out of the way.
