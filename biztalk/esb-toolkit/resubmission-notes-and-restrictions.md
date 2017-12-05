---
title: "重新提交資訊和限制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 391064a9-1d61-4b10-97ab-d93b37d1ae23
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d03c969dc056e251d8109ce5bc0a29c16f8ffeda
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="resubmission-notes-and-restrictions"></a>重新提交資訊和限制
下列的注意事項和限制適用於重新提交程序：  
  
-   您可以重新提交 XML 訊息，ESB WCF 上手，SOAP (ASMX) 上手，或任何 HTTP 接收位置。  
  
-   WCF 上手的預設 URL 為 http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc。  
  
-   入口網站的 Web.config 檔案中定義端點詳細資料的 WCF 上手中**\<用戶端\>**節點 **\<System.ServiceModel\>** 一節。 以下是預設值。  
  
    ```  
    <endpoint  
      address="http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc"  
      binding="wsHttpBinding"  
      bindingConfiguration="WSHttpBinding_ITwoWayAsyncVoid"  
      contract="ProcessRequest"   
      name="WSHttpBinding_ITwoWayAsyncVoid">                  
    </endpoint>  
    ```  
  
-   如果 WCF 上手位於遠端伺服器上，您必須更新為指向正確的伺服器位址。  
  
-   SOAP (ASMX) 上手的預設 URL 為 http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx。  
  
-   入口網站的 Web.config 檔案會定義 SOAP (ASMX) 上手中的組態 **\<applicationSettings\>**  > 一節。 以下是預設值。  
  
    ```  
    <setting   
      name="Microsoft_Practices_ESB_Portal_ProcessItinerary_Process"  
      serializeAs="String">  
      <value>  
        http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx  
      </value>  
    </setting>  
    ```  
  
-   如果 ASMX 上手位於遠端伺服器上，您需要更新具有正確的伺服器位址的 URL。  
  
-   您可以重新提交一般檔案格式的訊息僅為 HTTP 接收位置。 您無法將其發行到 WCF 或 SOAP 上手。 您必須確定 HTTP 接收位置有適當的管線可以耗用和/或剖析一般檔案。  
  
-   重新提交的訊息未包含任何原始訊息的內容屬性。  
  
-   重新提交適用於只有訊息本文。它不適用於整個訊息。  
  
-   這個重新送出程序支援只有單一部分訊息。 您不能使用多部分訊息重新提交程序。  
  
-   您無法重新送出二進位格式的郵件。