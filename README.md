# copt
Header-only C program attribute manager library

# Example
```C
#include <stdio.h>

#include "copt.h"

int main(int argc, char **argv)
{
    /* name of the program, version, usage */
    copt_program_init("myprogram", "0.1.0", "[OPTION] [ARGS...]");

    /* name of the option (ID), short flag, long flag, usage/description, parameters */
    copt_add_option("help", "-h", "--help", "Print help message", "");
    copt_add_option("version", "-v", "--version", "Print version", "");
    copt_add_option("delete", "-d", "--delete", "Delete a file", "[NAME]");

    /* prints the program version which was previously set */
    copt_print_version();

    /* automatically prints all the program's options and its usage */
    copt_print_help();

    /* interacting with argv */
    if (argc == 1 || copt_option_is("help", argv)) {
        copt_print_help();
    } else if (copt_option_is("version", argv)) {
        /* do whatever */
    } else if (copt_option_is("delete", argv)) {
        /* do whatever */
    } else {
        fprintf(stderr, "Error: unrecognised option\n");
        copt_print_help();
    }
    
    return 0;
}
```