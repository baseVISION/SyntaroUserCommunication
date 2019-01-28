# User Communication Engine for Syntaro Application Management

This tool allows to show pop-up notifications from the system context to the user desktop during an application installation with the Syntaro Applicatoin Management module. There were three new functions added to the BaseScript, which can used to send generig messages, prompt the user to close open applications and to ask if the user wants to postpone the installation to a later time.


## Prerequisites

As prerequisites for this application, you have to have the Syntaro BasePackage installed on the client. Also, you have to update the BaseScript in the Syntaro Portal, so you can use the new functions.


### Installing

You can install it with msiexec or deploy the package over the Syntaro Application Management module.

msiexec
```
msiexec /i Syntaro_UserCommunication_1.1.msi /Q
```

Syntaro Application Management

```
Execute-MSI Syntaro_UserCommunication_1.1.msi -Install
```

The application will be automatically started, when the user logs in the next time.

## Testing

To make sure, that the package was successfully installed, log off and then log in again and check if you have the Syntaro Application Management Icon in your traybar.
If you do, load the basescript as a module into a powershell session and execute the command:

```
Invoke-GenericUserMessage -title "Intalling Application" -message "We are currently installing your application please stand by"
```
If a pop-up windows, with the defined title and message appeaars, the package was installed successfully.

# Details
For more details, visit the [Syntaro Wiki](https://wiki.syntaro.com/index.php?title=Application_Management_Module#User_Notifications)

## Authors

* **Athiraiyan Kugaseelan*** - *Initial work* - [baseVision AG](https://basevision.ch)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

