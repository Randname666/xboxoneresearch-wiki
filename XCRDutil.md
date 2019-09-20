# XCRDutil
Manage XVD/XVC mounting in Host from SystemOS.

Xcrdutil can be used to get info about XVD files as well as mount and create XVD files with some limitations. Via the UWP sandbox, two different XVD files can be mounted, "Updater.xvd" and "SystemTools.xvd".

The tool is located at `C:\Windows\System32\xcrdutil.exe`

## Examples
Mount package

```
xcrdutil -m [XUC:]\targetPackage.xvd
```

Outputs something like:
```
Successfully mounted [XUC:]\targetPackage.xvd
Device Path : \\?\GLOBALROOT\Device\Harddisk21\Partition1
Command completed successfully.
```

Mounted XVD's can be accessed with junctions:

```
mklink /j D:\Folder \\?\GLOBALROOT\Device\Harddisk17\Partition1\
```

Query Info for given XVD:

```
xcrdutil -QueryInfo \??\F:\host.xvd 5
```

Write file to Host layer

```
xcrdutil -write_blob [XUC:]\targetPackage.xvd D:\DevelopmentFiles\localPackage.xvd
```

Read file from Host layer

```
xcrdutil -read_blob [XUC:]\targetPackage.xvd D:\DevelopmentFiles\localPackage.xvd
```

Delete file on Host layer

```
xcrdutil -delete_blob [XUC:]\targetPackage.xvd
```