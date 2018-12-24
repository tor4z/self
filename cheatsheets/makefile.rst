====
Makefile Cheatsheet
====

The Flavors of Variables
----

#. The value you specify is installed verbatim; if it contains references to other variables, these references are expanded
   whenever this variable is substituted. When this happens, it is called recursive expansion.

   ::

           foo = $(bar)
           bar = $(ugh)
           ugh = Huh?
           all:; echo $(foo)


   will echo ‘Huh?’: ‘$(foo)’ expands to ‘$(bar)’ which expands to ‘$(ugh)’ which finally expands to ‘Huh?’.

#. The value of a simply expanded variable is scanned once and for all, expanding any
   references to other variables and functions, when the variable is defined. 
   it contains their values as of the time this variable was defined. 

   ::

           x := foo
           y := $(x) bar
           x := later

   Is equivalent to

   ::

           y := foo bar
           x := later


#. There is another assignment operator for variables, ‘?=’. This is called a conditional
   variable assignment operator, because it only has an effect if the variable is not yet defined.
   This statement::

        FOO ?= bar

   Is exactly equivalent to this::

        ifeq ($(origin FOO), undefined)
        FOO = bar
        endif

   Note that a variable set to an empty value is still defined, so ‘?=’ will not set that variable.


#. Automatic Variables `see <https://www.gnu.org/software/make/manual/html_node/Automatic-Variables.html>`_

   :$@:
        The file name of the target of the rule.
        ‘$@’ is the name of whichever target caused the rule’s recipe to be run.

   :$%:
        The target member name, when the target is an archive member.
        if the target is foo.a(bar.o) then ‘$%’ is bar.o and ‘$@’ is foo.a. ‘$%’ is
        empty when the target is not an archive member. See Archive_

   :$<:
        The name of the first prerequisite. 
        If the target got its recipe from an implicit rule,
        this will be the first prerequisite added by the implicit rule

   :$?:
        The names of all the prerequisites that are newer than the target, with spaces between them.
        For prerequisites which are archive members, only the named member is used.

        ::

                lib: foo.o bar.o lose.o win.o
                        ar r lib $?

   :$^:
        The names of all the prerequisites, with spaces between them.
        For prerequisites which are archive members, only the named member is used 

   :$+:
        This is like ‘$^’, but prerequisites listed more than once are duplicated in the order they were
        listed in the makefile.

   :$|:
        The names of all the order-only prerequisites, with spaces between them.

   :$*:
        The stem with which an implicit rule matches
        If the target is dir/a.foo.b and the target pattern is a.%.b then the stem is dir/foo.
        The stem is useful for constructing names of related files.
        ‘$*’ is set to the target name minus the suffix. For example, if the target name is ‘foo.c’,
        then ‘$*’ is set to ‘foo’, since ‘.c’ is a suffix.

#. Complex Makefile Example `See <https://www.gnu.org/software/make/manual/html_node/Complex-Makefile.html>`_


.. _Archive: https://www.gnu.org/software/make/manual/html_node/Archives.html#Archives
