# Powershell Reference
This is just a general reference on how to do certain things on Windows OS using Power Shell

## Enabling Powershell Script Execution

### Enable script execution - Requires Local Admin
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
```

### Check current script execution policy
```powershell
Get-ExecutionPolicy
```
Result Interpretation 
- **Restricted**: The default setting on most Windows client systems. Scripts cannot run.
- **RemoteSigned**: Locally created scripts can run, but scripts downloaded from the internet must have a digital signature from a trusted publisher
- **Unrestricted** or **Bypass**: Script execution is enabled with no restrictions or warnings
- **AllSigned**: All scripts must be signed by a trusted publisher, including local ones. 
- **Undefined** or **Default**: No policy is set for the current scope, so the effective policy is determined by a higher-level scope.