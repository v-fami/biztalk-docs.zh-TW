---
title: "安裝及執行動態解析範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4359987-b18c-44f5-a2cf-e30e17ac5e9f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f93396fc71c9e765104ac67835e006e57ca0ade
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="installing-and-running-the-dynamic-resolution-sample"></a>安裝及執行動態解析範例
動態解析 」 範例示範如何在一般使用案例的 ESB 發送器和 ESB 發送器解譯器管線元件。 它示範如何使用元件以動態方式解析端點位置、 設定路由的屬性，並解決，並執行 Microsoft BizTalk 對應，在訊息層級，而不需使用協調流程。 它也示範單向和雙向的訊息模式。  
  
> [!NOTE]
>  熟悉內，解決機制時的最佳結果[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，您應該執行[安裝及執行 「 解析程式服務 」 範例](../esb-toolkit/installing-and-running-the-resolver-service-sample.md)執行動態解析範例之前。  
  
 範例應用程式包含兩個接收位置和兩個動態傳送埠，此範例會示範多個使用動態解析元件的使用案例。 每個使用案例說明如何解析程式和配接器提供者，在解決和配接器提供者架構，用來結合，可以提供各式各樣的鬆散偶合的傳訊解決方案的基礎。  
  
## <a name="one-way-messaging-scenarios"></a>單向傳訊的案例  
 所有單向傳訊案例 （除了使用 XPATH 解析程式） 使用檔案 NAOrderDoc.xml，位於 [\Source\Samples\DynamicResolution\Test\Data] 資料夾中，做為輸入接收位置命名為 DynamicResolution_FILE。 有七個單向的訊息範例中，所有由唯一的繫結檔案，您必須匯入，然後再執行每個範例。  
  
## <a name="two-way-messaging-scenarios"></a>雙向傳訊的案例  
 所有的雙向傳訊實例中使用範例 ESB。位於要求訊息發佈到 BizTalk http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx NorthAmericanServices Web 服務。 您可以執行使用 Microsoft InfoPath 此 Web 服務或透過公用程式，例如可從 Storm [CodePlex](http://go.microsoft.com/fwlink/?LinkID=187762&clcid=0x409)。  
  
 每個範例以動態方式解析提交訊息至範例 ESB 的端點 URL。位於 http://localhost/ESB.CanadianServices/SubmitPOService.asmx CanadianServices Web 服務。 此範例會執行下列一**submitOrder**動作或**submitPurchase**動作，根據在解析程序的結果。 雙向傳訊案例的接收位置是 DynamicResolutionReqResp_SOAP。 有 10 個的雙向傳訊範例中，所有由唯一的繫結檔案，您必須匯入，然後再執行每個範例。  
  
## <a name="binding-files"></a>繫結檔案  
 此範例的繫結檔案位於名為 \Source\Samples\DynamicResolution\Samples\Release 的資料夾。  
  
 所有的繫結檔案名稱的開頭 GlobalBank.ESB.DynamicResolution_SubmitOrder_To，後面接著套用至個別範例的指示。 例如，繫結檔案，例如 「 檔案輸出到檔案輸入會使用靜態的解析程式 」 是 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml。  
  
 每次您匯入其中一個繫結至 GlobalBank.ESB BizTalk 應用程式，基礎檔案接收位置內的範例應用程式會重設。 在接收埠名稱相關聯的動態傳送埠篩選條件。 因此，若要執行測試，您才剛匯入其中一個繫結檔案，請卸除適當命名的訊息 （適用於單向傳訊的案例） 輸入的資料夾或呼叫使用 InfoPath、 Storm 公用程式，或任何其他 NorthAmerican Web 服務適合的用戶端。  
  
## <a name="sample-dependencies"></a>範例相依性  
 動態解析範例具有相依性核心 ESB 安裝一部分的組件數目。 這些組件如下所示：  
  
-   **Microsoft.Practices.ESB.PipelineComponents.dll**。 這包含 ESB 發送器管線元件。  
  
-   **Microsoft.Practices.ESB.Resolver.dll**。 這會實作由管線的解析程式管理員。  
  
-   **Microsoft.Practices.ESB.Resolver.BRE.dll**。 這會實作商務規則引擎的解析程式。  
  
-   **Microsoft.Practices.ESB.Resolver.STATIC.dll**。 這會實作靜態的解析程式。  
  
-   **Microsoft.Practices.ESB.Resolver.UDDI.dll**。 這會實作 UDDI 解析程式。  
  
-   **Microsoft.Practices.ESB.Resolver.UDDI3.dll**。 這會實作 UDDI3 解析程式。  
  
-   **Microsoft.Practices.ESB.Resolver.XPATH.dll**。 這會實作 XPATH 解析程式。  
  
-   **Microsoft.Practices.ESB.Resolver.Schemas.dll**。 這包含解析程式的結構描述。  
  
-   **Microsoft.Practices.ESB.Adapter.dll**。 這會實作配接器管理員。  
  
-   **Microsoft.Practices.ESB.Adapter.FTP.dll**。 這會實作 FTP 配接器提供者。  
  
-   **Microsoft.Practices.ESB.Adapter.FILE.dll**。 這會實作檔案配接器提供者。  
  
-   **Microsoft.Practices.ESB.Adapter.MQSeries.dll**。 這會實作 MQSeries 配接器提供者。  
  
-   **Microsoft.Practices.ESB.Adapter.WcfBasicHttp.dll**。 這會實作 Wcf-basichttp 配接器提供者。  
  
-   **Microsoft.Practices.ESB.Adapter.WcfWSHttp.dll**。 這會實作 Wcf-wshttp 配接器提供者。  
  
 動態解析範例也是相依於先前的解析程式和配接器的正確設定。 請確定安裝中所述，完成處理程序設定這些[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。  
  
 本節包含下列主題：  
  
-   [安裝動態解析範例](../esb-toolkit/installing-the-dynamic-resolution-sample.md)  
  
-   [執行動態解析範例](../esb-toolkit/running-the-dynamic-resolution-sample.md)
