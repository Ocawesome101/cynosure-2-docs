                                ** Cynosure 2 **

    This tree contains a set of documentation for the Cynosure kernel's second iteration.

                                 ** Summary **

    Cynosure 2 is the second iteration of the Cynosure kernel.  It features a more posix-like kernel API, with even stricter distinctions between kernel and user space.  It requires that all filesystem drivers have permissions support, and emulates this feature on managed filesystems where it is not present.

    The Cynosure 2 kernel differentiates itself from the original Cynosure, and most other Unix-likes, by abstracting everything as URL rather than as a file (see `URLs.txt').
