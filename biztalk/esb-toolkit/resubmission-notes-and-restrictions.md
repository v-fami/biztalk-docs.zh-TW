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
# <a name="resubmission-notes-and-restrictions"></a><span data-ttu-id="c5681-102">重新提交資訊和限制</span><span class="sxs-lookup"><span data-stu-id="c5681-102">Resubmission Notes and Restrictions</span></span>
<span data-ttu-id="c5681-103">下列的注意事項和限制適用於重新提交程序：</span><span class="sxs-lookup"><span data-stu-id="c5681-103">The following notes and restrictions apply to the resubmission process:</span></span>  
  
-   <span data-ttu-id="c5681-104">您可以重新提交 XML 訊息，ESB WCF 上手，SOAP (ASMX) 上手，或任何 HTTP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="c5681-104">You can resubmit XML messages to the ESB WCF on-ramp, SOAP (ASMX) on-ramp, or any HTTP receive location.</span></span>  
  
-   <span data-ttu-id="c5681-105">WCF 上手的預設 URL 為 http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc。</span><span class="sxs-lookup"><span data-stu-id="c5681-105">The default URL for the WCF on-ramp is http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc.</span></span>  
  
-   <span data-ttu-id="c5681-106">入口網站的 Web.config 檔案中定義端點詳細資料的 WCF 上手中**\<用戶端\>**節點 **\<System.ServiceModel\>** 一節。</span><span class="sxs-lookup"><span data-stu-id="c5681-106">The portal Web.config file defines the endpoint details for the WCF on-ramp in the **\<Client\>** node of the **\<System.ServiceModel\>** section.</span></span> <span data-ttu-id="c5681-107">以下是預設值。</span><span class="sxs-lookup"><span data-stu-id="c5681-107">The following is the default value.</span></span>  
  
    ```  
    <endpoint  
      address="http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc"  
      binding="wsHttpBinding"  
      bindingConfiguration="WSHttpBinding_ITwoWayAsyncVoid"  
      contract="ProcessRequest"   
      name="WSHttpBinding_ITwoWayAsyncVoid">                  
    </endpoint>  
    ```  
  
-   <span data-ttu-id="c5681-108">如果 WCF 上手位於遠端伺服器上，您必須更新為指向正確的伺服器位址。</span><span class="sxs-lookup"><span data-stu-id="c5681-108">If the WCF on-ramp resides on a remote server, you must update the address to point to the correct server.</span></span>  
  
-   <span data-ttu-id="c5681-109">SOAP (ASMX) 上手的預設 URL 為 http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx。</span><span class="sxs-lookup"><span data-stu-id="c5681-109">The default URL for the SOAP (ASMX) on-ramp is http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx.</span></span>  
  
-   <span data-ttu-id="c5681-110">入口網站的 Web.config 檔案會定義 SOAP (ASMX) 上手中的組態 **\<applicationSettings\>**  > 一節。</span><span class="sxs-lookup"><span data-stu-id="c5681-110">The portal Web.config file defines the configuration for the SOAP (ASMX) on-ramp in the **\<applicationSettings\>** section.</span></span> <span data-ttu-id="c5681-111">以下是預設值。</span><span class="sxs-lookup"><span data-stu-id="c5681-111">The following is the default value.</span></span>  
  
    ```  
    <setting   
      name="Microsoft_Practices_ESB_Portal_ProcessItinerary_Process"  
      serializeAs="String">  
      <value>  
        http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx  
      </value>  
    </setting>  
    ```  
  
-   <span data-ttu-id="c5681-112">如果 ASMX 上手位於遠端伺服器上，您需要更新具有正確的伺服器位址的 URL。</span><span class="sxs-lookup"><span data-stu-id="c5681-112">If the ASMX on-ramp resides on a remote server, you need to update the URL with the correct server address.</span></span>  
  
-   <span data-ttu-id="c5681-113">您可以重新提交一般檔案格式的訊息僅為 HTTP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="c5681-113">You can resubmit flat file formatted messages only to an HTTP receive location.</span></span> <span data-ttu-id="c5681-114">您無法將其發行到 WCF 或 SOAP 上手。</span><span class="sxs-lookup"><span data-stu-id="c5681-114">You cannot submit them to a WCF or SOAP on-ramp.</span></span> <span data-ttu-id="c5681-115">您必須確定 HTTP 接收位置有適當的管線可以耗用和/或剖析一般檔案。</span><span class="sxs-lookup"><span data-stu-id="c5681-115">You must ensure that the HTTP receive location has the appropriate pipeline that can consume and/or parse the flat file.</span></span>  
  
-   <span data-ttu-id="c5681-116">重新提交的訊息未包含任何原始訊息的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="c5681-116">The resubmitted message does not contain any of the context properties of the original message.</span></span>  
  
-   <span data-ttu-id="c5681-117">重新提交適用於只有訊息本文。它不適用於整個訊息。</span><span class="sxs-lookup"><span data-stu-id="c5681-117">Resubmission applies to only the message body; it does not apply to the entire message.</span></span>  
  
-   <span data-ttu-id="c5681-118">這個重新送出程序支援只有單一部分訊息。</span><span class="sxs-lookup"><span data-stu-id="c5681-118">The resubmission process supports only single-part messages.</span></span> <span data-ttu-id="c5681-119">您不能使用多部分訊息重新提交程序。</span><span class="sxs-lookup"><span data-stu-id="c5681-119">You cannot use the resubmission process with multi-part messages.</span></span>  
  
-   <span data-ttu-id="c5681-120">您無法重新送出二進位格式的郵件。</span><span class="sxs-lookup"><span data-stu-id="c5681-120">You cannot resubmit binary-formatted messages.</span></span>