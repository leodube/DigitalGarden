# Winforms App MOTW Issue
#bug #csharp #winforms #solution

## Bug 

While attempting to deply a Winforms Click Once application on a client machine running Windwos 10, the app would install correctly but running the app would not work. It had worked properly after installs on other Windows 10 machines

## Solution
1. Navigate to `C::\Users\<user>\AppData\Local\Apps\2.0\<obfuscated\directories>`
2. Find folder with only 1 `.exe` in it
3. Right-click on the `.exe` file and click *Properties*
4. Under *General*, unblock the MOTW (Mark of the Web) by unchecking the line saying "This File Came From Another Computer And Might be Blocked"
