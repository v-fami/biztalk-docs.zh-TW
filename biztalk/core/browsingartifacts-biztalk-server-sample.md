---
title: "BrowsingArtifacts （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b63c0833-3445-4361-a8eb-63837017edf8
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32e29f945d9d20cd2ea998e0fa05eda6b52174ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="browsingartifacts-biztalk-server-sample"></a>BrowsingArtifacts （BizTalk Server 範例）
BrowsingArtifacts 範例示範如何列舉 BizTalk 成品和屬性。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。  
  
-   Windows PowerShell 指令碼範例需要 Windows PowerShell 執行原則來允許指令碼執行。 如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例示範如何使用**BtsCatalogExplorer**類別從**Microsoft.BizTalk.ExplorerOM**列舉成品，並報告其屬性的命名空間。 此範例所產生的報表中包含下列成品： 協調流程、 連接埠、 組件、 合作對象，以及轉換。 這個範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。 本主題中，也會提供 Windows PowerShell 範例指令碼。  
  
## <a name="where-to-find-this-sample"></a>此範例的位置  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*> \Admin\ExplorerOM\BrowsingArtifacts  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|BrowsingArtifacts.cs|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]這個範例中示範的作業的來源檔案。|  
|BrowsingArtifacts.sln，BrowsingArtifacts.csproj，BrowsingArtifacts.suo|此範例的方案和專案檔。|  
  
## <a name="building-and-running-this-sample"></a>建置和執行此範例  
  
#### <a name="to-build-this-sample"></a>建置此範例  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 BrowsingArtifacts.sln。  
  
2.  按一下 [ **建置** ] 功能表上的 [ **建置方案**]。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  開啟命令視窗並巡覽至下列資料夾：  
  
     \<*範例路徑*> \Admin\ExplorerOM\BrowsingArtifacts\bin\Debug  
  
2.  執行檔案 BrowsingArtifacts.exe。  
  
## <a name="windows-powershell-script-example"></a>Windows PowerShell 指令碼範例  
 下列 Windows PowerShell 指令碼可以用於示範的相同功能**ExplorerOM**類別：  
  
```  
Function EnumOrchestrations($catalog)  
{  
    Write-Host `r`n======================  
    Write-Host ===  ORCHESTRATIONS  ===  
    Write-Host ======================`r`n   
  
    #=== Enumerating the assemblies and pulling orchestration information ===#  
  
    foreach($assembly in $catalog.Assemblies)  
    {  
        foreach($orch in $assembly.Orchestrations)  
        {  
            #=== We can’t report the host if it is not hosted or enlisted ===#  
            if ($orch.Status -ieq "Unenlisted")  
            {  
                Write-Host Name : $orch.Fullname`r`nHost : N/A`r`nStatus : $orch.Status  
            }  
            else  
            {  
                Write-Host Name : $orch.Fullname`r`nHost : $orch.Host.Name`r`nStatus : $orch.Status  
            }  
  
            #=== Reporting port types and operations ===#  
            foreach($port in $orch.Ports)  
            {  
                Write-Host "`tPort:"$port.PortType.FullName  
  
                foreach($portop in $port.PortType.Operations)  
                {  
                    Write-Host "`t`tOperation:"$portop.Name  
                }  
            }  
  
            #=== Reporting Used roles ===#  
            foreach($role in $orch.UsedRoles)  
            {  
                Write-Host "`tRole:"$role.Name"`("$role.ServiceLinkType"`)"  
  
                foreach($EnlistedParty in $role.EnlistedParties)  
                {  
                    Write-Host "`t`tParty:"$Enlistedparty.Party.Name  
                }  
            }  
  
            #=== Reporting implemented roles ===#  
            foreach($role in $orch.ImplementedRoles)  
            {  
                Write-Host "`tRole:"$role.Name"`("$role.ServiceLinkType"`)"  
            }  
  
            Write-Host  
        }  
    }  
}  
  
Function EnumOtherArtifacts($catalog)  
{  
    Write-Host `r`n======================  
    Write-Host "===   ASSEMBLIES   ==="  
    Write-Host ======================`r`n   
  
    foreach($assembly in $catalog.Assemblies)  
    {  
        Write-Host $assembly.Name  
    }  
  
    Write-Host `r`n======================  
    Write-Host "===     HOSTS      ==="  
    Write-Host ======================`r`n   
  
    foreach($btshost in $catalog.Hosts)  
    {  
        Write-Host $btshost.Name"`($($btshost.Type)`)"  
    }  
  
    Write-Host `r`n======================  
    Write-Host "===    PARTIES     ==="  
    Write-Host ======================`r`n   
  
    foreach($party in $catalog.Parties)  
    {  
        Write-Host $party.Name  
  
        foreach($sendport in $party.SendPorts)  
        {  
            Write-Host "`tSendPort:"$sendport.Name  
        }  
  
        foreach($alias in $party.Aliases)  
        {  
            Write-Host "`tAlias:"$alias.Name":"$alias.Qualifier"="$alias.Value  
        }  
    }  
  
    Write-Host `r`n======================  
    Write-Host "===   TRANSFORMS   ==="  
    Write-Host ======================`r`n   
  
    foreach($transform in $catalog.Transforms)  
    {  
        Write-Host $transform.FullName":`r`n`t"$transform.SourceSchema.Fullname"==>"$transform.TargetSchema.Fullname`r`n  
    }  
}  
  
