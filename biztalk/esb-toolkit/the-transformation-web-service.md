---
title: "轉換 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 788bf4a9-a63b-4fd3-93a2-6e34a1464049
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5abad7a5a7bae3c76fba58ecd92fc3384df5ca25
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-transformation-web-service"></a><span data-ttu-id="66bb7-102">轉換 Web 服務</span><span class="sxs-lookup"><span data-stu-id="66bb7-102">The Transformation Web Service</span></span>
<span data-ttu-id="66bb7-103">轉換 Web 服務可讓外部應用程式提交至 ESB 應用程式的文件，並使用已部署的 Microsoft BizTalk 對應轉換。</span><span class="sxs-lookup"><span data-stu-id="66bb7-103">The Transformation Web service enables external applications to submit a document to an ESB application and have it transformed using a deployed Microsoft BizTalk map.</span></span> <span data-ttu-id="66bb7-104">不同於轉換代理程式時，此服務不會路由訊息到 BizTalk Messagebox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="66bb7-104">Unlike the transformation agent, this service does not route messages through the BizTalk Message Box database.</span></span>  
  
 <span data-ttu-id="66bb7-105">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含此服務的兩個版本： ASP.NET (ASMX) 版本和 Windows Communication Foundation (WCF) 版本。</span><span class="sxs-lookup"><span data-stu-id="66bb7-105">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains two versions of this service: an ASP.NET (ASMX) version and a Windows Communication Foundation (WCF) version.</span></span> <span data-ttu-id="66bb7-106">服務名稱就是**ESB。TransformServices**和**ESB。TransformServices.WCF**分別和服務會公開單一方法：</span><span class="sxs-lookup"><span data-stu-id="66bb7-106">The service names are **ESB.TransformServices** and **ESB.TransformServices.WCF**, respectively, and the services expose a single method:</span></span>  
  
-   <span data-ttu-id="66bb7-107">**轉換。**</span><span class="sxs-lookup"><span data-stu-id="66bb7-107">**Transform.**</span></span> <span data-ttu-id="66bb7-108">這個方法會採用做為參數**字串**，其中包含要轉換的訊息和**字串**，其中包含完整部署在 BizTalk 對應的名稱。</span><span class="sxs-lookup"><span data-stu-id="66bb7-108">This method takes as parameters a **String** that contains the message to transform and a **String** that contains the fully qualified name of a map deployed in BizTalk.</span></span> <span data-ttu-id="66bb7-109">方法會傳回**字串**，其中包含已轉換的文件。</span><span class="sxs-lookup"><span data-stu-id="66bb7-109">The method returns a **String** that contains the transformed document.</span></span> <span data-ttu-id="66bb7-110">使用字串參數，可降低在異質環境; 中的互通性問題的風險不過，請記住，這是 Web 服務，因此您應該避免使用它來轉換 （Transformation Service，在 BizTalk 中較適合大型文件） 的大型文件。</span><span class="sxs-lookup"><span data-stu-id="66bb7-110">The use of string parameters reduces the risk of interoperability issues in a heterogeneous environment; however, keep in mind that this is a Web service, so you should avoid using it to transform large documents (the Transformation Service in BizTalk is better suited for large documents).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66bb7-111">根據預設，轉換 Web 服務不會設定為需要安全通訊端層 (SSL) 用戶端存取時。</span><span class="sxs-lookup"><span data-stu-id="66bb7-111">By default, the Transformation Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients.</span></span> <span data-ttu-id="66bb7-112">您應該設定服務，讓需要 SSL 用戶端存取，並保護網際網路資訊服務 (IIS) Web 服務主機電腦與您使用網路層級 IPSec 和適當的檔案層級存取權的 BizTalk Server 之間的連線控制清單 (ACL) 權限。</span><span class="sxs-lookup"><span data-stu-id="66bb7-112">You should configure the service so that it requires SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and your BizTalk Server using network-level IPSec and appropriate file-level access control list (ACL) permissions.</span></span>