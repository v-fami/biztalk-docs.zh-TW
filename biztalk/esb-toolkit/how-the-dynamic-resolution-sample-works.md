---
title: 動態解析範例運作方式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7789316d-f2c4-4018-a8e8-dd9359f1664f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bab7a46a02dc080fa27b9df2b30614bc8a45c6e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976431"
---
# <a name="how-the-dynamic-resolution-sample-works"></a>動態解析範例運作方式
動態解析範例會使用 ESB 發送器解譯器管線元件的上一節中所述的所有傳訊範例。  

 單向傳訊案例，此範例會解析使用 STATIC、 BRE 或 XPATH 解析程式的端點，並且訊息代理程式的通訊協定檔案從檔案、 FTP 或 MQSeries。  

 雙向傳訊案例中，範例解析靜態、 BRE、 UDDI、 或 XPATH 解析程式所使用的端點，並從 SOAP 通訊協定，SOAP 或 Wcf-basichttp 訊息代理程式。 此外，這些範例解析，並執行 Microsoft BizTalk 對應使用 BRE 解析程式，以決定其解析結果使用包含在訊息內容屬性和訊息內文中的事實。  

 解析程序的結果會是雙向的所有範例都提交 ESB 其訊息。CanadianServices Web 服務位於http://localhost/ESB.CanadianServices/SubmitPOService.asmx。 此外，根據解析結果，此範例會執行其中一個**submitOrder**或**submitPurchase**動作。 此外，ESB 發送器解譯器管線元件會動態地執行 BizTalk 對應，根據指定 或 已解決 動作。  

 [圖 1] 顯示設定的管線，以 DynamicResolutionReqResp_SOAP 接收位置。  

 ![動態解析管線](../esb-toolkit/media/ch6-dynamicresolutionpipelines.gif "第 6 章第 DynamicResolutionPipelines")  

 **圖 1**  

 **設定的管線的 DynamicResolutionReqResp_SOAP 接收動態解析範例應用程式的位置**  

 [圖 2] 顯示 ESBReceiveXML 元件，它使用 ESB 發送器解譯器的每個執行個體屬性。  

 ![動態解析接收 XML](../esb-toolkit/media/ch6-dynamicresolutionreceivexml.gif "第 6 章第 DynamicResolutionReceiveXML")  

 **圖 2**  

 **動態解析範例應用程式的 ESBReceiveXML 管線中的元件，每個執行個體屬性**  

 圖 2 顯示下列屬性：  

- **啟用**。 此屬性會決定是否為作用中的管線。 如果此值設為**False**，訊息傳遞而不進行處理。  

- **端點**。 這個屬性是用來決定要載入的解析程式的連接字串，它會指定端點組態。  

- **MapName**。 這個屬性是用來決定要載入的解析程式和執行的 BizTalk 對應的連接字串。 它可以是完整的名稱，而不是解析程式的連接字串的對應。  

- **驗證**。 當設定為 **，則為 True** （預設設定），ESB 發送器解譯器元件會指示 ESB 轉換服務來驗證針對來源結構描述中的對應會定義來源訊息會解析並執行。  

  [圖 3] 顯示使用 ESB 發送器 ESBSendPassthrough 元件的每個執行個體屬性。  

  ![動態解析傳送通過](../esb-toolkit/media/ch6-dynamicresolutionsendpassthrough.gif "第 6 章第 DynamicResolutionSendPassthrough")  

  **圖 3**  

  **動態解析範例應用程式的 ESBSendPassthrough 管線中的元件，每個執行個體屬性**  

  圖 3 顯示下列屬性：  

- **啟用**。 此屬性會決定是否為作用中的管線。 如果此值設為**False**，訊息傳遞而不進行處理。  

- **端點**。 這個屬性是用來判斷哪些負載和端點組態的解析程式的連接字串。  

- **MapName**。 這個屬性是用來決定要載入的解析程式和執行的 BizTalk 對應的連接字串。 對應的完整格式的名稱可用來解析程式的連接字串取代。  

- **驗證**。 當設定為 **，則為 True** （預設設定），ESB 發送器解譯器元件會指示 ESB 轉換服務來驗證針對來源結構描述中的對應會定義來源訊息會解析並執行。
