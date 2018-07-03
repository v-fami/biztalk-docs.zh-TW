---
title: ReceiveLocations （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87d75941-3973-4166-91b0-f1192b25a804
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df19296fcf6c93d582034464402597248335e826
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019166"
---
# <a name="receivelocations-biztalk-server-sample"></a>ReceiveLocations （BizTalk Server 範例）
範例會示範如何建立 ReceiveLocations 接收中的位置[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中的使用**ExplorerOM**管理物件。 如需詳細資訊在一般情況下接收位置，請參閱 <<c0> [ 接收位置](../core/receive-locations.md)。  

## <a name="prerequisites"></a>必要條件  

- 您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理權限才能在此範例中使用的系統管理物件。  

- Windows PowerShell 指令碼需要 Windows PowerShell 執行原則，以允許執行指令碼。 如需詳細資訊，請參閱 [檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。  

## <a name="what-this-sample-does"></a>此範例的用途  
 此範例示範如何使用**ExplorerOM**系統管理的類別，來建立和設定接收埠和接收位置。 本主題也包含 Windows PowerShell 範例指令碼。 此範例會執行下列作業：  

-   建立新接收埠命名為 「 我的接收埠 」。  

-   建立新接收位置與新的連接埠相關聯，而且設定為使用 HTTP 傳輸通訊協定。  

-   此範例也會包含程序來刪除和列舉接收埠和位置的範例。  

## <a name="where-to-find-this-sample"></a>此範例的位置  
 這個範例位於下列 SDK 位置：  

 \<*範例路徑*\> \Admin\ExplorerOM\ReceiveLocations  

 下表顯示此範例中的檔案，並描述其用途。  


|                     檔案                      |                                                   描述                                                    |
|--------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
|               ReceiveLocations.cs                | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] 此範例中示範的作業的原始程式檔。 |
| ReceiveLocations.sln 和 ReceiveLocations.csproj |                                   此範例的方案和專案檔。                                    |

## <a name="building-and-running-this-sample"></a>建置和執行此範例  

#### <a name="to-build-this-sample"></a>建置此範例  

1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 ReceiveLocations.sln。  

2. 按一下 [ **建置** ] 功能表上的 [ **建置方案**]。  

#### <a name="to-run-this-sample"></a>執行此範例  

1. 開啟命令提示字元，使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理權限。  

2. 若要變更\<*樣本*\>\Admin\ExplorerOM\ReceiveLocations\bin\debug 目錄。  

3. 執行 ReceiveLocations.exe。  

4. 檢視新的接收埠和接收位置使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

## <a name="windows-powershell-script-example"></a>Windows PowerShell 指令碼範例  
 下列 PowerShell 範例指令碼會示範相同的作業為[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]版本。 請確定指令碼執行原則已正確設定如本主題中的需求 > 一節中所述。  

```  
#==================================================================#  
#===                                                            ===#  
#=== Create a new receive port named "My Receive Port" as an    ===#  
#=== example.                                                   ===#  
#===                                                            ===#  
#=== A new receive location will also be created and associated ===#  
#=== with the receive port.                                     ===#  
#===                                                            ===#  
#==================================================================#  
Function CreateAndConfigureReceiveLocation()  
{  
   $myreceivePort = $catalog.AddNewReceivePort($false)  

   #=== Note that if you don’t set the name property for the receieve port, ===#  
   #=== it will create a new receive location and add it to the receive     ===#     
   #=== port.                                                               ===#  

   $myreceivePort.Name = "My Receive Port"  

   #=== Create a new receive location and add it to the receive port ===#  
   $myreceiveLocation = $myreceivePort.AddNewReceiveLocation()  

   foreach ($handler in $catalog.ReceiveHandlers)  
   {  
      if ($handler.TransportType.Name -eq "HTTP")  
      {  
         $myreceiveLocation.ReceiveHandler = $handler  
         break  
      }  
   }  

   #=== Associate a transport protocol and URI with the receive location. ===#   
   $myreceiveLocation.TransportType = $catalog.ProtocolTypes["HTTP"]  
   $myreceiveLocation.Address = "/home"  

   #=== Assign the first receive pipeline found to process the message. ===#  
   foreach ($pipeline in $catalog.Pipelines)  
   {  
      if ($pipeline.Type -eq [Microsoft.Biztalk.ExplorerOM.PipelineType] "Receive")  
      {  
         $myreceiveLocation.ReceivePipeline = $pipeline  
         break  
      }  

      #=== Enable the receive location. ===#  
      $myreceiveLocation.Enable = $true  

      #=== Optional Properties ===#  
      $myreceiveLocation.FragmentMessages = [Microsoft.BizTalk.ExplorerOM.Fragmentation] "Yes"  
      $myreceiveLocation.ServiceWindowEnabled = $false    
   }  

    #=== Try to commit the changes made so far. If the commit fails, ===#  
    #=== roll back all changes.                                      ===#  
    $catalog.SaveChanges()  
}  

#===============================================================#  
#===                                                         ===#  
#=== Delete the receive port named "My Receive Port"         ===#  
#===                                                         ===#  
#===============================================================#  
Function DeleteReceivePort  
{  
  $receivePort = $catalog.ReceivePorts["My Receive Port"]  

  if ($receivePort -ne $null)  
  {  

    #=== Enumerate the receive locations. ===#  
    foreach ($location in $receivePort.ReceiveLocations)  
    {  
        if (($location.Name -eq "Receive Location1") -and ($location.IsPrimary -eq $false))  
        {  
          $receivePort.RemoveReceiveLocation($location)  
        }  
    }  

    $catalog.RemoveReceivePort($receivePort)    

    #=== Try to commit the changes made so far. If the commit fails, ===#  
    #=== roll back all changes in the trap handler.                  ===#  
    $catalog.SaveChanges()  
  }  
}  

#================================================================#  
#===                                                          ===#  
#=== Enumerate the receive ports and their receive locations. ===#  
#===                                                          ===#  
#================================================================#  
Function EnumerateReceiveLocations  
{  
   #=== Enumerate the receive locations in each of the receive ports. ===#  
   foreach ($receivePort in $catalog.ReceivePorts)  
   {  
      Write-host "`r`n$($receivePort.Name)"  

      #=== Enumerate the receive locations. ===#  
      foreach ($location in $receivePort.ReceiveLocations)  
      {  
         Write-Host "`t$($location.Name)"  
      }  
   }  

   Write-host ""  
}  

