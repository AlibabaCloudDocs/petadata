# Authorize resources using RAM {#concept_js4_mw4_mfb .concept}

Currently, RAM only supports authorizing DBInstance.

The resource is described as follows when authorized as a RAM user.

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

