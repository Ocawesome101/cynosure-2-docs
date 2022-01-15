                                ** Cynosure 2 **

    This tree contains a set of documentation for the Cynosure kernel's second iteration.

                                 ** Summary **

    Cynosure 2 is the second iteration of the Cynosure kernel.  It features a more posix-like kernel API, with even stricter distinctions between kernel and user space.  It requires that all filesystem drivers have permissions support, and emulates this feature on managed filesystems where it is not present.

    The Cynosure 2 kernel differentiates itself from the original Cynosure, and most other Unix-likes, by abstracting everything as URL rather than as a file (see `URLs.txt').
 
                          ** Build Configuration **

    This section describes the process of configuring Cynosure 2's build script.

    Configuration entries are read from .config, with each line in the following format:

        KEY=VALUE # comment

    There is a default configuration in .defconfig in the source tree.

    All available configuration options, each of which is paired with a description, are listed here:

      COMPONENT_3DPRINTER=[yn]
        Whether to enable kernel support for the 3D Printer component.

      COMPONENT_ACCESSPOINT=[yn]
        Whether to enable kernel support for the access_point component.

      COMPONENT_CHUNKLOADER=[yn]
        Whether to enable kernel support for the chunkloader component.

      COMPONENT_CRAFTING=[yn]
      
      COMPONENT_DATACARD=[yn]
        Whether to use the data card for cryptographic operations (e.g. password hashing) rather than a Lua implementation.  This reduces kernel size slightly but the resulting kernel will not boot unless a data card is present.

      COMPONENT_DATABASE=[yn]
      COMPONENT_DEBUG=[yn]

      COMPONENT_DRIVE=[yn]
        Whether to enable kernel support for registering drive components as block devices.  This is necessary when FS_SFS=y.
      
      COMPONENT_EEPROM=[yn]
      COMPONENT_EXPERIENCE=[yn]
      COMPONENT_FILESYSTEM=[yn]
      COMPONENT_GENERATOR=[yn]
      COMPONENT_GEOLYZER=[yn]
      COMPONENT_HOLOGRAM=[yn]
      COMPONENT_INTERNET=[yn]
      COMPONENT_INVENTORYCONTROLLER=[yn]
      COMPONENT_LEASH=[yn]
      COMPONENT_MICROCONTROLLER=[yn]
        Whether to enable kernel support for the microcontroller component.

      COMPONENT_MODEM=[yn]
        Whether to enable kernel support for the modem component.  This by itself does not do much - but all of the MODEM_* options require it.

      COMPONENT_MOTIONSENSOR=[yn]
      COMPONENT_NAVIGATION=[yn]
      COMPONENT_NETSPLITTER=[yn]
      COMPONENT_PISTON=[yn]
      COMPONENT_REDSTONE=[yn]
        Whether to enable redstone card support.

      COMPONENT_ROBOT=[yn]
        Whether to enable kernel support for the robot component.  This by itself does not do anything - but all of the ROBOT_* options require it.

      COMPONENT_SIGN=[yn]
      COMPONENT_TANKCONTROLLER=[yn]
      COMPONENT_TRACTORBEAM=[yn]
      COMPONENT_TRANSPOSER=[yn]
      COMPONENT_TUNNEL=[yn]
      COMPONENT_WORLDSENSOR=[yn]

      COMPONENT_CARDDOCK=[yn]
        Whether to enable kernel support for automatically registering components in Computeronics card docks.  This option is not very expensive for code size.

      PREEMPT_MODE=<good|fast|none>
        How often to insert forced yields into loaded Lua code:
          none - don't insert any, disable this functionality
          fast - force a yield every 0.1s
          good - force a yield every time the yield function is called

      EXEC_CLE=[yn]
        Whether to enable support for the Cynosure Lua Executable format.  It is highly recommended that you enable this option.

      EXEC_SHEBANG=[yn]
        Whether to enable kernel support for scripts starting with a shebang (#!/path/to/interpreter).

      FS_SFS=[yn]
        Enable or disable the Simple File System driver.  When this option is enabled, the resulting kernel will be able to mount and interact with SFS-formatted volumes.  See fs/simplefs.txt for details on the filesystem.

      FS_MANAGED=[yn]
        Enabled or disable the managed filesystem driver.

      SCHEME_MISC=[yn]
        Whether the kernel should support defining schemes from userspace.  When this option is enabled, user programs can register a scheme through the user: scheme.

      SCHEME_EXEC=[yn]
        Whether the kernel should support defining custom executable formats from userspace.  When this option is enabled, user programs can register custom executable format foo by writing specially formatted data to exec://foo, and read all defined formats by listing the files under exec:/.

      SCHEME_HTTP=[yn]
        Whether to include the http: and https: schemes.  These use OpenComputers' Internet Card component to open a HTTP connection.

      SCHEME_TCP=[yn]
        Whether to include the tcp: scheme.  This uses the Internet Card to maintain a TCP socket.

      SCHEME_COMPONENT=[yn]
        Whether to include the component: scheme.  This allows user programs to access raw components by first opening a component under this scheme, then using the invoke() system call with the file descriptor returned from that operation.

      LANGUAGE=<english|...>
        Sets the language to use for kernel error messages.