#=== Main Script Body ===#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== All reporting is performed in the following two functions ===#  
  
EnumOrchestrations $Catalog  
EnumOtherArtifacts $Catalog  
```  
  
 執行 Windows PowerShell 指令碼，以及範例輸出中的範例如下：  
  
```  
PS C:\> .\BrowsingArtifacts.ps1  
  
======================  
=== ORCHESTRATIONS ===  
======================  
  
Name : Microsoft.BizTalk.Edi.BatchSuspendOrchestration.BatchElementSuspendService  
Host : BizTalkServerApplication  
Status : Enlisted  
  
Name : Microsoft.BizTalk.Edi.BatchingOrchestration.BatchingService  
Host : BizTalkServerApplication  
Status : Enlisted  
  
Name : Microsoft.BizTalk.Edi.RoutingOrchestration.BatchRoutingService  
Host : BizTalkServerApplication  
Status : Enlisted  
  
Name : EAIOrchestrations.EAIProcess  
Host : N/A  
Status : Unenlisted  
        Port: EAIOrchestrations.ReceiveReqType  
                Operation: Operation_1  
        Port: EAIOrchestrations.SendDeclineType  
                Operation: Operation_1  
        Port: EAIOrchestrations.SendToERPType  
                Operation: Operation_1  
  
Name : B2BOrchestrations.B2BProcess  
Host : BizTalkServerApplication  
Status : Started  
        Port: B2BOrchestrations.ReceivePO_Type  
                Operation: Operation_1  
        Port: B2BOrchestrations.SendPOConfirmed_Type  
                Operation: Operation_1  
        Port: B2BSchemas.localhost.Process_.Process  
                Operation: ReceivePO  
        Port: B2BOrchestrations.ReceiveASN_Type  
                Operation: Operation_1  
        Port: B2BOrchestrations.ReceiveInvoice_Type  
                Operation: Operation_1  
        Port: B2BOrchestrations.PortType_PaymentVoucherArchive  
                Operation: Operation_1  
        Port: B2BSchemas.localhost1.Payment_Service_.Payment_Service  
                Operation: ProcessPayment  
        Port: B2BOrchestrations.SendPaymentAck_Type  
                Operation: Operation_1  
  
======================  
===   ASSEMBLIES   ===  
======================  
  
Microsoft.BizTalk.GlobalPropertySchemas  
Microsoft.BizTalk.DefaultPipelines  
Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties  
MQSeries  
Microsoft.BizTalk.Hws.HwsPromotedProperties  
Microsoft.BizTalk.Hws.HwsSchemas  
Microsoft.BizTalk.KwTpm.StsDefaultPipelines  
Microsoft.BizTalk.KwTpm.RoleLinkTypes  
mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
Microsoft.BizTalk.Edi.BaseArtifacts  
Microsoft.BizTalk.Edi.EdiPipelines  
Microsoft.BizTalk.Edi.BatchingOrchestration  
Microsoft.BizTalk.Edi.RoutingOrchestration  
Microsoft.BizTalk.Edi.EdiIntPipelines  
EAISchemas  
EAIOrchestrations  
B2BSchemas  
B2BOrchestrations  
WCFArtifacts  
FFDisassemblerWalkthrough  
BTSWhitespaceTest  
  
======================  
===     HOSTS      ===  
======================  
  
BizTalkServerApplication (InProcess)  
BizTalkServerIsolatedHost (Isolated)  
  
======================  
===    PARTIES     ===  
======================  
  
PartyB  
        Alias: Organization : OrganizationName = PartyB  
  
======================  
===   TRANSFORMS   ===  
======================  
  
EAISchemas.FFRequestDeniedMap :  
         EAISchemas.FlatFileSchema1 ==> EAISchemas.RequestDenied  
  
EAISchemas.RequestDeniedMap :  
         EAISchemas.Request ==> EAISchemas.RequestDenied  
  
B2BSchemas.InvoiceToPayment :  
         B2BSchemas.CommonInvoice ==> B2BSchemas.localhost1.Reference  
  
B2BSchemas.MapToCommonPO :  
         B2BSchemas.PO ==> B2BSchemas.localhost.Reference  
  
BizTalkArtifacts.ConcatMap :  
         BizTalkArtifacts.InputSchema ==> BizTalkArtifacts.OutputSchema  
  
FFDisassemblerWalkthrough.Map1 :  
         FFDisassemblerWalkthrough.Body ==> FFDisassemblerWalkthrough.Body  
  
BTSWhitespaceTest.Map1 :  
         FFDisassemblerWalkthrough.Body ==> BTSWhitespaceTest.Schema1  
```  
  
## <a name="see-also"></a>另請參閱  
 [系統管理員 ExplorerOM （BizTalk Server 範例資料夾）](../core/admin-explorerom-biztalk-server-samples-folder.md)