---
title: PartyResolution （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, parties
- orchestrations, examples
- parties, examples
- parties, orchestrations
- examples, routing
- orchestrations, parties
- examples, orchestrations
- examples, messages
- routing, messages
- messages, routing
ms.assetid: 220e6bc5-6f04-4f37-b0d0-f11c2cc14422
caps.latest.revision: 33
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35334b61199d758a5eafe8623ea576a047799925
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984431"
---
# <a name="partyresolution-biztalk-server-sample"></a>PartyResolution （BizTalk Server 範例）
PartyResolution 範例示範如何搭配運用 BizTalk 協調流程和合作對象解析，以將訊息路由至兩個可能收件者中的一個。  

## <a name="what-this-sample-does"></a>此範例的用途  
 此範例執行多個協調流程，示範下列不同的角色：  

-   買方協調流程，用來初始化訂單 (PO) 訊息處理。  

-   供應商協調流程，示範輸入和輸出合作對象解析。  

-   ShipmentAgency1 和 ShipmentAgency2 協調流程，根據 PO 中的出貨目的地回應供應商協調流程。  

## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 合作對象解析是指判斷訊息傳送者 (即傳送訊息之一方) 為何的程序。 例如，您可能只想要讓已知的合作對象傳送訊息。 輸出合作對象解析就是您在決定要將訊息傳送給哪些合作對象時所依據的程序。  

 除了合作對象解析之外，此案例還示範如何實作和使用角色。 例如，為了處理產品的出貨，您會建立一個傳送埠，指示託運商運送您產品的文件會傳送到該傳送埠。 如果您有多個託運商可供選擇，可在協調流程中建立託運商角色，而不要建立只有託運商 URL 不同的多個傳送埠。 然後您可將與產品出貨相關的訊息傳送到該託運商角色。 您會建立合作對象，然後將傳送埠與每個合作對象和合作對象憑證產生關聯。 最後您會將每個合作對象登錄到託運商角色以啟用它。 接著您就可以在協調流程中動態指定您要將訊息傳送到哪個託運商。  

 此範例也示範如何使用相互關聯，將內送訊息對應到正確的協調流程執行個體。  

- 買方、供應商和託運商的商務程序流程如下：  

- 買方的商務程序流程：  

  1.  從內部部門以 .xml 檔案的形式接收 PO 訊息。  

  2.  將 PO 訊息傳送到供應商。  

- 供應商的商務程序流程：  

  1.  解析合作對象 (輸入合作對象解析)，根據簽章憑證更新來源合作對象。  

  2.  接收來自買方的啟動訊息 (PO)。  

  3.  將 PO 確認訊息傳送到買方。  

  4.  確認送達國家/地區。  

  5.  解析輸出合作對象，找出要使用的託運商。 如果該國家/地區為美國，託運商就是 ShipmentAgency2。 如果該國家/地區為加拿大，託運商就是 ShipmentAgency1。  

  6.  將出貨訂單要求訊息傳送到適當的託運商。  

  7.  從適當的託運商接收出貨訂單確認訊息。  

  8.  將出貨建議訊息傳送到適當的託運商。  

  9. 從適當的託運商接收出貨建議確認訊息。  

  10. 將最後的 PO 送達回條訊息傳送給買方。  

- 託運商的商務程序流程 (兩個託運商都相同)：  

  1.  接收來自供應商的出貨訂單要求訊息。  

  2.  產生並傳送出貨訂單要求訊息的確認訊息。  

  3.  接收來自供應商的出貨建議訊息。  

  4.  產生並傳送出貨建議訊息的確認訊息。  

  以下聲明說明此範例設計的方式：  

- BuyerProcess.odx 協調流程會接收訊息，然後使用自訂的管線 MimePartyResSendPipeline 來編碼訊息並將它傳送到供應商。 這可使用管線設計師建置和部署自訂傳送管線來完成。 傳送訊息給供應商之前, 的訊息進行數位簽署買方的私密金鑰，在 BizTalk 群組屬性中所指定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

- SupplierProcess.odx 協調流程使用自訂的管線 MimePartyResReceivePipeline (此管線包含 MIME/SMIME 解碼器元件)，使用買方的公開金鑰解析並驗證買方的身份，來解碼訊息及執行輸入合作對象解析。 此項工作由建置和部署自訂的接收管線完成。  