#===================#  
#=== Main Script ===#  
#===================#  

#=== Make sure the ExplorerOM assembly is loaded ===#  

[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  

#=== Connect to the BizTalk Management database ===#  

$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  

#==================================================================#  
#=== Register a trap handler to discard changes on exceptions   ===#  
#=== Execution will continue in the event we want to delete the ===#  
#=== receive port.                                              ===#  
#==================================================================#  

$Script:NoExceptionOccurred = $true  
$ErrorActionPreference="silentlycontinue"  
trap   
{   
  $Script:NoExceptionOccurred = $false  
  "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes and continuing execution so we can attempt to clean up the receive port...`r`n"  
  $Catalog.DiscardChanges()  
}  

#=== Create the new receive port with its new receive location ===#  
CreateAndConfigureReceiveLocation  
Write-Host "`r`n`"My Receive Port`" created."  

#=== Enumerate each receive port along with its receive locations ===#  
Write-Host "`r`nEnumerating all receive ports...`r`n"  
EnumerateReceiveLocations  

#=== Prompt before removing the new example receive port and location ===#  
Write-Host "`r`nPress <ENTER> to delete `"My Receive Port`"..."  
Read-Host  
DeleteReceivePort  

#=== Enumerate again to show the receive port and location was removed ===#  
Write-Host "`r`nEnumerating all receive ports to show `"My Receive Port`" was removed...`r`n"  
EnumerateReceiveLocations  

```  

 以下是從顯示的接收埠和位置建立並刪除 PowerShell 指令碼執行的範例輸出：  

```  
PS C:\> .\ReceiveLocations.ps1  

"My Receive Port" created.  

Enumerating all receive ports...  

BatchControlMessageRecvPort  
        BatchControlMessageRecvLoc  

ResendReceivePort  
        ResendReceiveLocation  

HelloWorldReceivePort  
        HelloWorldReceiveLocation  

CBRReceivePort  
        CBRReceiveLocation  

RP_ReceivePOFromInternal  
        RL_ReceivePOFromInternal  

RP_ShipmentAgency1_OrderFiles  
        RL_ShipmentAgency1_OrderFiles  

RP_ShipmentAgency2_OrderFiles  
        RL_ShipmentAgency2_OrderFiles  

RP_ReceivePOFromBuyer  
        RL_ReceivePOFromBuyer  

RP_Receive_ShipmentAgency_Ack  
        RL_Receive_ShipmentAgency_Ack  

My Receive Port  
        Receive Location1  

Press <ENTER> to delete "My Receive Port"...  

Enumerating all receive ports to show "My Receive Port" was removed...  

BatchControlMessageRecvPort  
        BatchControlMessageRecvLoc  

ResendReceivePort  
        ResendReceiveLocation  

HelloWorldReceivePort  
        HelloWorldReceiveLocation  

CBRReceivePort  
        CBRReceiveLocation  

RP_ReceivePOFromInternal  
        RL_ReceivePOFromInternal  

RP_ShipmentAgency1_OrderFiles  
        RL_ShipmentAgency1_OrderFiles  

RP_ShipmentAgency2_OrderFiles  
        RL_ShipmentAgency2_OrderFiles  

RP_ReceivePOFromBuyer  
        RL_ReceivePOFromBuyer  

RP_Receive_ShipmentAgency_Ack  
        RL_Receive_ShipmentAgency_Ack  

```  

## <a name="see-also"></a>另請參閱  
 [接收位置](../core/receive-locations.md)   
 [Admin-ExplorerOM (BizTalk Server Samples 資料夾)](../core/admin-explorerom-biztalk-server-samples-folder.md)