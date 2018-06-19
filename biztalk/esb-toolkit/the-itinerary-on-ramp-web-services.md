---
title: 路線上手 Web Services |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7551974-b9d2-4ae3-b54c-3aa5ba058e95
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36d3724a6cd57dca8157c05e95d9e196f0fb6cf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295430"
---
# <a name="the-itinerary-on-ramp-web-services"></a><span data-ttu-id="6ecd9-102">路線上手 Web 服務</span><span class="sxs-lookup"><span data-stu-id="6ecd9-102">The Itinerary On-Ramp Web Services</span></span>
<span data-ttu-id="6ecd9-103">路線上手，公開的方法，可讓用戶端將訊息提交以處理路線服務，然後向前目標 Microsoft BizTalk 或 ESB 作業路線 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-103">The Itinerary Web service is an itinerary on-ramp that exposes a method that allows clients to submit messages for processing by the Itinerary Service and then onward to the target Microsoft BizTalk or ESB operations.</span></span>  
  
 <span data-ttu-id="6ecd9-104">行程 Web 服務給裝載 ESB 行程管線元件中，會驗證以確認這些服務會定義在路線[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]組態。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-104">The Itinerary Web service passes the payload to the ESB Itinerary pipeline components, which validates the itinerary to verify that these services are defined in the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] configuration.</span></span> <span data-ttu-id="6ecd9-105">然後元件會將特殊的內容屬性加入至包含已驗證的行程的訊息。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-105">Then the component adds special context properties to the message containing the validated itinerary.</span></span>  
  
 <span data-ttu-id="6ecd9-106">在泛型路線上手，訊息提交期間未提供 SOAP 標頭包含路線。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-106">In the case of a generic itinerary on-ramp, a SOAP header containing an itinerary is not provided during message submission.</span></span> <span data-ttu-id="6ecd9-107">同理，ESB 行程選取器管線元件用來取代 ESB 行程管線元件。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-107">Accordingly, the ESB Itinerary Selector pipeline component is used in place of the ESB Itinerary pipeline component.</span></span> <span data-ttu-id="6ecd9-108">ESB 行程選取器管線元件會解析路線根據預先定義的解析程式的連接字串，並提供相同 ESB 行程管線元件所提供的驗證。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-108">The ESB Itinerary Selector pipeline component resolves the itinerary based on a pre-defined resolver connection string, and it provides the same validation that the ESB Itinerary pipeline component provides.</span></span>  
  
 <span data-ttu-id="6ecd9-109">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含路線服務來支援單向和要求-回應訊息交換模式的兩種變化。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-109">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes two variations of the Itinerary service to support both one-way and request-response message-exchange patterns.</span></span> <span data-ttu-id="6ecd9-110">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含 ASP.NET (ASMX) 和 Windows Communication Foundation (WCF) 版本的這兩項服務，並提供泛型版本的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-110">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains an ASP.NET (ASMX) and a Windows Communication Foundation (WCF) version of both of these services, and it provides generic versions of the WCF services.</span></span>  
  
 <span data-ttu-id="6ecd9-111">提供的單向路線服務的名稱是**ESB。ItineraryService**， **ESB。ItineraryServices.WCF**，和**ESB。ItineraryServices.Generic.WCF**。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-111">The names of the provided one-way itinerary services are **ESB.ItineraryService**, **ESB.ItineraryServices.WCF**, and **ESB.ItineraryServices.Generic.WCF**.</span></span>  
  
 <span data-ttu-id="6ecd9-112">提供雙向的路線服務的名稱是**ESB。ItineraryServices.Response**， **ESB。ItineraryServices.Response.WCF**，和**ESB。ItineraryServices.Generic.Response.WCF**。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-112">The names of the provided two-way itinerary services are **ESB.ItineraryServices.Response**, **ESB.ItineraryServices.Response.WCF**, and **ESB.ItineraryServices.Generic.Response.WCF**.</span></span>  
  
 <span data-ttu-id="6ecd9-113">每個行程 Web 服務會公開下列方法：</span><span class="sxs-lookup"><span data-stu-id="6ecd9-113">Each of the Itinerary Web services exposes the following methods:</span></span>  
  
-   <span data-ttu-id="6ecd9-114">**SubmitRequest**。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-114">**SubmitRequest**.</span></span> <span data-ttu-id="6ecd9-115">Asmx 服務，這個方法會採用的執行個體**XmlNode**類別，其中包含要提交的訊息。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-115">For the ASMX-based service, this method takes an instance of the **XmlNode** class that contains the message to submit.</span></span> <span data-ttu-id="6ecd9-116">WCF 型服務，這個方法會採用 XML 字串，其中包含要提交的訊息。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-116">For the WCF-based service, this method takes an XML string that contains the message to submit.</span></span>  
  
-   <span data-ttu-id="6ecd9-117">**SubmitRequestResponse**。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-117">**SubmitRequestResponse**.</span></span> <span data-ttu-id="6ecd9-118">Asmx 服務，這個方法會採用的執行個體的參考**XmlNode**類別，其中包含要提交的訊息，並傳回回應訊息執行個體中**XmlNode**傳遞至它。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-118">For the ASMX-based service, this method takes a reference to an instance of the **XmlNode** class that contains the message to submit and returns the response message in the instance of the **XmlNode** passed to it.</span></span> <span data-ttu-id="6ecd9-119">WCF 型服務，這個方法會採用參考**物件**類型，它是 XML 字串，其中包含要提交的訊息，並傳回陣列**XmlNodes**中**物件**傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-119">For the WCF-based service, this method takes a reference to an **Object** type that is an XML string that contains the message to submit and returns an array of **XmlNodes** in the **Object** that was passed to it.</span></span>  
  
 <span data-ttu-id="6ecd9-120">如需使用路線 Web 服務的詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-120">For more information about using the Itinerary Web services, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ecd9-121">根據預設，路線 Web 服務不會設定為需要安全通訊端層 (SSL) 用戶端存取時。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-121">By default, the Itinerary Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients.</span></span> <span data-ttu-id="6ecd9-122">您應該設定為要求 SSL 用戶端存取和保護網際網路資訊服務 (IIS) Web 服務主機電腦和裝載使用網路層級 IPSec ESBExceptions 資料庫的伺服器之間的連線並適當的服務檔案層級存取控制清單 (ACL) 權限。</span><span class="sxs-lookup"><span data-stu-id="6ecd9-122">You should configure the service to require SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and the server that hosts the ESBExceptions database using a network-level IPSec and appropriate file-level access control list (ACL) permissions.</span></span>