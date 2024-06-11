---
external_links:
  - title: apple/cups#371 on GitHub
    url: https://github.com/apple/cups/issues/371
    icon: bi bi-github
  - title: apple/cups#6009 on GitHub
    url: https://github.com/apple/cups/issues/6009
    icon: bi bi-github
---
# Use A4 paper for printing with CUPS and AirPrint

When you try to set up a self-hosted AirPrint print server with Linux and CUPS, your iPhone or iPad may only allow you to print in Legal and Letter sizes, instead of your-preferred A4. You can set up the following steps to make sure that your iPhone or iPad uses the A4 size by default.

1. Open `/etc/cups/cupsd.conf`, then set or add (if not exists) `DefaultPaperSize A4` (instead of `DefaultPaperSize Letter`).
2. Change the value on `/etc/papersize` to `a4` (instead of `letter`).
3. Open your printer's PPD file on `/etc/cups/ppd`, then modify the following values to `A4` (instead of `Letter`):

```
*DefaultPageSize: A4
*StpDefaultPageSize: A4
*DefaultPageRegion: A4    
*StpDefaultPageRegion: A4 
*DefaultImageableArea: A4
*StpDefaultImageableArea: A4
*DefaultPaperDimension: A4    
*StpDefaultPaperDimension: A4    
```

4. Delete the CUPS cache directory with `sudo rm -rf /var/cache/cups`. Just to make sure things working right due to an [old bug](https://github.com/apple/cups/issues/371).
5. Try to reopen the Print menu on your iPhone or iPad.

## If that is still not working

Some printers may only print A4 papers properly if the page size values are adjusted.

1. On your printer's PPD file on `/etc/cups/ppd`, Change all occurences of `PageSize[595.000 842.000]` to `PageSize[595.275590551181 841.889763779528]`.
2. Delete the CUPS cache directory with `sudo rm -rf /var/cache/cups`. Just to make sure things working right due to an [old bug](https://github.com/apple/cups/issues/371).
3. Try to reopen the Print menu on your iPhone or iPad.
