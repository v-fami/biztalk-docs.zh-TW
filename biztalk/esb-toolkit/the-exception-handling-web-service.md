---
title: 例外狀況處理 Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dfe6ebdf-9b92-40c7-93fb-afd6c5f68aaa
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1bcc8146947f5e3cbaf58e31d1f515a055d102c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974303"
---
# <a name="the-exception-handling-web-service"></a><span data-ttu-id="bf608-102">例外狀況處理 Web 服務</span><span class="sxs-lookup"><span data-stu-id="bf608-102">The Exception Handling Web Service</span></span>
<span data-ttu-id="bf608-103">例外狀況處理 Web 服務接受的錯誤訊息，並將其發佈至 ESB 例外狀況入口網站。</span><span class="sxs-lookup"><span data-stu-id="bf608-103">The Exception Handling Web service accepts a fault message and publishes it to the ESB Exception Portal.</span></span> <span data-ttu-id="bf608-104">用戶端應用程式可以建立例外狀況訊息，並將它們提交到 ESB，針對該例外狀況類型或泛型處理常式中，設定任何處理常式可以處理的例外狀況的地方。</span><span class="sxs-lookup"><span data-stu-id="bf608-104">A client application can create exception messages and submit them to the ESB, where any handler configured for that exception type, or a generic handler, can process the exception.</span></span> <span data-ttu-id="bf608-105">這項服務的主要優點是它可讓參與 ESB 例外狀況處理機制的 ESB 應用程式外部的實體。</span><span class="sxs-lookup"><span data-stu-id="bf608-105">The major benefit of this service is that it allows entities outside an ESB application to participate in the ESB exception handling mechanism.</span></span>  
  
 <span data-ttu-id="bf608-106">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含這項服務的兩個版本： ASP.NET (ASMX) 版本和 Windows Communication Foundation (WCF) 版本。</span><span class="sxs-lookup"><span data-stu-id="bf608-106">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains two versions of this service: an ASP.NET (ASMX) version and a Windows Communication Foundation (WCF) version.</span></span> <span data-ttu-id="bf608-107">服務名稱為**ESB。ExceptionHandlingServices**和**ESB。ExceptionHandlingServices.WCF**，分別與服務會公開單一方法：</span><span class="sxs-lookup"><span data-stu-id="bf608-107">The service names are **ESB.ExceptionHandlingServices** and **ESB.ExceptionHandlingServices.WCF**, respectively, and the services expose a single method:</span></span>  
  
- <span data-ttu-id="bf608-108">**SubmitFault**。</span><span class="sxs-lookup"><span data-stu-id="bf608-108">**SubmitFault**.</span></span> <span data-ttu-id="bf608-109">這個方法會採用的執行個體**FaultMessage**類別，並沒有傳回值。</span><span class="sxs-lookup"><span data-stu-id="bf608-109">This method takes an instance of the **FaultMessage** class and has no return value.</span></span>  
  
  <span data-ttu-id="bf608-110">如需方法的例外狀況處理機制搭配運作的資訊，請參閱[使用 ESB 例外狀況管理](../esb-toolkit/using-esb-exception-management.md)。</span><span class="sxs-lookup"><span data-stu-id="bf608-110">For information about the way the exception handling mechanism works, see [Using ESB Exception Management](../esb-toolkit/using-esb-exception-management.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf608-111">根據預設，例外狀況處理 Web 服務未設定為需要 Secure Sockets Layer (SSL) 用戶端存取時。</span><span class="sxs-lookup"><span data-stu-id="bf608-111">By default, the Exception Handling Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients.</span></span> <span data-ttu-id="bf608-112">您應該設定服務，因此它需要 SSL 用戶端存取和保護 Internet Information Services (IIS) Web 服務主機電腦和裝載的伺服器之間的連線**ESBExceptions**資料庫使用網路層級 IPSec 和適當的檔案層級存取控制清單 (ACL) 權限。</span><span class="sxs-lookup"><span data-stu-id="bf608-112">You should configure the service so that it requires SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and the server that hosts the **ESBExceptions** database using network-level IPSec and appropriate file-level access control list (ACL) permissions.</span></span>