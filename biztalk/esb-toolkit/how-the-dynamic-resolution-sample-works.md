---
title: 動態解析範例的運作方式 |Microsoft 文件
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
ms.openlocfilehash: fe7d7b473482c432c8e3ae9ca48cab414a9e9573
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22294886"
---
# <a name="how-the-dynamic-resolution-sample-works"></a>動態解析範例的運作方式
動態解析範例會使用上一節中所述的所有傳訊範例 ESB 發送器解譯器管線元件。  
  
 單向傳訊的案例，此範例解析 STATIC、 BRE 或 XPATH 解析程式所使用的端點，並可仲介的通訊協定檔案從檔案、 FTP 或 MQSeries。  
  
 雙向傳訊的案例，範例解析 STATIC、 BRE、 UDDI 或 XPATH 解析程式所使用的端點，並從 SOAP 通訊協定，SOAP 或 Wcf-basichttp 會居間處理。 此外，在範例解析並執行 Microsoft BizTalk 對應使用 BRE 解析程式，以判斷解析結果使用包含在訊息內容屬性和訊息內文中的事實。  
  
 在解析程序的結果是雙向的所有範例都提交 ESB 其訊息。位於 http://localhost/ESB.CanadianServices/SubmitPOService.asmx CanadianServices Web 服務。 此外，根據解析結果，此範例會執行任何**submitOrder**或**submitPurchase**動作。 此外，ESB 發送器解譯器管線元件以動態方式執行 BizTalk 對應，根據指定的或已解決的動作。  
  
 圖 1 顯示的 DynamicResolutionReqResp_SOAP 設定的管線的接收位置。  
  
 ![動態解析管線](../esb-toolkit/media/ch6-dynamicresolutionpipelines.gif "第 6 章第 DynamicResolutionPipelines")  
  
 **圖 1**  
  
 **設定的管線的 DynamicResolutionReqResp_SOAP 接收動態解析範例應用程式的位置**  
  
 圖 2 顯示使用 ESB 發送器解譯器 ESBReceiveXML 元件的每個執行個體屬性。  
  
 ![動態解析接收 XML](../esb-toolkit/media/ch6-dynamicresolutionreceivexml.gif "第 6 章第 DynamicResolutionReceiveXML")  
  
 **圖 2**  
  
 **動態解析的 ESBReceiveXML 管線中元件的每個執行個體屬性範例應用程式**  
  
 圖 2 顯示下列屬性：  
  
-   **啟用**。 此屬性會決定是否為作用中的管線。 如果這個值設定為**False**，訊息傳遞而不進行處理。  
  
-   **端點**。 這個屬性是用來決定要載入的解析程式的連接字串，它會指定端點組態。  
  
-   **MapName**。 這個屬性是用來判斷要載入的解析程式，以及要執行的 BizTalk 對應的連接字串。 它可以是完整的名稱的對應，而不是解析程式的連接字串。  
  
-   **驗證**。 當設定為**True** （預設值），ESB 發送器解譯器元件會指示 ESB 轉換服務來驗證針對來源結構描述中的對應，會定義來源訊息會解析並執行。  
  
 圖 3 顯示使用 ESB 發送器 ESBSendPassthrough 元件的每個執行個體屬性。  
  
 ![動態解析傳送通過](../esb-toolkit/media/ch6-dynamicresolutionsendpassthrough.gif "第 6 章第 DynamicResolutionSendPassthrough")  
  
 **圖 3**  
  
 **動態解析的 ESBSendPassthrough 管線中元件的每個執行個體屬性範例應用程式**  
  
 圖 3 顯示下列屬性：  
  
-   **啟用**。 此屬性會決定是否為作用中的管線。 如果這個值設定為**False**，訊息傳遞而不進行處理。  
  
-   **端點**。 這個屬性是用來決定要載入和端點組態的解析程式的連接字串。  
  
-   **MapName**。 這個屬性是用來判斷要載入的解析程式，以及要執行的 BizTalk 對應的連接字串。 對應的完整限定的名稱可用來解析程式的連接字串取代。  
  
-   **驗證**。 當設定為**True** （預設值），ESB 發送器解譯器元件會指示 ESB 轉換服務來驗證針對來源結構描述中的對應，會定義來源訊息會解析並執行。