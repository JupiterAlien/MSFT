## Andrés Hidalgo.
## PowerShell script to clear Chrome's cache and cookies. 


> Write-Output "| ---------------------------------------- |"
> Write-Output "| Clearing Google Chrome Cache and Cookies |"
> Write-Output "| ---------------------------------------- |"

try
{
    # This will check if the Default folder is empty, if not, it will proceed with the other instructions
    $directory = Get-Item -Path "$env:LOCALAPPDATA\Google\Chrome\User Data\Default"
    if (!($directory.EnumerateFileSystemInfos() | Select-Object -First 1))
    {
        "The folder \Google\Chrome\User Data\Default is empty"
    }
    
    else 
    {
        Remove-Item -path "$env:LOCALAPPDATA\Google\Chrome\User Data\Default\Cache\*" -Recurse -Force -EA SilentlyContinue -Verbose
        Remove-Item -path "$env:LOCALAPPDATA\Google\Chrome\User Data\Default\Cache2\entries\*" -Recurse -Force -EA SilentlyContinue -Verbose
        Remove-Item -path "$env:LOCALAPPDATA\Google\Chrome\User Data\Default\Cookies" -Recurse -Force -EA SilentlyContinue -Verbose
        Remove-Item -path "$env:LOCALAPPDATA\Google\Chrome\User Data\Default\Media Cache" -Recurse -Force -EA SilentlyContinue -Verbose
        Remove-Item -path "$env:LOCALAPPDATA\Google\Chrome\User Data\Default\Cookies-Journal" -Recurse -Force -EA SilentlyContinue -Verbose
    }
}
catch { Write-Output "An error occurred." 
Write-Output $_ }

Write-Output "| --------- |"
Write-Output "| Task done |"
Write-Output "| --------- |"


----

