# Automatic Warranty retrieval and reporting
See https://www.cyberdrain.com/automating-with-powershell-automating-warranty-information-reporting/ for more information.

This is a PowerShell module that helps you get warranty information for items in your CMDB, PSA, or RMM. This module was made due to some shady businesses going on in the world of Warranty reporting and lookups, and to democtratize the warranty lookups. :)

# Installation instructions

This module has been published to the PowerShell Gallery. Use the following command to install:  

    install-module PSWarranty

# Supported Platforms

The following platforms are supported. You can also use a CSV file as a source to generate reports. This won't sync back to the source though. Some APIs don't allow write-back, so those are only available to create reports.

An unchecked box means development for this is underway

## PSA    
- [x] Autotask
- [x] Connectwise Manage
- [x] IT-Glue (Yes, I know its not a PSA, but where else would I put this?)

## RMM
- [x] Solarwinds N-Able (Reporting only)
- [ ] Solarwinds RMM
- [ ] NinjaRMM (Reporting only)
- [ ] SyncroRMM
- [x] DattoRMM
- [ ] Connectwise Automate

# Supported Manufacturers
- [x] Dell (Requires API key)
- [x] Microsoft
- [x] HP (Spotty API. New one coming soon.)
- [x] Lenovo
- [x] Apple (Estimated dates)

# Usage

To execute an update of all devices in Autotask use:

    $Creds = get-credential  
    update-warrantyinfo -Autotask -AutotaskCredentials $creds -AutotaskAPIKey 'APIINTEGRATIONKEY' -SyncWithSource -OverwriteWarranty

This script will then update all devices in Autotask with the date found in the APIs. If they date returned is invalid it will not update. If the date is already filled in, it will overwrite this.

To only generate HTML reports use

    $Creds = get-credential  
    update-warrantyinfo -Autotask -AutotaskCredentials $creds -AutotaskAPIKey 'APIINTEGRATIONKEY' -GenerateReports

This will generate the reports in C:\Temp. To set the path yourself use

       update-warrantyinfo -Autotask -AutotaskCredentials $creds -AutotaskAPIKey 'APIINTEGRATIONKEY' -GenerateReports -ReportsLocation "C:\OtherFolder"


# Contributions

Feel free to send pull requests or fill out issues when you encounter them. I'm also completely open to adding direct maintainers/contributors and working together! :) I'd love if we could make this into a huge help for our entire community.

# Future plans

Version 0.8 includes all things I required for myself, if you need a feature, shoot me a feature request :)