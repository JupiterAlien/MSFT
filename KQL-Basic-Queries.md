## Hunting for clicks in URLs


       let domains =  pack_array("suspicious.domain.here", "suspicious.domain.here", "suspicious.domain.here");
       DeviceNetworkEvents
       | where Timestamp > ago(15d)
       | where RemoteUrl in~ (domains)
       | distinct Timestamp, DeviceName, InitiatingProcessAccountName, InitiatingProcessAccountUpn, InitiatingProcessParentFileName, RemoteUrl
       | sort by Timestamp desc


       UrlClickEvents
       | where Timestamp > ago(15d)
       | where Url contains "123matka" or UrlChain contains "123matka"
       | summarize count(RemoteUrl) by Timestamp, DeviceName, RemoteUrl


## Hunting for suspicious Inbox Rules    

    let startTime = ago(30d);
    let endTime = now();
    CloudAppEvents
    | where Timestamp between(startTime .. endTime)
    | where ActionType contains "rule"
    | where AccountDisplayName == "USER_NAME_HERE"
    | where Application == "Microsoft Exchange Online"
    | where RawEventData has_any("Delete", "Send", "Reply")
    | project Timestamp, AccountDisplayName, Application, ActionType, AccountObjectId, IPAddress, IsExternalUser, IsImpersonated
  
 
## Hunting for hash-related activity
 
 Change the hash type according to your necessity / IOC. 
 
    let fileHash = "paste hash here";
    find in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents)
    where SHA256 == fileHash or InitiatingProcessSHA256 == fileHash
    project Timestamp, DeviceName, LocalIP, ActionType, FileName, InitiatingProcessFileName, ProcessCommandLine, RemoteUrl, RemoteIP, SHA256, SHA1, MD5
  
 
## Hunting for domain-related actvity
 
    let domainName= 'paste domain here';
    DeviceNetworkEvents
    | where RemoteUrl =~domainName
    | project DeviceName, LocalIP, LocalPort, ActionType, Timestamp, RemoteUrl, Protocol, RemoteIP, RemotePort
  
## Hunting for IP-related activity

    DeviceNetworkEvents
    | where RemoteIP == "paste remote IP here"
    | project Timestamp, DeviceName, LocalIP, LocalPort, RemoteUrl, RemoteIP, RemotePort, InitiatingProcessFileName, InitiatingProcessCommandLine
  
  
## Hunting for activity related to multiple URLs / IOCs

    DeviceNetworkEvents
    | where RemoteUrl in~ ("paste","the","urls","or","domains","here","separeted","by","commas")
    | project DeviceName, LocalIP, LocalPort, ActionType, Timestamp, RemoteUrl, Protocol, RemoteIP, RemotePort





