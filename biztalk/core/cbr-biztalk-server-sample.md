---
title: CBR （BizTalk Server 範例） |Microsoft 文件
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
ms.openlocfilehash: 30811b4f0dba463d518bdd9cd8f6d227e0e79aac
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967468"
---
# <a name="cbr-biztalk-server-sample"></a>CBR （BizTalk Server 範例）
CBR 範例將示範如何使用**ExplorerOM**系統管理物件來加入和設定新傳送埠的 BizTalk 訊息的內容為基礎的路由。  
  
## <a name="prerequisites"></a>必要條件  
  
-   這個範例需要，藉由執行中的 setup.bat 部署 CBRSample \<*範例路徑*\>\Messaging\CBRSample 目錄。  
  
-   您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。  
  
-   Windows PowerShell 指令碼範例需要 Windows PowerShell 執行原則來允許指令碼執行。 如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例示範如何使用中的系統管理物件**Microsoft.BizTalk.ExplorerOM** CBRApplication 範例中加入兩個新的連接埠的命名空間。 這些新的連接埠是 CBRApplication 的範例連接埠。 連接埠會使用 HTTP 配接器將訊息路由至假設 HTTP Web 服務位址設定。 此範例會使用 **ExplorerOM** 物件示範下列作業：  
  
-   使用**AddNewSendPort**方法**應用程式**来加入新的傳送埠，呼叫以 CBRApplication SendportUSOrders 類別。 連接埠設定為使用 HTTP 配接器與假設性的 Web 位址的傳輸。  
  
-   將篩選加入至 SendportUSOrders 訂閱 CBRApplication 與在美國太平洋時區中的訊息國家/地區碼值為 100。  
  
-   加入輸出對應來 SendportUSOrders CBRApplication 對應轉換美國為基礎的訊息。  
  
-   加入新的傳送埠呼叫 SendportCANOrders CBRApplication 及設定它使用 HTTP 配接器與假設性的 Web 位址的傳輸。  
  
-   將篩選加入至 SendportCANOrders 訂閱中 CBRApplication 加拿大的國碼/地區碼值為 200 的訊息。  
  
-   加入輸出對應來 SendportCANOrders CBRApplication 對應轉換加拿大為基礎的訊息。  
  
## <a name="where-to-find-this-sample"></a>此範例的位置  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*\>\Admin\ExplorerOM\CBR  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|ContentBasedRouting.cs|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]這個範例中示範的作業的來源檔案。|  
|CBR.sln，CBR.csproj，CBR.suo|此範例的方案和專案檔。|  
  
## <a name="building-and-running-this-sample"></a>建置和執行此範例  
  
#### <a name="to-build-this-sample"></a>建置此範例  
  
1.  請確定您已完成建置、 部署和設定 CBRSample 的步驟。 這些步驟中提供[CBRSample （BizTalk Server 範例）](../core/cbrsample-biztalk-server-sample.md)。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 CBR.sln。  
  
3.  按一下 [ **建置** ] 功能表上的 [ **建置方案**]。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台並瀏覽至**CBRApplication**節點。  
  
2.  展開**CBRApplication**節點可讓您確認**傳送埠**節點目前已列為 [cbrussendport] 和 [cbrcansendport] 只有兩個連接埠。  
  
3.  開啟命令視窗並巡覽至下列資料夾：  
  
     \<*範例路徑*\>\Admin\ExplorerOM\CBR\bin\Debug  
  
4.  執行檔案 CBR.exe。  
  
5.  按 f5 鍵在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來重新整理 下的檢視**傳送埠**節點。 您現在應該會看到兩個新連接埠新增至 CBRApplication 此範例。 它們稱為 SendportUSOrders 和 SendportCANOrders。  
  
## <a name="windows-powershell-script-example"></a>Windows PowerShell 指令碼範例  
 下列 Windows PowerShell 指令碼可以用來示範 **ExplorerOM** 類別的相同功能。 不過，因為**新增**方法**SendPort.OutboundTranforms**集合標記中的內部**ExplorerOM**不能直接從呼叫的組件Windows PowerShell。 此 Windows PowerShell 指令碼示範如何使用 BizTalk WMI 提供者，從 Windows PowerShell 輸出的轉換地圖加入至新的連接埠。  
  
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
  
 以下是執行 Windows PowerShell 指令碼來建立兩個新的連接埠的輸出範例。 新的連接埠也可以驗證在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，如上面所述。  
  
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
  
## <a name="see-also"></a>請參閱  
 [系統管理員 ExplorerOM （BizTalk Server 範例資料夾）](../core/admin-explorerom-biztalk-server-samples-folder.md)   
 [CBRSample (BizTalk Server 範例)](../core/cbrsample-biztalk-server-sample.md)