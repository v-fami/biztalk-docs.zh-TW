---
title: UnenlistParties （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, parties
- parties, examples
- parties, unenlisting
- examples, administering
- administering, examples
ms.assetid: a751a0fc-ca94-4610-a8aa-db3a24159334
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34cbb94dff7211a157fc492c1157fa379236641e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973468"
---
# <a name="unenlistparties-biztalk-server-sample"></a>UnenlistParties （BizTalk Server 範例）
UnenlistParties 範例示範如何取消登錄與已部署之 BizTalk Server 組件關聯的所有合作對象。  
  
> [!WARNING]
>  如果在部署後不需要部署指令碼，就應該將其移除。 必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。  
  
-   Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。 如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 此範例是以 Visual C# 撰寫而成，並使用 [BizTalk 總管] 物件模型中的物件，執行下列作業：  
  
-   查詢特定組件。  
  
-   擷取與該組件相關聯的所有角色。  
  
-   取消登錄與每個這類角色相關聯的所有合作對象。  
  
-   處理任何錯誤，讓有意義的資訊能傳回給使用者。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*\>\Admin\ExplorerOM\UnenlistParties\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|App.ico, AssemblyInfo.cs, UnenlistParties.csproj, UnenlistParties.sln, UnenlistParties.cs|專案、解決方案和原始程式檔，用於建置 Visual C# 命令列應用程式，以取消登錄特定組件的所有合作對象。|  
  
### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟解決方案檔 UnenlistParties.sln。  
  
2.  在**建置**功能表上，選取**建置方案**。  
  
### <a name="to-run-this-sample"></a>執行此範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\Admin\ExplorerOM\UnenlistParties\bin\Debug\  
  
2.  執行 UnenlistParties.exe 檔案，它會傳遞下列其中一個命令列引數：  
  
    -   **\<** ***AssemblyName* \>** 。 凡是與該組件名稱相關聯的合作對象都將取消登錄。 如果組件名稱包含空格，請用引號括住該名稱。  
  
    -   **/?.** 顯示說明。  
  
     例如：  
  
    ```  
    UnenlistParties "My BizTalk Assembly.dll"  
    ```  
  
     -或-  
  
    ```  
    UnenlistParties /?  
    ```  
  
## <a name="windows-powershell-script-example"></a>Windows Powershell 指令碼範例  
 下列 Windows Powershell 指令碼片段可以用來示範的相同功能**ExplorerOM**類別：  
  
```  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=====================================================#  
#=== If no assembly name is specified, just list   ===#  
#=== the assemblies, roles and partyies enlisted.  ===#  
#=====================================================#  
  
if ($args[0] -eq $null)  
{  
  Write-Host `r`n===========================================================  
  Write-Host No assembly name provided for party unenlist operation.  
  Write-Host Listing Parties for each assembly on local BizTalk Server:  
  Write-Host ===========================================================`r`n  
  
  foreach ($assembly in $Catalog.Assemblies)  
  {  
    write-host $Assembly.Name`r`n  
  
    foreach ($role in $Assembly.Roles)  
    {  
      write-host `t($role.name)  
  
      foreach($party in $role.EnlistedParties)  
      {  
        Write-Host `t`t($party.Party.Name)  
      }  
      write-host  
    }  
  }  
  
  write-host  
}  
  
#=====================================================#  
#=== If assembly name is specified, remove parties ===#  
#=== enlisted in all roles for the assembly.       ===#  
#=====================================================#  
  
else  
{  
  $Assembly = $Catalog.Assemblies[$args[0]]  
  
  if ($assembly -eq $null)  
  {  
    write-host Assembly named $args[0] not found.`r`n  
  }   
  
  else  
  {  
    write-host `r`nUnenlisting parties from all roles in ($Assembly.Name)`r`n  
  
    foreach ($role in $Assembly.Roles)  
    {  
  
      $count = $role.EnlistedParties.count  
  
      for($c=0; $c -lt $count; $c++)  
      {  
        #==========================================================#  
        #=== Array index stays at zero because the collection   ===#  
        #=== changes after each item is removed.                ===#  
        #==========================================================#  
  
        $party = $role.EnlistedParties[0]  
  
        Write-Host Unenlisting ($party.Party.Name) from ($role.Name)...  
        $role.RemoveEnlistedParty($party)  
        Write-Host done.`r`n  
      }  
    }  
  
    write-Host Comitting changes...  
    $catalog.SaveChanges()  
    Write-Host done.`r`n  
  }  
}  
  
```  
  
 下列指令碼輸出是由從供應商組件的一部分 PartyResolution 範例取消登錄合作對象產生。 PartyResolution 範例位於\<*範例路徑*\>\Admin\Orchestrations\PartyResolution 目錄。  
  
```  
PS C:\> .\UnenlistParties.ps1 Supplier  
  
Unenlisting parties from all roles in Supplier  
  
Unenlisting ShipmentAgency1 from ShipmentRole ...  
done.  
  
Unenlisting ShipmentAgency2 from ShipmentRole ...  
done.  
  
Unenlisting BuyerAgency from Buyer ...  
done.  
  
Comitting changes...  
done.  
```  
  
## <a name="see-also"></a>請參閱  
 [Admin-ExplorerOM (BizTalk Server Samples 資料夾)](../core/admin-explorerom-biztalk-server-samples-folder.md)