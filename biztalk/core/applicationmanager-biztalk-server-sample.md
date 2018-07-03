---
title: ApplicationManager （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51ebe7a8-a0ca-4d2a-bf40-ec6421ba5a95
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b926f9e848ab86f5b168d46b3b0e84d85356f592
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010735"
---
# <a name="applicationmanager-biztalk-server-sample"></a>ApplicationManager （BizTalk Server 範例）
ApplicationManager 範例示範如何啟動或停止 BizTalk 應用程式使用的管理物件。  

## <a name="prerequisites"></a>必要條件  

- 您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理權限才能在此範例中使用的系統管理物件。  

- Windows PowerShell 指令碼需要 Windows PowerShell 執行原則，以允許執行指令碼。 如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。  

## <a name="what-this-sample-does"></a>此範例的用途  
 此範例示範如何使用**BtsCatalogExplorer**並**應用程式**類別**Microsoft.BizTalk.ExplorerOM**啟動和停止的已部署的命名空間 BizTalk 應用程式。 此範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。 本主題也包含 Windows PowerShell 範例指令碼。 此範例會示範下列作業：  

-   使用連接到 「 BizTalk 管理 」 資料庫**BtsCatalogExplorer**類別。  

-   尋找應用程式執行個體從**BtsCatalogExplorer**根據應用程式名稱。  

-   正在提交應用程式啟動或停止命令。  

## <a name="where-to-find-this-sample"></a>此範例的位置  
 這個範例位於下列 SDK 位置：  

 \<*範例路徑*\>\Admin\ExplorerOM\ApplicationManager  

 下表顯示此範例中的檔案，並描述其用途。  


|                                 檔案                                 |                                                 描述                                                  |
|-------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|                               Program.cs                                | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] 此範例中示範的作業的原始程式檔。 |
| ApplicationManager.sln,ApplicationManager.csproj,ApplicationManager.suo |                                  此範例的方案和專案檔。                                  |

## <a name="building-and-running-this-sample"></a>建置和執行此範例  

#### <a name="to-build-this-sample"></a>建置此範例  

1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 ApplicationManager.sln。  

2. 按一下 [ **建置** ] 功能表上的 [ **建置方案**]。  

#### <a name="to-run-this-sample"></a>執行此範例  

1. 開啟命令視窗並巡覽至下列資料夾：  

    \<*範例路徑*\>\Admin\ExplorerOM\ApplicationManager\bin\Debug  

2. 執行檔案 ApplicationManager.exe 提供下列兩個已排序命令列引數：  

   - **\<啟動&#124;停止\>** 第一個引數是要在部署的應用程式上執行的作業。  

   - **\<ApplicationName\>** 第二個引數是所部署的應用程式的名稱。  

     例如：  

   ```  
   ApplicationManager.exe stop MyBizTalkApp  
   ```  

    使用不足的命令列參數執行此範例顯示使用語法。 例如：  

   ```  
   Usage:  

   ApplicationManager <start|stop> <Application Name>  

    Where:  
     <Application Name> = The name of the application that needs to be changed  

   Example: ApplicationManager start Application1  
   ```  

## <a name="windows-powershell-script-example"></a>Windows PowerShell 指令碼範例  
 下列 Windows PowerShell 指令碼片段，可以用來示範相同的功能**ExplorerOM**類別：  

```  
#=== Make sure the ExplorerOM assembly is loaded ===#  

[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  

#=== Connect the BizTalk Management database ===#  

$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  

#=== Loop through applications in the catalog trying to find a name match ===#  

foreach($app in $Catalog.Applications)  
{  
    if ($($app.Name) -ieq $args[1])  
    {  

        #=== The first command-line argument should be "start" or "stop" ===#  

        if ($args[0] -ieq "start")  
        {  
            Write-Host `r`nIssuing start command to $app.Name...`r`n  
            $app.Start([Microsoft.BizTalk.ExplorerOM.ApplicationStartOption] "StartAll")  
            $Catalog.SaveChanges()  
        }  

        if ($args[0] -ieq "stop")  
        {  
            Write-Host `r`nIssuing stop command to $app.Name...`r`n  
            $app.Stop([Microsoft.BizTalk.ExplorerOM.ApplicationStopOption] "StopAll")  
            $Catalog.SaveChanges()  
        }  

    }  
}  
```  

 指令碼必須要有相同的命令列引數為[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]範例。 執行 Windows PowerShell 指令碼，來啟動已部署的 BizTalk 應用程式的範例如下：  

```  
PS C:\> .\ApplicationManager.ps1 start MyBizTalkApp  

Issuing start command to MyBizTalkApp ...  
```  

## <a name="see-also"></a>另請參閱  
 [Admin-ExplorerOM (BizTalk Server Samples 資料夾)](../core/admin-explorerom-biztalk-server-samples-folder.md)