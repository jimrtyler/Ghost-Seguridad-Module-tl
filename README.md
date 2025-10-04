# 👻 Ghost Security Module
**PowerShell-based na Windows at Azure Security Hardening Tool**

> **Proactive na security hardening para sa Windows endpoints at Azure environments.** Ang Ghost ay nagbibigay ng PowerShell-based na hardening functions na makakatulong na mabawasan ang mga karaniwang attack vectors sa pamamagitan ng pag-disable sa mga hindi kinakailangang services at protocols.

## ⚠️ Mahahalagang Disclaimer

**KAILANGAN NG TESTING**: Laging i-test muna ang Ghost sa mga non-production environments. Ang pag-disable ng mga services ay maaaring makaapekto sa mga lehitimong business functions.

**WALANG GUARANTEE**: Bagaman ang Ghost ay nakatutok sa mga karaniwang attack vectors, walang security tool na makakapigil sa lahat ng mga pag-atake. Ito ay isang component ng isang comprehensive security strategy.

**OPERATIONAL IMPACT**: Ilang functions ay maaaring makaapekto sa system functionality. Maingat na suriin ang bawat setting bago mag-deploy.

**PROFESSIONAL ASSESSMENT**: Para sa production environments, makipag-consult sa mga security experts upang matiyak na ang mga settings ay naaayon sa mga pangangailangan ng inyong organisasyon.

## 📊 Security Landscape

Ang Ransomware damages ay umabot sa **$57 billion noong 2025**, at ang research ay nagpapakita na maraming matagumpay na pag-atake ang sumusulit sa mga basic Windows services at misconfigurations. Ang mga karaniwang attack vectors ay kinabibilangan ng:

- **90% ng ransomware incidents** ay nagsasangkot ng RDP exploitation
- **SMBv1 vulnerabilities** ay nagbigay-daan sa mga pag-atake tulad ng WannaCry at NotPetya
- **Document macros** ay nananatiling pangunahing malware delivery method
- **USB-based attacks** ay patuloy na nagtutungo sa air-gapped networks
- **PowerShell abuse** ay tumaas nang malaki sa mga nakaraang taon

## 🛡️ Ghost Security Functions

Ang Ghost ay nagbibigay ng **16 Windows hardening functions** kasama ang **Azure security integration**:

### Windows Endpoint Hardening

| Function | Layunin | Mga Consideration |
|----------|---------|----------------|
| `Set-RDP` | Namamahala ng Remote Desktop access | Maaaring makaapekto sa remote administration |
| `Set-SMBv1` | Kumokontrol ng legacy SMB protocol | Kailangan para sa mga sobrang lumang sistema |
| `Set-AutoRun` | Kumokontrol ng AutoPlay/AutoRun | Maaaring makaapekto sa user convenience |
| `Set-USBStorage` | Naglilimita ng USB storage devices | Maaaring makaapekto sa lehitimong USB usage |
| `Set-Macros` | Kumokontrol ng Office macro execution | Maaaring makaapekto sa macro-enabled documents |
| `Set-PSRemoting` | Namamahala ng PowerShell remoting | Maaaring makaapekto sa remote management |
| `Set-WinRM` | Kumokontrol ng Windows Remote Management | Maaaring makaapekto sa remote administration |
| `Set-LLMNR` | Namamahala ng name resolution protocol | Karaniwang ligtas na i-disable |
| `Set-NetBIOS` | Kumokontrol ng NetBIOS sa TCP/IP | Maaaring makaapekto sa legacy applications |
| `Set-AdminShares` | Namamahala ng administrative shares | Maaaring makaapekto sa remote file access |
| `Set-Telemetry` | Kumokontrol ng data collection | Maaaring makaapekto sa diagnostic capabilities |
| `Set-GuestAccount` | Namamahala ng Guest account | Karaniwang ligtas na i-disable |
| `Set-ICMP` | Kumokontrol ng ping responses | Maaaring makaapekto sa network diagnostics |
| `Set-RemoteAssistance` | Namamahala ng Remote Assistance | Maaaring makaapekto sa helpdesk operations |
| `Set-NetworkDiscovery` | Kumokontrol ng network discovery | Maaaring makaapekto sa network browsing |
| `Set-Firewall` | Namamahala ng Windows Firewall | Kritikal para sa network security |

### Azure Cloud Security

| Function | Layunin | Mga Requirement |
|----------|---------|--------------|
| `Set-AzureSecurityDefaults` | Nagpe-enable ng basic Azure AD security | Microsoft Graph permissions |
| `Set-AzureConditionalAccess` | Nag-configure ng access policies | Azure AD P1/P2 licensing |
| `Set-AzurePrivilegedUsers` | Nag-audit ng privileged accounts | Global Admin permissions |

