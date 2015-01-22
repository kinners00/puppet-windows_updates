# windows_updates

Puppet module to install selected windows updates or mask of updated etc.

#### How to use

Install specific update by KB number.

```puppet
  windows_updates::kb {'Some cool KB!':
    ensure => 'present',
    kb => 'KB3012199'
  }
````

Install Updates by name or mask. Will install all updates matching `.Net*` mask

```puppet
  windows_updates::list {'.Net Updates':
    ensure => 'present',
    name => '.Net*'
  }
````

If you are not sure what updates go with name you defined - use `dry_run` option and point it to output file.

```puppet
  windows_updates::list {'.Net Updates':
    ensure => 'present',
    dry_run => 'C:\\what_will_be_installed.txt'
    name => '.Net*'
  }
````

In this case your `what_will_be_installed.txt` will look like:

```
  ComputerName Status KB          Size Title
  ------------ ------ --          ---- -----
  WIN-H7VQ4... ------ KB2931358 322 KB Security Update for Microsoft .NET Frame...
  WIN-H7VQ4... ------ KB2931366 584 KB Security Update for Microsoft .NET Frame...
  WIN-H7VQ4... ------ KB2961851  15 MB Security Update for Internet Explorer 11...
  WIN-H7VQ4... ------ KB2934520  72 MB Microsoft .NET Framework 4.5.2 for Windo...
```
