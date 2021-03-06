---
content_git_url: https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerAccessToken.md
external help file: Microsoft.Store.PartnerCenter.PowerShell.dll-Help.xml
Module Name: PartnerCenter
online version:
original_content_git_url: https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerAccessToken.md
schema: 2.0.0
---

# New-PartnerAccessToken

## SYNOPSIS
Generate a new access token that can be used to access Partner Center.

## SYNTAX

### UserCredential (Default)
```powershell
New-PartnerAccessToken -ApplicationId <String> [-Consent] [-Credential <PSCredential>]
 [-Environment <EnvironmentName>] [-RefreshToken <String>] -Resource <String> [-TenantId <String>]
 [<CommonParameters>]
```

### ServicePrincipal
```powershell
New-PartnerAccessToken [-Consent] -Credential <PSCredential> [-Environment <EnvironmentName>]
 [-RefreshToken <String>] -Resource <String> [-ServicePrincipal] [-TenantId <String>] [<CommonParameters>]
```

## DESCRIPTION
The New-PartnerAccessToken command generates a new access token that can be used to access Partner Center.

## EXAMPLES

### Example 1
```powershell
PS C:\> $appId = '<AAD-AppId>'
PS C:\> $appSecret = '<AAD-AppSecret>' | ConvertTo-SecureString -AsPlainText -Force
PS C:\> $credential = New-Object System.Management.Automation.PSCredential $appId, $appSecret
PS C:\> New-PartnerAccessToken -Credential $credential -Resource https://api.partnercenter.microsoft.com -ServicePrincipal -TenantId '<TenantId>'
```

Generates a new access token using a service principal for authentication.

### Example 2
```powershell
PS C:\> $credential = Get-Credential
PS C:\> New-PartnerAccessToken -ApplicationId '<AAD-AppId>' -Credential $credential -Resource https://api.partnercenter.microsoft.com -TenantId '<TenantId>'
```

Generates a new access token using user credentials for authentication.

### Example 3
```powershell
PS C:\> $appId = '<AAD-AppId>'
PS C:\> $appSecret = '<AAD-AppSecret>' | ConvertTo-SecureString -AsPlainText -Force
PS C:\> $credential = New-Object System.Management.Automation.PSCredential $appId, $appSecret
PS C:\> $token = New-PartnerAccessToken -Consent -Credential $credential -Resource https://api.partnercenter.microsoft.com -ServicePrincipal
```

Performs the secure app model partner consent process. The `$token.RefreshToken` value should be stored in a secure location such as Azure Key vault. The Azure AD application used in this example much have `urn:ietf:wg:oauth:2.0:oob` configured as one of the reply URLs.

### Example 4
```powershell
PS C:\> $appId = '<AAD-AppId>'
PS C:\> $appSecret = '<AAD-AppSecret>' | ConvertTo-SecureString -AsPlainText -Force
PS C:\> $credential = New-Object System.Management.Automation.PSCredential $appId, $appSecret
PS C:\> New-PartnerAccessToken -RefreshToken '<Refresh-Token-Value>' -Resource https://api.partnercenter.microsoft.com -Credential $credential -ServicePrincipal
```

Generates a new access token using the refresh token. The Azure AD application used in this example much have `urn:ietf:wg:oauth:2.0:oob` configured as one of the reply URLs.

## PARAMETERS

### -ApplicationId
The application identifier used to access Partner Center.

```yaml
Type: String
Parameter Sets: UserCredential
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Consent
A flag that indicates that the intention is to perform the partner consent process.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Credentials that represents the service principal.

```yaml
Type: PSCredential
Parameter Sets: UserCredential
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

```yaml
Type: PSCredential
Parameter Sets: ServicePrincipal
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Environment
Name of the environment to be used during authentication.

```yaml
Type: EnvironmentName
Parameter Sets: (All)
Aliases: EnvironmentName
Accepted values: GlobalCloud, ChinaCloud, GermanCloud, USGovernment

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RefreshToken
The refresh token to use in the refresh flow.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Resource
The identifier of the target resource that is the recipient of the requested token.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ServicePrincipal
A flag indicating that a service principal will be used to authenticate.

```yaml
Type: SwitchParameter
Parameter Sets: ServicePrincipal
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TenantId
The Azure AD domain or tenant identifier.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationResult

## NOTES

## RELATED LINKS
