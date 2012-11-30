= HFMCmd

HFMCmd is a command-line tool for performing or automating operations in Oracle
Hyperion Financial Management (HFM). It provides a command-line interface for
performing a wide range of repetitive and/or bulk operations on an HFM
application in a simple manner, and facilitates lights out automation of HFM.

HFMCmd uses the published HFM API to perform operations against an HFM
application, but it provides more than just a thin wrapper over the HFM API:
- Where an API function might operate on a single item (e.g. the
  Consolidate API function takes a single Scenario / Year / Entity combination),
  the corresponding command in HFMCmd will typically accept a collection of members
  for each dimension, and automatically manage the looping over each combination.
- Most commands with a large number of parameters provide sensible defaults for
  many parameters. You can consult the online help to determine which parameters
  are required, and which have default values.
- Long-running operations provide progress bars that provide feedback as the
  operation completes.
- Substitution variables can be defined (or environment variables can be used),
  and can then be used virtually anywhere in a command.

In this manner, bulk operations can be performed quickly and easily on large
numbers of scenarios, entities, etc.


== Available Commands

The available commands are continuously being added to, but already there are
commands available for performing most operations associated with:
* Metadata management (e.g. loading / extracting metadata, rules, etc)
* Calculation, consolidation, translation, etc
* Process management (starting, promoting, rejecting, submitting, approving etc)
* Document management (e.g. loading / extracting web forms, reports, etc)

To see a complete list of available commands, run:

    HFMCmd Help Commands

To get detailed help for a specific command, use:

    HFMCmd Help <CommandName>


== Downloading Pre-Built Binaries

HFMCmd supports 2 different builds, one for .NET 3.5 and one for .NET 4.0.
Functionally, the two builds are identical; the only difference is the size of
the executable, and the required version of the .NET framework. Most machines
will already have .NET 3.5 installed, so pick that version if you are unsure.


== Installation

HFMCmd is built as a single standalone .EXE file; no installation is required,
simply unzip it to a directory somewhere, and it is ready to run.

=== Pre-Requisites

HFMCmd does require an existing installation of the .NET framework, as already
described. It also requires at least a client installation of HFM on the machine
where it is to run.


== Running HFMCmd

HFMCmd supports two modes of operation:
1. A single command can be entered on the command-line, along with
   all of the options it requires as keyword arguments, e.g.

      HFMCmd.exe Consolidate UserName:admin Password:password ClusterName:PROD
          AppName:IFRS Scenario:Actual Year:2008 Periods:May-July Entity:GROUP

2. Commands can be read from a command-file, e.g.

      HFMCmd.exe consolidate.hfm

   Contents of consolidate.hfm:

      SetLogonInfo:
        UserName: admin
        Password: password

      OpenApplication:
        ClusterName: PROD
        AppName: IFRS

      Consolidate:
        Scenario: Actual
        Year: 2008
        Periods: May-July
        Entity: GROUP


== Supported Versions of HFM

HFMCmd has been designed to work with multiple different versions of HFM, and
should work with versions 9.3 through to 11.1.2.2, including support for the new
extended dimensionality in 11.1.2.2.


== Licence

HFMCmd is open source software, licenced under a BSD-style licence. That means
it is free to use or modify by anyone for any purpose - but no responsibility is
taken for any bugs, issues or losses that may arise in the use of the software.
See the LICENCE file for more details.


== Issues / Bugs / Feature Requests

If you do identify an issue, bug, or missing feature, you can log an Issue at
https://github.com/agardiner/hfmcmd/issues. There is no guarantee your issue
will be addressed, but you have a better chance if you log an issue and provide
clear and concise details.