- 然後供應商協調流程會初始化 POCorrelationSets，此屬性定義為以升級的屬性 PONo 為基礎。 PONo 在稍後階段用來將輸入和輸出訊息對應到此協調流程執行個體，因為整個協調流程中有多個傳送和接收動作。  

- 供應商協調流程會實作角色連結，以處理輸入和輸出合作對象解析。 供應商協調流程使用兩種角色連結類型：  

  -   Buyer_Supplier 角色連結類型  

  -   Supplier_Shipment 角色連結類型  

- 在 Buyer_Supplier**角色連結**圖形，供應商是扮演提供者角色，而且因為供應商從買方接收第一個訊息，取用者角色位於買方。 當供應商協調流程傳送確認到買方角色時，會有一個與買方關聯的傳送埠，而訊息則會透過此指定傳送埠傳送到買方。 若要尋找此傳送埠，以滑鼠右鍵按一下**BuyerAgency**中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，然後按一下**屬性**。 傳送埠會顯示下**傳送埠**。  

- 然後協調流程會使用下列運算式傳回合作對象資訊，並透過呼叫名為 CheckPartyName 的外部組件將 XML 檔案寫入資料夾中。  

  ```  
  Buyer_Supplier(Microsoft.XLANGs.BaseTypes.SourceParty)  
  ```  

- 在 Supplier_Shipment**角色連結**圖形，出貨角色包含具有兩項作業用來從供應商的訊息傳送至適當的託運商視目的合作對象的傳送埠。 供應商角色包含一個接收埠，以及用來接收來自託運商之回應的兩項作業。 在傳送和接收這些訊息時會使用相互關聯，它是根據 PONo 而建立。  

  > [!NOTE]
  >  當您繫結供應商協調流程時，會發現只需要繫結一個傳送埠和兩個接收埠。 這是因為目的合作對象的傳送埠已經和合作對象繫結。 此外，其中一個協調流程中的接收埠包含兩個接收作業，因此，即使您會看到三**接收**圖形，只有兩個都必須繫結。  

- 供應商協調流程使用下列程式碼的第一行，藉由呼叫名為 QueryShipmentCatalogComponent 的外部組件來取得託運商。 然後它會使用第二行來設定出貨角色的目的合作對象。  

  ```  
  strShipmentName= objQueryShipmentCatalog.GetShipmentDetails(POMessage.MessagePart_1.POHeader.Address.Country);  
  Supplier_Shipment(Microsoft.XLANGs.BaseTypes.DestinationParty) = new Microsoft.XLANGs.BaseTypes.Party(strShipmentName,"OrganizationName");  
  ```  

- Shipper1Process.odx 和 Shipper2Process.odx 的建置，是用於接收 SupplierProcess.odx 的送貨單和出貨建議，並用於傳送回應給 SupplierProcess.odx。 在這兩個託運商協調流程中都有使用相互關聯，而相互關聯類型則是依據升級屬性 PONo 而定。  

## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \Orchestrations\PartyResolution\  

 下表顯示此範例中的檔案，並描述其用途。  


