# KQL queries seeking for hits related to Nokoyama ransomware. 

The IOCs were extracted from Trendmicro's report: https://www.trendmicro.com/en_us/research/22/c/nokoyawa-ransomware-possibly-related-to-hive-.html



    find in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents)
    where SHA256 in~ ("a70729b3241154d81f2fff506e5434be0a0c381354a84317958327970a125507","2ef9a4f7d054b570ea6d6ae704602b57e27dee15f47c53decb16f1ed0d949187",
    "c170717a69847bb7b050832c55fcd2a214e9180c8cde5f86088bd4e5266e2fd9",
    "a290ce75c6c6b37af077b72dc9c2c347a2eede4fafa6551387fa8469539409c7","e097cde0f76df948f039584045acfa6bd7ef863141560815d12c3c6e6452dce4")
    | top 1000 by Timestamp
    | sort by DeviceName, Timestamp