### Enterprise Deployment Options

| Paraan | Use Case | Mga Requirement |
|--------|----------|--------------|
| **Direct Execution** | Testing, maliliit na environments | Local admin rights |
| **Group Policy** | Domain environments | Domain admin, GP management |
| **Microsoft Intune** | Cloud-managed devices | Intune licensing, Graph API |

## 🚀 Quick Start

### Security Assessment
```powershell
# I-load ang Ghost module
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')

# Tingnan ang kasalukuyang security posture
Get-Ghost
```

### Basic Hardening (I-test Muna)
```powershell
# Essential hardening - i-test sa lab environment muna
Set-Ghost -SMBv1 -AutoRun -Macros

# I-review ang mga pagbabago
Get-Ghost
```

### Enterprise Deployment
```powershell
# Group Policy deployment (domain environments)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Intune deployment (cloud-managed devices)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Installation Methods

### Option 1: Direct Download (Testing)
```powershell
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')
```

### Option 2: Module Installation
```powershell
# I-install mula sa PowerShell Gallery (kapag available)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Option 3: Enterprise Deployment
```powershell
# I-copy sa network location para sa Group Policy deployment
# I-configure ang Intune PowerShell scripts para sa cloud deployment
```

## 💼 Use Case Examples

### Small Business
```powershell
# Basic protection na may minimal na impact
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Healthcare Environment
```powershell
# HIPAA-focused hardening
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Financial Services
```powershell
# High-security configuration
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Cloud-First Organization
```powershell
# Intune-managed deployment
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Function Details

### Core Hardening Functions

#### Network Services
- **RDP**: Binoblock ang remote desktop access o nire-randomize ang port
- **SMBv1**: Dini-disable ang legacy file sharing protocol
- **ICMP**: Pinipigilan ang ping responses para sa reconnaissance
- **LLMNR/NetBIOS**: Binoblock ang legacy name resolution protocols

#### Application Security
- **Macros**: Dini-disable ang macro execution sa Office applications
- **AutoRun**: Pinipigilan ang automatic execution mula sa removable media

#### Remote Management
- **PSRemoting**: Dini-disable ang PowerShell remote sessions
- **WinRM**: Tinitiguil ang Windows Remote Management
- **Remote Assistance**: Binoblock ang remote assistance connections

#### Access Control
- **Admin Shares**: Dini-disable ang C$, ADMIN$ shares
- **Guest Account**: Dini-disable ang Guest account access
- **USB Storage**: Nililimitahan ang USB device usage

### Azure Integration
```powershell
# Kumukonekta sa Azure tenant
Connect-AzureGhost -Interactive

# I-enable ang security defaults
Set-AzureSecurityDefaults -Enable

# I-configure ang conditional access
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# I-audit ang privileged users
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune Integration (Bago sa v2)
```powershell
# Kumukonekta sa Intune
Connect-IntuneGhost -Interactive

# I-deploy gamit ang Intune policies
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Mahahalagang Considerations

### Testing Requirements
- **Lab Environment**: I-test muna ang lahat ng settings sa isolated environment
- **Phased Deployment**: Unti-unting palawakin upang matukoy ang mga problema
- **Rollback Plan**: Siguraduhing makakaya ninyong ibalik ang mga pagbabago kung kinakailangan
- **Documentation**: I-record kung aling mga settings ang gumagana sa inyong environment

### Potential Impact
- **User Productivity**: Ilang settings ay maaaring makaapekto sa araw-araw na workflows
- **Legacy Applications**: Mga lumang sistema ay maaaring kailangan ng mga partikular na protocols
- **Remote Access**: Isaalang-alang ang impact sa lehitimong remote administration
- **Business Processes**: I-verify na hindi nasisira ng mga settings ang mga kritikal na functions

### Security Limitations
- **Defense in Depth**: Ang Ghost ay isang layer ng security, hindi kumpleto na solusyon
- **Ongoing Management**: Ang security ay nangangailangan ng tuloy-tuloy na monitoring at updates
- **User Training**: Ang technical controls ay dapat na ipares sa security awareness
- **Threat Evolution**: Ang mga bagong attack methods ay maaaring makalusot sa kasalukuyang proteksyon

## 🎯 Attack Scenario Examples

Bagaman ang Ghost ay nakatutok sa mga karaniwang attack vectors, ang specific prevention ay nakadepende sa tamang implementation at testing:

