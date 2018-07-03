---
title: 動態解析範例的單向傳訊案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38237840-e957-4298-84c9-700ec72f2bc5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 359b91a1a5da9ce435d3d9aa5884d6928d0e0a9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987535"
---
# <a name="one-way-messaging-scenarios-for-the-dynamic-resolution-sample"></a>動態解析範例的單向傳訊案例
本主題說明如何執行的單向傳訊案例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]動態解析範例。  

 **若要執行動態解析範例的單向傳訊的案例**  

1. 您第一次執行此範例之前，請確定接收位置 URL 指向適當的目錄。 指定來源子資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\In DynamicResolution_FILE 接收位置。 此外，請確定名為 DynamicResolutionOneWay 動態傳送埠存在。  

   > [!NOTE]
   >  動態解析範例會使用動態解析機制，將訊息傳送至輸出資料夾、 FTP 站台或 MQSeries 佇列。 這就是為什麼此範例中未定義的靜態傳送埠。 動態解析元件會擷取解析中的輸出 URL 和配接器提供者架構 ESBReceiveXml 管線中，設定 DynamicResolution_FILE 內呼叫時，接收位置。  

2. 如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。  

3. 決定您想要執行的範例。 全都是單向傳訊 （除了使用 XPATH 解析程式） 的範例使用 NAOrderDoc.xml 位於 \Source\Samples\DynamicResolution\Test\Data 的資料夾中的檔案輸入至名為 DynamicResolution_FILE 的接收位置。 有七個單向傳訊範例，每一個由唯一的繫結檔案。 下表列出這些範例中，使用其相關聯的繫結檔案和描述。  

   |檔案輸入輸出使用靜態的解析程式的檔案|  
   |-------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |在接收埠以靜態方式設定對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  

   |檔案輸入輸出使用 UDDI 解析程式的檔案|  
   |-----------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |在接收埠以靜態方式設定對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  

   |檔案輸入輸出使用 UDDI 解析程式，透過 「 UDDI 服務金鑰的檔案|  
   |----------------------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_SERVICEKEY_ Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |在接收埠以靜態方式設定對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  

   > [!NOTE]
   >  如上述範例中，您必須存在於目標 UDDI 伺服器上的其中一個變更繫結檔案中的服務金鑰。  

   |檔案輸入與輸出使用靜態的解析程式的 FTP|  
   |------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |在接收埠以靜態方式設定對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  

   |檔案輸入與輸出使用 ENDPOINTCONFIG 參數與靜態的解析程式的 FTP|  
   |-----------------------------------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC__ ENDPOINTCONFIG_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |在接收埠以靜態方式設定對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  
   |會將配接器提供者設定的其他名稱/值組。|  

   |檔案輸入至 MQS 輸出使用靜態的解析程式|  
   |------------------------------------------------------------|  
   |您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_MQS_STATIC_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。|  
   |在接收埠以靜態方式設定對應。|  
   |ESB 發送器會在使用接收位置的端點解析。|  

   |                                                                             檔案輸入輸出使用 XPATH 解析程式的檔案                                                                             |
   |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                        您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_XPATH_STATIC_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。                        |
   |                                                                                 在接收埠以靜態方式設定對應。                                                                                  |
   |                                                                    ESB 發送器會在使用接收位置的端點解析。                                                                    |
   | 使用訊息內的資訊來判斷適當的端點。 您可以使用此範例中的測試檔案是 NAOrderDoc_XPATH_FILE.xml、 NAOrderDoc_XPATH_FTP.xml 和 NAOrderDoc_XPATH_MQS.xml。 |


4. 匯入繫結檔案，您想要執行到 GlobalBank.ESB 應用程式的範例訊息。  

5. 在 Windows 檔案總管中，開啟資料夾 \Source\Samples\DynamicResolution\Test\Data 並將適當的輸入的檔案複製到資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\In。 您使用的檔案取決於您決定要執行的範例：  

   -   XPATH 範例中，使用下列檔案： NAOrderDoc_XPATH_FILE.xml、 NAOrderDoc_XPATH_FTP.xml 或 NAOrderDoc_XPATH_MQS.xml。  

   -   如需其他範例，使用檔案 NAOrderDoc.xml。  

6. 查看已傳送訊息的適當位置。 位置取決於您所使用的繫結檔案。 以下是範例：  

   -   輸入 FTP 輸出的範例檔案會將訊息傳遞到名稱為 Out 的 FTP 虛擬目錄時建立安裝範例。  

   -   檔案輸入輸出檔的範例會將訊息傳遞至 \DynamicResolution\Test\Filedrop\Out 子資料夾。  

   -   檔案輸入 MQS 輸出的範例會將訊息傳遞至測試。放大時建立的佇列，您會安裝範例。  

   -   檔案輸入至 檔案輸出使用 XPATH 解析程式範例會將訊息傳遞到訊息中指定的位置。 範例文件包含目的位置和傳輸型別 （傳輸類型會附加至訊息的檔案名稱; 例如，NAOrderDoc_XPATH_FTP.xml 訊息中包含的 FTP 傳輸的型別規格）。  

   若要了解此範例會使用 ESB 發送器和 ESB 發送器解譯器管線元件，請參閱[動態解析範例運作方式](../esb-toolkit/how-the-dynamic-resolution-sample-works.md)。