---
title: "DeleteParty （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, parties
- parties, examples
- deleting, parties
- examples, administering
- parties, deleting
- administering, examples
ms.assetid: 8161af7d-76ef-4df5-81c8-f0f5c81df9a8
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d07793400f0217ef2f3ddcc637265f186647a00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deleteparty-biztalk-server-sample"></a>DeleteParty （BizTalk Server 範例）
DeleteParty 範例示範如何刪除指定的合作對象。  
  
> [!WARNING]
>  如果在部署後不需要部署指令碼，就應該將其移除。 必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。  
  
> [!NOTE]
>  您必須先建立合作對象，才可以將它刪除。 這是執行其中一種方式執行[PartyResolution （BizTalk Server 範例）](../core/partyresolution-biztalk-server-sample.md)範例。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。  
  
-   Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。 如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例中，撰寫 Microsoft Visual C# 中，使用 BizTalk 總管物件模型 (ExplorerOM)，物件會執行下列作業：  
  
-   查詢指定的合作對象。  
  
-   刪除該合作對象。  
  
-   處理任何錯誤，讓有意義的資訊能傳回給使用者。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*> \Admin\ExplorerOM\DeleteParty\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|App.ico、AssemblyInfo.cs、DeleteParty.csproj、DeleteParty.sln、DeleteParty.cs|專案、方案和原始程式檔，用於建置 Visual C# 命令列應用程式，以移除指定的合作對象。|  
  
### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟方案檔 DeleteParty.sln。  
  
2.  按一下 [ **建置** ] 功能表上的 [ **建置方案**]。  
  
### <a name="to-run-this-sample"></a>執行此範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*> \Admin\ExplorerOM\DeleteParty\bin\Debug\  
  
2.  執行 DeleteParty.exe 檔案，它會傳遞下列兩個命令列引數：  
  
    -   **\<**   
         ***PartyName* >。** 要刪除的合作對象的名稱。 如果合作對象名稱包含空格，請用引號括住該名稱。  
  
    -   **/?.** 顯示說明。  
  
     例如：  
  
    ```  
    DeleteParty "My Party #3"  
    ```  
  
     -或-  
  
    ```  
    DeleteParty /?  
    ```  
  
## <a name="windows-powershell-script-example"></a>Windows Powershell 指令碼範例  
 下列 Windows PowerShell 指令碼片段可以用來示範的相同功能**ExplorerOM**類別：  
  
```  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=======================================#  
#=== If no party name is specified   ===#  
#=== just list the parties.          ===#  
#=======================================#  
  
if ($args[0] -eq $null)  
{  
  Write-Host `r`nNo party name provided for delete operation.`r`n`r`nListing Parties on local Biztalk Server:  
  
  $Catalog.Parties | Format-List Name  
}  
  
#==========================================#  
#=== Delete the specified party by name ===#  
#==========================================#  
  
else  
{  
  $party = $Catalog.Parties[$args[0]]  
  Write-Host `r`nRemoving Party named `"($args[0])`"`r`n  
  $catalog.RemoveParty($party)  
  $catalog.SaveChanges()  
}  
```  
  
 指令碼範例需要單一合作對象名稱做為命令列引數傳遞。  它會依名稱尋找該合作對象，並嘗試將它刪除。  如果沒有命令列引數傳遞給它，指令碼會列出本機 Biztalk 伺服器上的所有合作對象。 以下是從指令碼的範例輸出：  
  
```  
PS C:\> .\DeletePart.ps1  
  
No party name provided for delete operation.  
  
Listing Parties on local Biztalk Server:  
  
Name : Party1  
  
Name : Party3  
  
Name : Party2  
  
PS C:\> .\DeletePart.ps1 Party3  
  
Removing Party named " Party3 "  
  
PS C:\> .\DeletePart.ps1  
  
No party name provided for delete operation.  
  
Listing Parties on local Biztalk Server:  
  
Name : Party1  
  
Name : Party2  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [系統管理員 ExplorerOM （BizTalk Server 範例資料夾）](../core/admin-explorerom-biztalk-server-samples-folder.md)