---
title: CBR （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: add16683-4090-4854-8d6e-923b58937e9d
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a4f27cd62a546213041be594094ff6b5e39274b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005319"
---
# <a name="cbr-biztalk-server-sample"></a>CBR （BizTalk Server 範例）
CBR 範例示範如何使用**ExplorerOM**系統管理物件來加入和設定新傳送埠的 BizTalk 訊息的內容型路由。  

## <a name="prerequisites"></a>必要條件  

- 此範例需要將執行中的 setup.bat 部署 CBRSample \<*範例路徑*\>\Messaging\CBRSample 目錄。  

- 您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理權限才能在此範例中使用的系統管理物件。  

- Windows PowerShell 指令碼範例需要 Windows PowerShell 執行原則來允許指令碼執行。 如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。  

## <a name="what-this-sample-does"></a>此範例的用途  
 此範例示範如何使用中的系統管理物件**Microsoft.BizTalk.ExplorerOM** CBRApplication 範例來新增兩個新的連接埠的命名空間。 這些新的連接埠是 CBRApplication 的範例連接埠。 將訊息路由至假設的 HTTP Web 服務位址設定連接埠使用 HTTP 配接器。 此範例會使用 **ExplorerOM** 物件示範下列作業：  

-   使用**AddNewSendPort**方法**應用程式**来加入新的傳送埠，呼叫以 CBRApplication SendportUSOrders 類別。 連接埠會設定為使用 HTTP 配接器與假設性的 Web 位址的傳輸。  

-   將篩選新增至 SendportUSOrders CBRApplication 美國的訊息訂閱值為 100 的國家/地區的程式碼。  

-   將加入輸出對應 SendportUSOrders CBRApplication 對應轉換以美國為基礎的訊息。  

-   加入新的傳送埠，稱為 SendportCANOrders CBRApplication 及設定它使用 HTTP 配接器與假設性的 Web 位址的傳輸。  

-   篩選條件加入 SendportCANOrders 訂閱中訊息 CBRApplication 加拿大國家/地區代碼值為 200。  

-   將加入輸出對應 SendportCANOrders CBRApplication 對應轉換加拿大為基礎的訊息。  

## <a name="where-to-find-this-sample"></a>此範例的位置  
 這個範例位於下列 SDK 位置：  

 \<*範例路徑*\>\Admin\ExplorerOM\CBR  

 下表顯示此範例中的檔案，並描述其用途。  


|           檔案            |                                                 描述                                                  |
|------------------------------|--------------------------------------------------------------------------------------------------------------|
|    ContentBasedRouting.cs    | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] 此範例中示範的作業的原始程式檔。 |
| CBR.sln，CBR.csproj，CBR.suo |                                  此範例的方案和專案檔。                                  |

## <a name="building-and-running-this-sample"></a>建置和執行此範例  

#### <a name="to-build-this-sample"></a>建置此範例  

1. 請確定您已完成建置、 部署和設定 CBRSample 的步驟。 會提供這些步驟[CBRSample （BizTalk Server 範例）](../core/cbrsample-biztalk-server-sample.md)。  

2. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 CBR.sln。  

3. 按一下 [ **建置** ] 功能表上的 [ **建置方案**]。  

#### <a name="to-run-this-sample"></a>執行此範例  

1. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，然後瀏覽至**CBRApplication**節點。  

2. 依序展開**CBRApplication**節點，以確認**傳送連接埠**節點目前已列為 [cbrussendport] 和 [cbrcansendport] 只有兩個連接埠。  

3. 開啟命令視窗並巡覽至下列資料夾：  

    \<*範例路徑*\>\Admin\ExplorerOM\CBR\bin\Debug  

4. 執行檔案 CBR.exe。  

5. 按下 F5，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來重新整理檢視底下**傳送埠**節點。 現在，您應該會看到兩個新連接埠新增至 CBRApplication 此範例。 它們稱為 SendportUSOrders 和 SendportCANOrders。  

## <a name="windows-powershell-script-example"></a>Windows PowerShell 指令碼範例  
 下列 Windows PowerShell 指令碼可以用來示範 **ExplorerOM** 類別的相同功能。 不過，因為**新增**方法**SendPort.OutboundTranforms**集合中的內部標記**ExplorerOM**不能直接從呼叫的組件Windows PowerShell。 此 Windows PowerShell 指令碼示範如何使用 BizTalk WMI 提供者，從 Windows PowerShell 輸出的轉換對應加入新的連接埠。  

