# pg_conftool

This is a limited implementation of Debian's `pg_conftool`.

## Why

The original `pg_conftool` requires Perl and a distribution using `postgresql-common`.
This `pg_conftool` requires only POSIX shell, supports setting multiple parameters at once, and works in FreeBSD.

## Usage

```
pg_conftool [-bsvh] [-j JAIL | -R DIR] [VERSION CLUSTERNAME | PROFILE] [CONFIGFILE] COMMAND

-b      Format boolean value as on or off (not for "show all").
-j JAIL The jid or name of the jail to operate within (on FreeBSD).
-s      Show only the value (not for "show all").
-v      Verbose output (inform if parameter is not found).
-R DIR  The root directory to operate within.
-h      Print help.

VERSION CLUSTERNAME is used to specify cluster in `postgresql-common` distributions.
PROFILE is used to specify cluster in FreeBSD, it must be contained in the
`postgresql_profiles` variable within rc.conf(5).
CONFIGFILE may specify an absolute pathname; cluster specification is not needed then.

show PARAMETER|all      Show a parameter, or all present in CONFIGFILE.
set [PARAMETER VALUE | PARAMETER=VALUE]...
			Set or update a parameter, or multiple parameters.
remove PARAMETER        Remove (comment out) a parameter from CONFIGFILE.
edit                    Open the config file in $EDITOR [vi].
```

## Limitations

`include` and `include_dir` directives are not supported.
