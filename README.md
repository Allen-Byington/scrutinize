# Scrutinize
Shell program to compare linux OS Configurations

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

  Multiple Compare:  This mode will use the generated template to compare a list of machines.  It will take either the list of hosts on the comand line or a file that contains one host per line. (Use switches -o, -a, -l and -t)

Output: 