```  
Function WMI_AddOutboundTransformToPort($transform,$strPortName)  
{  
    Write-Host "WMI Processing Transform...`r`nPortName `:"$strPortName  
    Write-Host "Transform `:"$transform.AssemblyQualifiedName  

    $WMIsendport = get-wmiobject MSBTS_SendPort -filter "Name=`"$strPortName`"" -namespace root\microsoftbiztalkserver  
    $WMIsendport.OutboundTransforms = $transform.AssemblyQualifiedName  
    [Void] $WMIsendport.Put()  
    [Void] $WMIsendport.Start()  
}  

#===================#  
#=== Main Script ===#  
#===================#  

#=== Make sure the ExplorerOM assembly is loaded ===#  

[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  

#=== Connect to the BizTalk Management database ===#  

$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  

$CBRApp = $Catalog.Applications["CBRApplication"]  

if ($CBRApp -eq $null)  
{  
    Write-Host "`r`nFailed to find `"CBRApplication`" deployed on this BizTalk server."  
    Write-Host "You must deploy the SDK\Samples\Messaging\CBRSample in order to test this script.`r`n"  
}  
else  
{  
    #=== Register a trap handler for any exceptions ===#  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  

    #===================================#  
    #=== Create the U.S. Orders Port ===#  
    #===================================#  

    $USPort = $CBRApp.AddNewSendPort($false,$false)  
    $USPort.Name = "SendportUSOrders"  
    $USPort.PrimaryTransport.TransportType = $Catalog.ProtocolTypes["HTTP"]  
    $USPort.PrimaryTransport.Address = "http://process_orders_US.asp"  
    $USPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  

    #=== add the filter to subscribe to messages with U.S country code 100 ===#  

    $USPort.Filter = "<Filter><Group>" +  
                     "<Statement Property='BTS.ReceivePortName' Operator='0' Value='ReceivePortPO'/>" +   
                     "<Statement Property='CBRSample.CountryCode' Operator='0' Value='100'/>" +  
                     "</Group></Filter>"  

    Write-Host("`r`nAdding " + $UsPort.Name + " to catalog ...")  
    $Catalog.SaveChanges()  

    #=========================================================================================#  
    #=== SendPortTranformCollection::Add is marked internal in ExplorerOM for some reason. ===#  
    #=== Use WMI to set this as a workaround through PowerShell.                           ===#  
    #=========================================================================================#  

    WMI_AddOutboundTransformToPort $Catalog.Transforms["CBRSample.CBRInput2USMap"] $USport.Name  

    #=====================================#  
    #=== Create the Canada Orders Port ===#  
    #=====================================#  

    $CanadaPort = $CBRApp.AddNewSendPort($false,$false)  
    $CanadaPort.Name = "SendportCANOrders"  
    $CanadaPort.PrimaryTransport.TransportType = $Catalog.ProtocolTypes["HTTP"]  
    $CanadaPort.PrimaryTransport.Address = "http://process_orders_CAN.asp"  
    $CanadaPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  

    #=== add the filter to subscribe to messages with U.S country code 100 ===#  

    $CanadaPort.Filter = "<Filter><Group>" +  
                     "<Statement Property='BTS.ReceivePortName' Operator='0' Value='ReceivePortPO'/>" +   
                     "<Statement Property='CBRSample.CountryCode' Operator='0' Value='200'/>" +  
                     "</Group></Filter>"  

    Write-Host("`r`nAdding " + $UsPort.Name + " to catalog ...")  
    $Catalog.SaveChanges()  

    #=========================================================================================#  
    #=== SendPortTranformCollection::Add is marked internal in ExplorerOM for some reason. ===#  
    #=== Use WMI to set this as a workaround through PowerShell.                           ===#  
    #=========================================================================================#  

    WMI_AddOutboundTransformToPort $Catalog.Transforms["CBRSample.CBRInput2CANMap"] $CanadaPort.Name  

    Write-Host  
}  
```  

 以下是執行 Windows PowerShell 指令碼來建立兩個新的連接埠的範例輸出。 新的連接埠也可以驗證在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]如先前所述的管理主控台。  

```  
PS C:\> .\CBR.ps1  

Adding SendportUSOrders to catalog ...  
WMI Processing Transform...  
PortName : SendportUSOrders  
Transform : CBRSample.CBRInput2USMap,CBRSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ba2e1651515c6db7  

Adding SendportUSOrders to catalog ...  
WMI Processing Transform...  
PortName : SendportCANOrders  
Transform : CBRSample.CBRInput2CANMap,CBRSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ba2e1651515c6db7  

```  

## <a name="see-also"></a>另請參閱  
 [Admin-explorerom （BizTalk Server Samples 資料夾）](../core/admin-explorerom-biztalk-server-samples-folder.md)   
 [CBRSample (BizTalk Server 範例)](../core/cbrsample-biztalk-server-sample.md)