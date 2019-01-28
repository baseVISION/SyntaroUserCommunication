# User Communication Engine for Syntaro Application Management

This tool allows to show pop-up notifications from the system context to the user desktop during an application installation with the Syntaro Applicatoin Management module. There were three new functions added to the BaseScript, which can be used to send the following messages:
- generic messages
- prompt the user to close an open applications
- ask if the user wants to postpone the installation to a later time.


## Prerequisites
- Up to date version of basescript ([See the Wiki for more details](https://wiki.syntaro.com/index.php?title=Application_Management_Module#Others))
- Windows 10 clients
- Basepackage has to be installed on the client



## Installation

You can download the installation MSI from [GitHub](https://github.com/baseVISION/SyntaroUserCommunication/releases).

Once you have downloaded the MSI package, you can deploy it with msiexec or  over the Syntaro Application Management module.

msiexec

```
msiexec /i Syntaro_UserCommunication_1.1.msi /Q
```

Syntaro Application Management ([Visit the Wiki to see how to create a new application package](https://wiki.syntaro.com/index.php?title=Application_Management_Create_your_first_Package)).

```
Execute-MSI Syntaro_UserCommunication_1.1.msi -Install
```


#### Installation detail

During installation three files will be copied to: "C:\Program Files\Syntaro\UserCommunication". Those three files are:
- Syntaro.Appmanagement.UserCommunication.exe
- Newtonsoft.Json.xml
- Newtonsoft.Json.dll

After the files are copied, the EXE will be registered in the run-key of the user, so it starts automatically the next time, the user logs in.

## Testing

To make sure, that the package was successfully installed, log off and then log in again and check if you have the Syntaro Application Management Icon in your traybar.
![TraybarIcon](https://github.com/baseVISION/SyntaroUserCommunication/blob/master/Pictures/Traybar.png)


If you do, load the basescript as a module into a powershell and create a user notification.
To do so, download the basescript from [GitHub](https://github.com/ThomasKur/SyntaroApplicationManagementBaseScript/blob/master/SyntaroAppManagementHelper_001.ps1) to C:\Scripts\baseScript.ps1. Once downloaded, start PowerShell as an elevated user and execute the following lines:

```
Set-ExecutionPolicy Bypass
Import-Module "C:\Scripts\baseScript.ps1"
Invoke-GenericUserMessage -title "Intalling Application" -message "We are currently installing your application please stand by"
```
If a pop-up windows, with the defined title and message appears, the package was installed successfully.
![PopUpWindows](https://github.com/baseVISION/SyntaroUserCommunication/blob/master/Pictures/Syntaro.Appmanagement.UserCommunication_OcCjlob7c7.png)

## Details
For more details, visit the [Syntaro Wiki](https://wiki.syntaro.com/index.php?title=Application_Management_Module#User_Notifications)

## Authors

* **Athiraiyan Kugaseelan*** - *Initial work* - [baseVision AG](https://basevision.ch)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

