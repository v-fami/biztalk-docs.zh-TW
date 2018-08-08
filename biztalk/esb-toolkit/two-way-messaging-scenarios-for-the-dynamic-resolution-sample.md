---
title: 動態解析範例的雙向傳訊案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e89792f1-c725-46c4-946c-23211e2f892a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6787edc22c06d6935518be9d223f5968a595d6cf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997015"
---
# <a name="two-way-messaging-scenarios-for-the-dynamic-resolution-sample"></a>動態解析範例的雙向傳訊案例
本主題說明如何執行的雙向傳訊案例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]動態解析範例。  

 **若要執行動態解析範例的雙向傳訊案例**  

1. 第一次執行此範例之前，請確定接收位置 URL 會指向適當的 Web 服務。 指定 Web 服務 URL /ESB。NorthAmericanServices/CustomerOrder.asmx DynamicResolutionReqResp_SOAP 的接收位置。 此外，請確認名為 DynamicResolutionSolicitResp 動態傳送埠存在。  

   > [!NOTE]
   >  動態解析範例會使用動態解析傳送和接收來自加拿大的 Web 服務的回應 (http://localhost/ESB.CanadianServices/SubmitPOService.asmx) 。 這就是為什麼此範例中未定義的靜態傳送埠。 動態解析元件會擷取輸出 URL 從解析度和配接器提供者架構，稱為 ESBReceiveXml 管線中，DynamicResolutionReqResp_SOAP 內設定的接收位置。 在某些雙向傳訊的範例中，ESBMapSend 管線解析，並執行 Microsoft BizTalk 對應。  

2. 如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。  

3. 決定您想要執行的範例。 所有的雙向傳訊案例使用 ESB。NorthAmericanServices Web 服務位於 http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx 發佈要求訊息至 BizTalk，它會使用名為 DynamicResolutionReqResp_SOAP 接收位置。 10 的雙向傳訊範例，每一個由唯一的繫結檔案。 下表列出這些範例中，使用其相關聯的繫結檔案和描述。  

   |SOAP 的輸出 (submitOrder 動作) 的 SOAP 輸入使用 BRE 解析程式|  
   |---------------------------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_BRE_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |ESB 發送器會在使用接收位置的端點解析。|  

   |SOAP 的輸出 (submitOrder 動作) 的 SOAP 輸入端點和轉換解析使用 BRE 解析程式|  
   |----------------------------------------------------------------------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_BRE_Routing_AND_ Transform_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |使用 ESB 發送器元件輸出的傳送埠上的管線和輸出的接收位置的管線，以動態解析，並執行對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  

   |SOAP 的輸出 (submitOrder 動作) 的 SOAP 輸入使用靜態的解析程式|  
   |------------------------------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_STATIC_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |在接收埠以靜態方式設定對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  

   |SOAP 的輸出 (submitOrder 動作) 的 SOAP 輸入使用 UDDI 解析程式對 Microsoft UDDI Server|  
   |--------------------------------------------------------------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_UDDI_MSFTREGISTRY_ Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |在接收埠以靜態方式設定對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  

   > [!NOTE]
   >  如上述範例中，您必須存在於目標 UDDI 伺服器上的其中一個變更繫結檔案中的服務金鑰。  

   |SOAP 的輸出 (submitOrder 動作) 的 SOAP 輸入使用 UDDI 解析程式對 SOA 軟體 UDDI 伺服器|  
   |-----------------------------------------------------------------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_UDDI_SOAREGISTRY_ Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |在接收埠以靜態方式設定對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  

   |                                                            SOAP 的輸出 (submitOrder 動作) 的 SOAP 輸入使用 XPATH 解析程式                                                            |
   |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                 您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_XPATH_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。                  |
   |                                                                           在接收埠以靜態方式設定對應。                                                                           |
   |                                                             ESB 發送器會在使用接收位置的端點解析。                                                              |
   | 訊息中包含的端點組態識別碼 =<http://localhost/ESB.CanadianServices/SubmitPOService.asmx>和 customerName =<http://globalbank.esb.dynamicresolution.com/canadianservices/>。 |

   |SOAP 的輸出 (submitPurchase 動作) 的 SOAP 輸入使用 BRE 解析程式端點和轉換解析|  
   |---------------------------------------------------------------------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitPurchaseOrder_BRE_Routing_ AND_Transform_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |使用 ESB 發送器元件輸出的傳送埠上的管線和輸出的接收位置的管線，以動態解析，並執行對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  
   |BRE 解析程式變更**動作**從**submitOrder**來**submitPurchase**。|  

   |                                              SOAP 的輸出 (submitPurchase 動作) 的 SOAP 輸入使用靜態的解析程式                                               |
   |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | 您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitPurchaseOrder_STATIC_ Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。 |
   |                                                               在接收埠以靜態方式設定對應。                                                                |
   |                                                  ESB 發送器會在使用接收位置的端點解析。                                                  |
   |                                           靜態解析程式變更**動作**從**submitOrder**來**submitPurchase**。                                           |


4. 匯入繫結檔案，您想要執行到 GlobalBank.ESB 應用程式的範例訊息。  

5. 呼叫 NorthAmerican Web 服務使用的 Microsoft InfoPath、.NET Web 服務 Studio 或任何其他適當的機制。 請確定您包含作業所需的所有參數。  

6. 尋找傳回的訊息回應。 如果您指定**submitOrder**動作，「 提交訂單 」 的文字將前面加上值的**識別碼**欄位中傳回的訊息。 如果您指定**submitPurchase**動作，「 提交採購 」 的文字將前面加上值的**識別碼**欄位中傳回的訊息。  

   若要了解此範例會使用 ESB 發送器和 ESB 發送器解譯器管線元件，請參閱[動態解析範例運作方式](../esb-toolkit/how-the-dynamic-resolution-sample-works.md)。