|                                                                                                                                 檔案                                                                                                                                 |                                                                                                                                                              描述                                                                                                                                                              |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                      BuyerBinding.xml, ShippingAgency1Binding.xml, ShippingAgency2Binding.xml, SupplierBinding.xml                                                                                      |                                                                                                                                            用於自動化設定，例如連接埠繫結。                                                                                                                                             |
|                                                                                                                               Cleanup.bat                                                                                                                               |                                                                   用來解除部署組件，以及將它從全域組件快取中移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。                                                                    |
|                                                                                                                           PartyResolution.sln                                                                                                                           |                                                                                                                              包含不同子資料夾中所有專案的方案檔。                                                                                                                               |
|                                                                                                                            PurchaseOrder.xml                                                                                                                            |                                                                                                                                                           範例 PO 輸入檔。                                                                                                                                                            |
|                                                                                                                                Setup.bat                                                                                                                                |                                                                                                                                         用來建置和初始化此範例的一部分。                                                                                                                                         |
|                                                                                                    在 \Buyer 資料夾中：<br /><br /> Buyer.btproj, BuyerProcess.odx                                                                                                     |                                                                                                                             用來實作此範例中買方的 BizTalk 專案和協調流程。                                                                                                                             |
|                                                                                                             在 \Catalog 資料夾中：<br /><br /> Catalog.xml                                                                                                             |                                                                                                                         用來根據 PO 中指定的出貨目的地決定託運商。                                                                                                                          |
|                                                                                      在 \CheckPartyName 資料夾中：<br /><br /> AssemblyInfo.cs, CheckPartyName.csproj, Class1.cs                                                                                       |                                                                                                  CheckPartyName 應用程式的 Microsoft Visual C# 專案和來源檔案，用來存取來源合作對象的屬性。                                                                                                   |
|                                                                在 \FilePolling 資料夾中：<br /><br /> App.ico, AssemblyInfo.cs, FilePolling.cs, FilePolling.csproj, FilePolling.resx, FilePolling.sln,                                                                 |                                                                 FilePolling 應用程式的 Visual C# 方案、專案、來源和相關檔案。<br /><br /> 請使用此應用程式以瞭解有關此自動化案例的處理狀態。                                                                  |
|                                                                            在 \Pipeline\projectschema 資料夾中：<br /><br /> MimePartyResReceivePipeline.btp, MimePartyResSendPipeline.btp                                                                             |                                                                                             此範例中不同角色所使用的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線檔案。                                                                                             |
|                                                                在 \QueryShipmentCatalogComponent 資料夾中：<br /><br /> AssemblyInfo.cs, QueryShipmentCatalog.cs, QueryShipmentCatalogComponent.csproj                                                                 | QueryShipmentCatalog 元件的 Visual C# 專案和來源檔案，用來存取 Catalog.xml 檔案中定義的出貨目錄。<br /><br /> QueryShipmentCatalog 元件決定供應商將使用的託運商。 它使用 Catalog.xml 中的資料，根據地理位置決定最佳的託運商。 |
| 在 \Schemas 資料夾中：<br /><br /> PODeliveryReceipt.xsd, POPropertySchema.xsd, PurchaseOrder.xsd, PurchaseOrderAcknowledgement.xsd, Schemas.btproj, ShipmentAdvice.xsd, ShipmentAdviceAcknowledgement.xsd, ShipmentOrderAcknowledgement.xsd, ShipmentOrderRequest.xsd |                                                                                                                                           此範例中不同角色所使用的結構描述。                                                                                                                                           |
|                                                                  在 \ShipmentAgency1 資料夾：<br /><br /> ShipmentAdviceAck.btm, ShipmentAgency1.btproj, ShipmentOrderAck.btm, Shipper1Process.odx                                                                   |                                                                                                                      用來實作此範例中 ShipmentAgency1 的 BizTalk 專案、協調流程和對應。                                                                                                                       |
|                                                                  在 \ShipmentAgency2 資料夾中：<br /><br /> ShipmentAdviceAck.btm, ShipmentAgency2.btproj, ShipmentOrderAck.btm, Shipper2Process.odx                                                                   |                                                                                                                      用來實作此範例中 ShipmentAgency2 的 BizTalk 專案、協調流程和對應。                                                                                                                       |
|                                     在 \Supplier 資料夾中：<br /><br /> PO_POAck.btm, PO_ShipmentOrderRequest.btm, ShipmentAdviceAck_PODeliveryReceipt.btm, ShipmentOrder_ShipmentAdvice.btm, Supplier.btproj, SupplierProcess.odx                                     |                                                                                                                        用來實作此範例中供應商的 BizTalk 專案、協調流程和對應。                                                                                                                        |

## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  

