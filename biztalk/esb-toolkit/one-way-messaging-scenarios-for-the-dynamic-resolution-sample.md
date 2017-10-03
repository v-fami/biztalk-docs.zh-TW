---
title: "動態解析範例單向傳訊案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38237840-e957-4298-84c9-700ec72f2bc5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8296c46561a8afa928033ae6002e3de621170234
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="one-way-messaging-scenarios-for-the-dynamic-resolution-sample"></a>動態解析範例單向傳訊的案例
本主題說明如何執行單向傳訊案例的[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]動態解析 」 範例。  
  
 **若要執行單向傳訊案例動態解析範例**  
  
1.  您第一次執行此範例之前，請確定接收位置 URL 指向適當的目錄。 指定來源子資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\In DynamicResolution_FILE 接收位置。 此外，請確定存在名為 DynamicResolutionOneWay 動態傳送埠。  
  
    > [!NOTE]
    >  動態解析 」 範例是使用動態解析機制將訊息傳送至輸出資料夾、 FTP 站台或 MQSeries 佇列。 這就是為什麼此範例中未定義靜態傳送埠。 動態解析元件擷取輸出 URL 從解析度，並呼叫 ESBReceiveXml 管線中，設定 DynamicResolution_FILE 內時，配接器提供者架構接收位置。  
  
2.  如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。  
  
3.  決定您想要執行的範例。 所有單向傳訊 （除了使用 XPATH 解析程式） 的範例使用檔案 NAOrderDoc.xml 位於 \Source\Samples\DynamicResolution\Test\Data 資料夾做為輸入命名 DynamicResolution_FILE 的接收位置。 有七個單向傳訊範例，分別由唯一的繫結檔案。 下表列出這些範例中，關聯的繫結檔案與說明。  
  
    |檔案輸入輸出使用靜態的解析程式的檔案|  
    |-------------------------------------------------------------|  
    |會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。|  
    |在接收埠以靜態方式設定對應。|  
    |ESB 發送器會在使用接收位置的端點解析。|  
  
    |檔案輸入輸出使用 UDDI 解析程式的檔案|  
    |-----------------------------------------------------------|  
    |會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。|  
    |在接收埠以靜態方式設定對應。|  
    |ESB 發送器會在使用接收位置的端點解析。|  
  
    |檔案輸入輸出使用 UDDI 解析程式，透過 「 UDDI 服務金鑰的檔案|  
    |----------------------------------------------------------------------------|  
    |會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_SERVICEKEY_ Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。|  
    |在接收埠以靜態方式設定對應。|  
    |ESB 發送器會在使用接收位置的端點解析。|  
  
    > [!NOTE]
    >  上述範例中，您必須變更成目標 UDDI 伺服器上現有的繫結檔案中的服務金鑰。  
  
    |檔案輸入輸出使用靜態的解析程式的 ftp|  
    |------------------------------------------------------------|  
    |會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。|  
    |在接收埠以靜態方式設定對應。|  
    |ESB 發送器會在使用接收位置的端點解析。|  
  
    |檔案輸入輸出使用靜態的解析程式和 ENDPOINTCONFIG 參數的 ftp|  
    |-----------------------------------------------------------------------------------------|  
    |會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC__ ENDPOINTCONFIG_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。|  
    |在接收埠以靜態方式設定對應。|  
    |ESB 發送器會在使用接收位置的端點解析。|  
    |傳送配接器提供者設定的額外名稱/值組。|  
  
    |MQS 輸出使用靜態的解析程式輸入檔案|  
    |------------------------------------------------------------|  
    |會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_MQS_STATIC_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。|  
    |在接收埠以靜態方式設定對應。|  
    |ESB 發送器會在使用接收位置的端點解析。|  
  
    |檔案輸入輸出使用 XPATH 解析程式的檔案|  
    |------------------------------------------------------------|  
    |會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_XPATH_STATIC_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。|  
    |在接收埠以靜態方式設定對應。|  
    |ESB 發送器會在使用接收位置的端點解析。|  
    |使用訊息內的資訊來判斷適當的端點。 您可以使用此範例中的測試檔案為 NAOrderDoc_XPATH_FILE.xml、 NAOrderDoc_XPATH_FTP.xml 和 NAOrderDoc_XPATH_MQS.xml。|  
  
4.  訊息的範例，您要執行到 GlobalBank.ESB 應用程式的繫結檔匯入。  
  
5.  在 Windows 檔案總管 中開啟資料夾 \Source\Samples\DynamicResolution\Test\Data 並將適當的輸入的檔複製到資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\In。 您使用的檔案取決於您決定要執行的範例：  
  
    -   XPATH 範例中，使用下列檔案： NAOrderDoc_XPATH_FILE.xml、 NAOrderDoc_XPATH_FTP.xml 或 NAOrderDoc_XPATH_MQS.xml。  
  
    -   如需其他範例，使用 NAOrderDoc.xml 的檔案。  
  
6.  查看已傳送訊息的適當位置。 該位置取決於您所使用的繫結檔案。 範例如下：  
  
    -   輸入 FTP 輸出的範例檔案會將訊息傳遞到名稱為 Out 的 FTP 虛擬目錄時建立安裝範例。  
  
    -   輸入與輸出檔案的範例檔案會將訊息傳遞至 \DynamicResolution\Test\Filedrop\Out 子資料夾。  
  
    -   檔案輸入輸出 MQS 範例會將訊息傳遞至測試。時建立佇列時，您會安裝範例。  
  
    -   輸入檔案輸出使用 XPATH 解析程式的範例檔案會將訊息傳遞至訊息中指定的位置。 範例文件包含目的地位置和傳輸類型 （傳輸類型會附加至訊息的檔案名稱; 例如，NAOrderDoc_XPATH_FTP.xml 訊息包含的 FTP 傳輸的型別規格）。  
  
 若要了解此範例會使用 「 ESB 發送器和 ESB 發送器解譯器管線元件，請參閱[動態解析範例的運作方式](../esb-toolkit/how-the-dynamic-resolution-sample-works.md)。