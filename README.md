# lsWin

Use "ls" command with Windows console (cmd.exe)

Run the console as Administrator

`setx PATH "%PATH%;C:\code\GitHub\lsWin"`

or from PowerShell, which already supports the ls command, but can be used to set user or machine level environment variables:

$lsWinPath = "c:\REPLACE-ME\lsWin"
$envLevel = "machine"
# or 
# $envLevel = "user"

function append-envVariable($varName, $val, $envLevel="user") {
    $currVal = [Environment]::GetEnvironmentVariable($varName, $envLevel)
    $combinedVal = "$currVal;$val"
    [Environment]::SetEnvironmentVariable($varName, $combinedVal, $envLevel)
    write-host ([Environment]::GetEnvironmentVariable($varName, $envLevel))
}

$currPath = [Environment]::GetEnvironmentVariable("Path", $envLevel)
$newPath = "$currPath;$lsWinPath"
[Environment]::SetEnvironmentVariable("Path", "Test value.", "User")

# dirMac
Use "dir" command with Mac terminal

add to your .bash_profile and restart the terminal
`dir(){ ls; }`
