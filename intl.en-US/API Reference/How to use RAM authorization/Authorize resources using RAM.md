# Authorize resources using RAM {#concept_js4_mw4_mfb .concept}

Currently, RAM only supports authorizing DBInstance.

The authorization rules of RAM are listed as follows.

|Resource|Description in an authorization policy|
|--------|--------------------------------------|
|DBInstance| acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid

 acs:petadata:$regionid:$accountid:dbinstance/\*

 acs:petadata:\* : \*:dbinstance/\*

 |

**Note:** 

-   $regionid: the ID of a region. Use an asterisk \(\*\) to indicate the ID of any region.
-   $dbinstanceid: the ID of a DBInstance. Use an asterisk \(\*\) to indicate the ID of any instance.
-   $accoutid: the userid of the resource owner. Use an asterisk \(\*\) to indicate the ID of any account.