### WannaCry-Style Attacks
- **Mitigation**: Ang `Set-Ghost -SMBv1` ay dini-disable ang vulnerable protocol
- **Consideration**: Siguraduhin na walang legacy system na nangangailangan ng SMBv1

### RDP-Based Ransomware
- **Mitigation**: Ang `Set-Ghost -RDP` ay binoblock ang remote desktop access
- **Consideration**: Maaaring kailangan ng alternative remote access methods

### Document-Based Malware
- **Mitigation**: Ang `Set-Ghost -Macros` ay dini-disable ang macro execution
- **Consideration**: Maaaring makaapekto sa lehitimong macro-enabled documents

### USB-Delivered Threats
- **Mitigation**: Ang `Set-Ghost -USBStorage -AutoRun` ay nililimitahan ang USB functionality
- **Consideration**: Maaaring makaapekto sa lehitimong USB device usage

## 🏢 Enterprise Features

### Group Policy Support
```powershell
# I-apply ang settings gamit ang Group Policy registry
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Ang mga settings ay nalalapat domain-wide pagkatapos ng GP refresh
gpupdate /force
```

### Microsoft Intune Integration
```powershell
# Lumikha ng Intune policies para sa Ghost settings
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Ang mga policies ay awtomatikong naide-deploy sa managed devices
```

### Compliance Reporting
```powershell
# Lumikha ng security assessment report
Get-Ghost | Export-Csv -Path "Security-Audit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure security posture report
Get-AzureGhost | Out-File "Azure-Security-Report.txt"
```

## 📚 Best Practices

### Pre-Deployment
1. **I-document ang Current State**: Patakbuhin ang `Get-Ghost` bago mag-implement ng mga pagbabago
2. **I-test Nang Husto**: I-validate sa non-production environment
3. **Mag-plan ng Rollback**: Alamin kung paano ibabalik ang bawat setting
4. **Stakeholder Review**: Siguraduhin na ang mga business units ay pumapayag sa mga pagbabago

### Sa Panahon ng Deployment
1. **Phased Approach**: I-deploy muna sa pilot groups
2. **I-monitor ang Impact**: Bantayan ang user complaints o system issues
3. **I-document ang Issues**: I-record ang anumang problema para sa future reference
4. **I-communicate ang Changes**: Ipaalam sa mga users ang security improvements

### Post-Deployment
1. **Regular Assessment**: Pana-panahong patakbuhin ang `Get-Ghost` upang i-verify ang settings
2. **I-update ang Documentation**: Panatilihing current ang security configurations
3. **I-review ang Effectiveness**: I-monitor ang security incidents
4. **Continuous Improvement**: I-adjust ang settings base sa threat landscape

## 🔧 Troubleshooting

### Mga Karaniwang Problema
- **Permission Errors**: Siguraduhin ang elevated PowerShell session
- **Service Dependencies**: Ilang services ay maaaring may dependencies
- **Application Compatibility**: I-test kasama ang business applications
- **Network Connectivity**: I-verify na gumagana pa rin ang remote access

### Recovery Options
```powershell
# I-enable ulit ang specific services kung kinakailangan
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Tungkol sa Author

**Jim Tyler** - Microsoft MVP para sa PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10,000+ subscribers)
- **Newsletter**: [PowerShell.News](https://powershell.news) - Weekly security intelligence
- **Author**: "PowerShell for Systems Engineers"
- **Experience**: Mga dekada ng PowerShell automation at Windows security

## 📄 License at Disclaimer

### MIT License
Ang Ghost ay ibinibigay sa ilalim ng MIT License para sa libreng paggamit, pagbabago, at pamamahagi.

### Security Disclaimer
- **Walang Warranty**: Ang Ghost ay ibinibigay "as-is" nang walang anumang uri ng warranty
- **Kailangan ng Testing**: Laging i-test muna sa non-production environments
- **Professional Guidance**: Makipag-consult sa security experts para sa production deployments
- **Operational Impact**: Ang mga authors ay hindi responsable sa anumang operational disruption
- **Comprehensive Security**: Ang Ghost ay isang component ng complete security strategy

### Support
- **GitHub Issues**: [Mag-report ng bugs o mag-request ng features](https://github.com/jimrtyler/Ghost/issues)
- **Documentation**: Gamitin ang `Get-Help <function> -Full` para sa detalyadong tulong
- **Community**: PowerShell at security community forums

---

**🔒 Palakasin ang inyong security posture gamit ang Ghost - pero laging i-test muna.**

```powershell
# Magsimula sa assessment, hindi sa assumptions
Get-Ghost
```

**⭐ I-star ang repository na ito kung nakatulong ang Ghost sa pagpapabuti ng inyong security posture!**