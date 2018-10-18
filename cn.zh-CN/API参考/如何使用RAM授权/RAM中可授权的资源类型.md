# RAM中可授权的资源类型 {#concept_js4_mw4_mfb .concept}

目前，可以在RAM中进行授权的资源类型仅一种——DBInstance。

在通过RAM进行授权时，资源的描述方式如下：

|资源类型|授权策略中的资源描述方式|
|----|------------|
|DBInstance| acs:petadata:$regionid: $accountid:dbinstance/$dbinstanceid

 acs:petadata:$regionid:$accountid:dbinstance/\*

 acs:petadata:\* : \*:dbinstance/\*

 |

**说明：** 

-   所有$regionid应为某个region的id，或者“\*”。
-   所有$dbinstanceid应为某个dbinstance的id，或者“\*”。
-   accoutid 当资源拥有者的userid，或者“\*”；以此类推。

