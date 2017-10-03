---
title: "PartnerManagement （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83e2a84f-ab25-4a7c-b8d7-0ba2dfa93095
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 790530d79b06d399e032096d64d47e65bb1dd7a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="partnermanagement-biztalk-server-sample"></a>PartnerManagement （BizTalk Server 範例）
PartnerManagement 範例示範如何管理合作對象中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境使用**ExplorerOM**管理物件。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。  
  
-   Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。 如需詳細資訊，請參閱 [檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例將示範如何使用系統管理類別從**Microsoft.BizTalk.ExplorerOM**管理合作對象的命名空間。 合作對象代表交易夥伴或後端應用程式可以與之互動的商務程序。 如需有關合作對象一般情況下，請參閱文件[合作對象](../core/parties.md)或[角色連結和服務連結角色](../core/role-links-and-service-link-roles.md)。 此範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。 本主題也包含 Windows PowerShell 範例指令碼。 此範例會示範下列作業：  
  
-   建立新的合作對象的自訂或標準的別名，並加入現有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳送埠到合作對象。  
  
-   登錄 BizTalk server 上的現有角色連結的新合作對象。  
  
-   取消登錄新的合作對象。  
  
-   正在刪除新的合作對象。  
  
## <a name="where-to-find-this-sample"></a>此範例的位置  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*> \Admin\ExplorerOM\PartnerManagement  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|PartnerManagement.cs|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]這個範例中示範的作業的來源檔案。|  
|PartnerManagement.sln 和 PartnerManagement.csproj|此範例的方案和專案檔。|  
  
## <a name="building-and-running-this-sample"></a>建置和執行此範例  
 建立範例之前，您需要四個自訂 BizTalk server 的 「 範例修改程式碼。 這是必要的因為此範例會使用與合作對象和登記任意的角色名稱相關聯的傳送埠的任意名稱。 因此，您需要提供範例的有效名稱。 為了示範這個範例，本主題說明如何先建置 PartyResolution 範例從下列目錄： \<*範例路徑*> \Orchestrations\PartyResolution。 這種方法用來確定有效的角色名稱，然後傳送連接埠名稱會出現在 BizTalk server 來示範的範例程序上。  
  
#### <a name="to-build-this-sample"></a>建置此範例  
  
1.  先確定已建置和初始化，才會有效的角色名稱和傳送連接埠名稱可由範例 PartyResolution 範例。 這在標題為 「 建置和初始化此範例 」 一節記載[PartyResolution （BizTalk Server 範例）](../core/partyresolution-biztalk-server-sample.md)。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 PartnerManagement.sln。  
  
3.  在 [方案總管] 中開啟原始程式檔 PartnerManagement.cs。  
  
4.  向下捲動至名為函式**CreateParty**和插入兩個傳送連接埠名稱，從 PartyResolution 範例，或使用 BizTalk server 環境中的有效名稱。 下列程式碼範例示範使用 PartyResolution 範例傳送埠的變更。  
  
    ```  
    // Replacing arbitrary send port names with PartyResolution send port names ===  
  
    //            myParty.SendPorts.Add(catalog.SendPorts["NormalDelivery"]);  
    //            myParty.SendPorts.Add(catalog.SendPorts["ExpressDelivery"]);  
                myParty.SendPorts.Add(catalog.SendPorts["SP_FilesToShipmentAgency1"]);  
                myParty.SendPorts.Add(catalog.SendPorts["SP_FilesToShipmentAgency2"]);  
  
    ```  
  
5.  向下捲動至名為函式**EnlistParty**和變更，讓它搜尋名為"ShipmentRole 」 角色的供應商組件的 「 foreach 迴圈 」 使用登記。 下列程式碼範例示範如何使用來自 PartyResolution 範例 ShipmentRole 變更。  
  
    ```  
                // Search for the “Shipmentrole” instead of “shipperRole”  
                Role svcRole = null;  
    //===       foreach (Role role in catalog.Assemblies[0].Roles)  
                foreach (Role role in catalog.Assemblies["Supplier"].Roles)  
                {  
    //===          if (role.Name == "ShipperRole")  
                   if (role.Name == "ShipmentRole")  
                   {  
                      svcRole = role;  
                      break;  
                   }  
                }  
  
    ```  
  
6.  向下捲動至名為函式**UnenlistParty**和變更搜尋 ShipmentRole 的供應商組件的 「 foreach 迴圈 」。 下列程式碼範例示範這項變更。  
  
    ```  
                // Search for the “ShipmentRole” instead of “shipperRole”  
                Role svcRole = null;  
    //===       foreach (Role role in catalog.Assemblies[0].Roles)  
                foreach (Role role in catalog.Assemblies["Supplier"].Roles)  
                {  
    //===          if (role.Name == "ShipperRole")  
                   if (role.Name == "ShipmentRole")  
                   {  
                      svcRole = role;  
                      break;  
                   }  
                }  
  
    ```  
  
7.  在建立並登錄 ShipmentRole 的新合作對象之後, 的範例為了立即取消-登錄合作對象，並將它刪除。 將下列程式碼變更加入至主要程序，暫停執行，並讓您檢視建立新的合作對象中登記[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
    ```  
    static void Main(string[] args)  
    {  
       CreateParty();     
       EnlistParty();     
  
       Console.WriteLine("\nNew Party created and enlisted.\n\nPress <Enter> to unenlist and delete.\n");  
       Console.ReadLine();  
  
       UnenlistParty();   
       DeleteParty();  
    }  
  
    ```  
  
8.  按一下 [ **建置** ] 功能表上的 [ **建置方案**]。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  開啟命令視窗並巡覽至下列資料夾：  
  
     \<*範例路徑*> \Admin\ExplorerOM\PartnerManagement\bin\Debug  
  
2.  執行檔案 PartnerManagement.exe。  
  
3.  此範例會顯示訊息，建立並登錄新的合作對象，當開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，然後檢視命名為新的合作對象**fedex 寄送**下**合作對象**節點。  
  
4.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，瀏覽樹狀檢視**ShipmentRole**下**Applications\BizTalk 應用程式 1\Role 連結**。 按兩下**ShipmentRole** ，並注意**ShipmentAgency1**對應至**SupplierAdvice**作業和**ShipmentAgency2**對應至**SupplierOrder**登記中的作業。  
  
5.  在命令視窗中，按下 ENTER，以允許取消範例-登錄並刪除新的合作對象。  
  
6.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，確認已從取消登錄的合作對象**ShipmentRole**和刪除從**合作對象**節點。  
  
## <a name="windows-powershell-script-example"></a>Windows PowerShell 指令碼範例  
 下列 Windows PowerShell 指令碼範例可以用於示範的相同功能**ExplorerOM**類別：  
  
```  
#===============================================================#  
#===                                                         ===#  
#=== Create a new party named "FedEx" as an example.         ===#  
#===                                                         ===#  
#=== Two Shipment agency send ports from the PartyResolution ===#  
#=== sample will be added to the party.                      ===#  
#===                                                         ===#  
#===============================================================#  
Function CreateParty  
{  
  #=== Create a party =====================#  
  $myParty = $Catalog.AddNewParty()  
  $myParty.Name = "FedEx"  
  
  #=== create a standard alias ==========================#  
  $standardAlias = $myParty.AddNewAlias()  
  $standardAlias.Name = "D-U-N-S (Dun & Bradstreet)"  
  $standardAlias.Value = "Value1"  
  
  #=== Create a custom alias ==================#  
  $customAlias = $myParty.AddNewAlias()  
  $customAlias.Name = "Telephone"  
  $customAlias.Qualifier = "100"  
  $customAlias.Value = "4255550234"  
  
  #=== Add party send ports =====================================================#  
  
  #===============================================================#  
  #=== Have to use IList directly on this sendports collection ===#  
  #=== to work around a PowerShell issue.                      ===#  
  #===============================================================#  
  $iList = [System.Collections.IList]  
  
  $sendport1 = $Catalog.SendPorts["SP_FilesToShipmentAgency1"]  
  [void] $iList.GetMethod("Add").Invoke($myParty.SendPorts,$sendport1)  
  
  $sendport2 = $Catalog.SendPorts["SP_FilesToShipmentAgency2"]  
  [void] $iList.GetMethod("Add").Invoke($myParty.SendPorts,$sendport2)  
  
  #=== Specify a signature certificate, make sure the certificate is available ===#  
  #=== in the AddressBook store of the Local Machine                           ===#  
  
  foreach ($certificate in $Catalog.Certificates)  
  {  
    if ($certificate.ShortName -eq "BR, Certisign Certificadora Digital Ltda., Certisign - Autoridade Certificadora - AC2")  
    {  
      $myParty.SignatureCert = $certificate  
    }  
  }  
  
  #=== Commit the changes ===#  
  $catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Delete the party named "FedEx"                          ===#  
#===                                                         ===#  
#===============================================================#  
Function DeleteParty  
{  
  $Catalog.RemoveParty($Catalog.Parties["FedEx"])  
  
  #=== Commit the changes ===#  
  $catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Enlist the "FedEx" party with the "ShipmentRole"        ===#  
#===                                                         ===#  
#===============================================================#  
Function EnlistParty  
{  
  $myParty = $Catalog.Parties["FedEx"]  
  
  #=== Get the "ShipmentRole" in the Supplier assembly.        ===#  
  $svcRole = $Catalog.Assemblies["Supplier"].Roles["ShipmentRole"]  
  
  #=== Enlist the party under the shipper role ===#  
  $enlistedParty = $svcRole.AddNewEnlistedParty($myParty)  
  
  #===============================================================#  
  #=== Have to use IList directly on this sendports collection ===#  
  #=== to work around a PowerShell issue.                      ===#  
  #===============================================================#  
  $iList = [System.Collections.IList]   
  
  #===============================================================#  
  #=== Example port to be used for the role's "SupplierAdvice" ===#  
  #=== operation.                                              ===#  
  #=== Using the first send port added to the new party which  ===#  
  #=== is "SP_FilesToShipmentAgency1" at index 0 in the        ===#  
  #=== sendports collection.                                   ===#  
  #===============================================================#  
  $enlistedParty.Mappings[0].SendPort = $iList.GetProperty("Item").GetValue($myParty.SendPorts,0)  
  
  #===============================================================#  
  #=== Example port to be used for the role's "SupplierOrder"  ===#  
  #=== operation.                                              ===#  
  #=== Using the second send port added to the new party which ===#  
  #=== is "SP_FilesToShipmentAgency2" at index 1 in the        ===#  
  #=== sendports collection.                                   ===#  
  #===============================================================#  
  $enlistedParty.Mappings[1].SendPort = $iList.GetProperty("Item").GetValue($myParty.SendPorts,1)  
  
  #=== Commit the changes ===#  
  $Catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Unenlist the "FedEx" party from the ShipmentRole        ===#  
#===                                                         ===#  
#===============================================================#  
Function UnenlistParty  
{  
  #=== Get the "ShipmentRole" from the Supplier assembly. ===#  
  $svcRole = $Catalog.Assemblies["Supplier"].Roles["ShipmentRole"]  
  
  #=== Remove the "FedEx" party ===#  
  foreach ($enlistedparty in $svcRole.EnlistedParties)  
  {  
    if ($enlistedparty.Party.Name -eq "FedEx")  
    {  
      $svcRole.RemoveEnlistedParty($enlistedparty)  
      break  
    }  
  }  
  
  #=== Commit the changes ===#  
  $Catalog.SaveChanges()  
}  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== This sample expects the PartyResolution sample to be built and deployed  ===#  
#=== to the BizTalk Server.                                                   ===#  
  
write-host `r`nMake sure the "PartyResolution" sample application from the Orchestrations   
write-host sample directory is deployed and running.  
write-host By default it will be listed in the BizTalk Server Administration Console  
write-host with the application name: `"BizTalk.Application.1`"`r`n  
  
$SupplierAssembly = $Catalog.Assemblies["Supplier"]  
  
#==================================================================#  
#=== Register a trap handler to discard changes on exceptions   ===#  
#=== Execution will continue in the event we want to unenlist,  ===#  
#=== and delete the party.                                      ===#  
#==================================================================#  
  
$Script:NoExceptionOccurred = $true  
$ErrorActionPreference="silentlycontinue"  
trap   
{   
  $Script:NoExceptionOccurred = $false  
  "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes and continuing execution so we can attempt to clean up the party...`r`n"  
  $Catalog.DiscardChanges()  
}  
  
CreateParty  
EnlistParty  
  
if ($Script:NoExceptionOccurred)  
{  
  Write-Host "`r`nExample Party `"FedEx`" should be created and enlisted with the `"ShipmentRole`".`r`n"  
  Write-Host You can view the results in the BizTalk Server Administration console.`r`n  
  Write-Host "Press <Enter> to unenlist and delete...`r`n"  
  Read-Host  
}  
  
UnenlistParty  
DeleteParty  
  
```  
  
 以下是從執行中的 PowerShell 範例指令碼的範例輸出。 如果指令碼執行失敗，請確定已啟用 PowerShell 指令碼根據需求注意，本主題的頂端。  
  
```  
PS C:\> .\PartnerManagement.ps1  
  
Make sure the PartyResolution sample application from the Orchestrations  
sample directory is deployed and running.  
By default it will be listed in the BizTalk Server Administration Console  
with the application name: "BizTalk.Application.1"  
  
Example Party "FedEx" should be created and enlisted with the "ShipmentRole".  
  
You can view the results in the BizTalk Server Administration console.  
  
Press <Enter> to unenlist and delete...  
```  
  
## <a name="see-also"></a>另請參閱  
 [合作對象](../core/parties.md)   
 [角色連結和服務連結角色](../core/role-links-and-service-link-roles.md)   
 [系統管理員 （BizTalk Server 範例資料夾）](../core/admin-biztalk-server-samples-folder.md)