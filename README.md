# Features By Platform 
Each Platform Support Some Of The Features Only Windows 10/11 64-bit Has Fully Working Features.
| Fonctionality   | Windows 32-Bit   | Windows 64-Bit   | Macintosh   |
|-------------|-------------|-------------|-------------|
| Scanning For Devices     | True    | True     | Working On     |
| Disabling Selected Device     | True     | True     | Working On     |
| Unistalling Driver Of Device     | False     | True     | Working On     |


# Required To Understand 
Simple Console C++ Software To Disable Or Unistall A Device.

This is the new function to disable a device wich need special TrustedInstaller Permission.
```cpp
void disableDevice(HDEVINFO deviceInfoSet, SP_DEVINFO_DATA& deviceInfoData) {
    if (SetupDiSetClassInstallParams(deviceInfoSet, &deviceInfoData, nullptr, 0)) {
        if (SetupDiCallClassInstaller(DIF_PROPERTYCHANGE, deviceInfoSet, &deviceInfoData)) {
            std::cout << "Device disabled successfully." << std::endl;
        }
        else {
            displayError("Failed to disable device");
        }
    }
    else {
        displayError("Failed to set class install parameters");
    }
}
```
This is the part Of giving Numbers To Devices It Has A Dealy Of One Number Please Add One Number To Your Desired Value.
```cpp
    int deviceNumber;
    std::cout << "Enter the number of the device you want to select: ";
    std::cin >> deviceNumber;

    if (deviceNumber < 1 || deviceNumber > deviceNames.size()) {
        std::cerr << "Invalid device number." << std::endl;
        SetupDiDestroyDeviceInfoList(deviceInfoSet);
        return 1;
    }
```