> [!NOTE]
>  在建置和初始化此範例之前，您必須確定預設的 BizTalk 內含式主控件設定為「信任的驗證」。 如需詳細資訊，請參閱 < [BizTalk Server 執行階段安全性建議](../core/biztalk-server-runtime-security-recommendations.md)。  

 MIME 管線元件不支援在 64 位元主控件執行個體。 與檔案配接器之傳送和接收處理常式關聯的主控件必須設定做為僅 32 位元主控件。 如需有關這個，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。 如果您已經有 32 位元的唯一主控件，在系統上，設定，想要使用它，請參閱[設定 File 配接器](../core/configure-the-file-adapter.md)設定 file 配接器相關聯的主機上的指示傳送和接收處理常式。  

 在本節中所述的憑證必須新增至設定將用於簽署訊息的預設 BizTalk 內含式主控件執行個體的登入帳戶的個人存放區。  

 根據預設 setup.bat 下面所述的檔案會預設成安裝合作對象解析範例[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。 您可以修改 setup.bat 檔案，以便部署至新的範例[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]陳述式加上應用程式開啟 setup.bat 檔案，並取代區段`@ECHO Deploy Assemblies...`取代下列項目：  

```  
@ECHO Deploy Assemblies...  

btstask AddApp -ApplicationName:PartyResolutionSample -Description:"Party Resolution Orchestration sample from the SDK"  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Schemas\bin\Release\Schemas.dll -Options:GacOnAdd  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Pipeline\projectschema\bin\Release\ProjectSchema.dll -Options:GacOnAdd   
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Buyer\bin\Release\Buyer.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%BuyerBindingFileName%  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:ShipmentAgency1\bin\Release\ShipmentAgency1.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%ShipmentAgency1BindingFileName%  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:ShipmentAgency2\bin\Release\ShipmentAgency2.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%ShipmentAgency2BindingFileName%  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Supplier\bin\Release\Supplier.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%SupplierBindingFileName%  
```  

#### <a name="to-build-and-initialize-the-partyresolution-sample"></a>建置和初始化 PartyResolution 範例  

1. 在命令視窗中，瀏覽至下列資料夾：  

    \<*範例路徑*> \Orchestrations\PartyResolution  

2. 執行檔案 Setup.bat，這會執行下列動作：  

   - 編譯此範例的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，並部署產生的組件。  

   - 建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送和接收埠。  

      在安裝過程中，您可能會收到下列或類似的警告。 您可以安全地忽略這些警告。  

     ```  
     "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\PartyResolution.sln" (Buildtarget) (1) ->  
     "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj" (default target) (5) ->  
     "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj" (default target) (5:2) ->  
     (CompileODX target) ->  
       C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\SupplierProcess.odx(831,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it [C:\ProgramFiles\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj]  
       C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\SupplierProcess.odx(841,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it [C:\ProgramFiles\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj]  

     ```  

3. 開始**Visual Studio 命令提示字元**。  

4. 輸入下列命令將組件安裝到全域組件快取中：  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Schemas\bin\Release\schemas.dll  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Pipeline\projectschema\bin\Release\ProjectSchema.dll  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Buyer\bin\Release\Buyer.dll  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\ShipmentAgency1\bin\Release\ShipmentAgency1.dll  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\ShipmentAgency2\bin\Release\ShipmentAgency2.dll  

   - gacutil-i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Supplier\bin\Release\Supplier.dll  

5. 從「憑證授權單位」(CA) 取得安全的電子郵件憑證。 CA 可以是協力廠商授權單位或您組織中的授權單位。 在您取得憑證後，請匯出公開金鑰和私密金鑰。  

6. 若要私用的金鑰匯入至主控件執行個體的登入帳戶和公開金鑰至本機電腦其他人存放區的個人存放區中，執行下列作業：  

   1. 在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開 BizTalk 群組]，然後再展開**平台設定**。  

   2. 按一下 **主控件執行個體**並尋找顯示預設的內含式主控件執行個體的登入帳戶。 在預設安裝中預設內含式主控件應命名為 [biztalkserverapplication]。  

   3. 按一下 **[開始]**，然後按一下 **[執行]**。 在 **執行**方塊中，輸入**mmc.exe**，然後按一下**確定**。 輸入主控件執行個體登入帳戶，若要開啟的 「 Microsoft Management Console (MMC) 」，該帳戶下的正確密碼。  

   4. 在 [檔案] 功能表上，按一下 [新增/移除嵌入式管理單元]。  

   5. 在 **新增或移除嵌入式管理單元**對話方塊中，選取**憑證**，然後按一下**新增**。  

   6. 在 **憑證嵌入式管理單元**對話方塊中，選取**我的使用者帳戶**，然後按一下 **完成**。  

   7. 在 **新增或移除嵌入式管理單元**對話方塊中，選取**憑證**，然後按一下**新增**。  

   8. 在 **憑證嵌入式管理單元**對話方塊中，選取**電腦帳戶**，然後按一下 **下一步**。  

   9. 在 [**選取電腦**] 對話方塊中，選取**本機電腦**，然後按一下**完成**。  

   10. 在 [**新增或移除嵌入式管理單元**] 對話方塊中，按一下**確定**。  

   11. 依序展開**憑證-目前使用者**節點，然後展開**個人**。 以滑鼠右鍵按一下**憑證**，按一下**所有工作**，然後按一下**匯入**。  

   12. 匯入的私密金鑰，並提供精靈中的密碼。  

   13. 依序展開**Certificates (Local Computer)** 節點，然後展開**其他人**。 以滑鼠右鍵按一下**憑證**，按一下**所有工作**，然後按一下**匯入**。  

   14. 匯入公開金鑰。  

7. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**BizTalk 群組**節點，然後按一下**屬性**。 在  **BizTalk 群組-群組屬性**對話方塊中，選取**憑證**。  

8. 在 [**憑證**] 對話方塊中，按一下**瀏覽**，然後選取您剛才匯入的私密金鑰。 此處指定的憑證用於簽章訊息。 按一下 [確定] 。  

9. 若要更新 BuyerAgency 合作對象，在此範例中執行下列作業：  

   1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，選取**合作對象**。  

   2. 以滑鼠右鍵按一下**BuyerAgency** ，然後按一下**屬性**。 在  **BuyerAgency-合作對象屬性**對話方塊中，選取**一般**。  

   3. 底下**別名**一節的對話方塊中，加入新的別名名稱與限定詞設定為**WindowsUser**。 將值設定為 使用者名稱格式為\<網域 \ 使用者名稱 > (e.g.SOMEDOMAIN\someuser)。  

   4. 選取 **憑證**，然後按一下**瀏覽**並選取您剛才匯入的公用金鑰。 此處指定的憑證用於驗證輸入訊息的傳送者識別。 按一下 [確定] 。  

10. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**平台設定**，然後選取**主機**。  

11. 以滑鼠右鍵按一下**BizTalkServerApplication** ，然後按一下**屬性**。 在  **BizTalkServerApplication-主控件屬性**對話方塊中，選取**憑證**。  

12. 按一下 **瀏覽**，然後選取您剛才匯入的私密金鑰。 此處指定的憑證用於解密輸入訊息。 按一下 [確定] 。  

13. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**平台設定**，然後選取**主控件執行個體**。  

14. 以滑鼠右鍵按一下**BizTalkServerApplication** ，然後按一下**重新啟動**。  

## <a name="running-this-sample"></a>執行此範例  

#### <a name="to-run-the-partyresolution-sample"></a>執行 PartyResolution 範例  

1.  執行下列資料夾中的 FilePolling.exe：  

     *\<範例路徑 >* \Orchestrations\PartyResolution\FilePolling\bin\Debug  

2.  按一下 **啟動輪詢**。  

3.  將提供的 PO 執行個體檔案 PurchaseOrder.xml 貼入下列資料夾中：  

     *\<範例路徑 >* \Orchestrations\PartyResolution\FileDrop\PurchaseOrder  

4.  觀察一系列可讓您了解此範例進度的相關訊息 (以訊息方塊的形式提供)：  

    1.  供應商何時接收來自買方的 PO。  

    2.  何時從託運商 1 或 2 收到出貨訂單要求。  

    3.  託運商 1 或 2 何時收到出貨建議。  

    4.  供應商何時將 PO 送達回條傳送到買方。  

5.  按一下 **結束**關閉檔案輪詢程式。  

> [!NOTE]
>  您可以將 PurchaseOrder.xml 中的「國家」標記編輯成「美國」，然後重複步驟 2 和步驟 3。 觀察出貨訂單現在是否傳送到託運商 2。  

## <a name="uninstalling-this-sample"></a>解除安裝這個範例  

#### <a name="to-uninstall-the-partyresolution-sample"></a>解除安裝 PartyResolution 範例  

1. 在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 來\<*範例路徑*> \Orchestrations\ PartyResolution\\。  

2. 執行 Cleanup.bat。  

## <a name="see-also"></a>另請參閱  
 [合作對象解析管線元件](../core/party-resolution-pipeline-component.md)   
 [如何設定 MIME SMIME 編碼器管線元件](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)   
 [如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)   
 [協調流程 (BizTalk Server Samples 資料夾)](../core/orchestrations-biztalk-server-samples-folder.md)