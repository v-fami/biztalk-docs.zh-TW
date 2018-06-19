---
title: 使用 WCF 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- consuming, WCF services
- WCF services, consuming
ms.assetid: ca6c0514-c1df-43ad-8f02-df117271b0b5
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3fc0764295cbbc793b07757691e1f0c730a4049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237862"
---
# <a name="consuming-wcf-services"></a><span data-ttu-id="73236-102">使用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="73236-102">Consuming WCF Services</span></span>
<span data-ttu-id="73236-103">使用 WCF 服務可讓您將現有 WCF 服務加入商務程序中。</span><span class="sxs-lookup"><span data-stu-id="73236-103">Consuming WCF services enables you to add existing WCF services to your business process.</span></span> <span data-ttu-id="73236-104">您可以將數個 WCF 服務彙總成為一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="73236-104">You can aggregate several WCF services into a single orchestration.</span></span>  
  
 <span data-ttu-id="73236-105">您可以使用 [BizTalk WCF 服務使用精靈]，從協調流程使用 (呼叫) WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="73236-105">You can consume (call) a WCF service from your orchestration by using the BizTalk WCF Service Consuming Wizard.</span></span> <span data-ttu-id="73236-106">[BizTalk WCF 服務使用精靈] 會建立必要的連接埠類型和訊息類型來使用 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="73236-106">The BizTalk WCF Service Consuming Wizard creates port types and message types necessary for consuming WCF services.</span></span> <span data-ttu-id="73236-107">[BizTalk WCF 服務使用精靈] 所建立的兩個繫結檔案可透過開發命令列工具或精靈匯入，以便使用系統提供的繫結 WCF 配接器和 WCF-Custom 配接器來設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="73236-107">The BizTalk WCF Service Consuming Wizard also creates two binding files that can be imported by the development command-line tool or wizard to configure the send ports with the system-provided binding WCF adapters and the WCF-Custom adapter.</span></span> <span data-ttu-id="73236-108">此精靈可讓您將 SOAP 標頭與所使用 WCF 服務搭配使用、變更所使用 WCF 服務的 URI，以及動態設定所使用 Web 服務適用的 WCF。</span><span class="sxs-lookup"><span data-stu-id="73236-108">The wizard allows you to use SOAP headers with a consumed WCF service, change the URI of a consumed WCF service, and dynamically set the WCF for a consumed Web service.</span></span> <span data-ttu-id="73236-109">WCF 傳送配接器會使用 WCF 服務，而 WCF 接收位置會發佈 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="73236-109">WCF send adapters consume WCF services and WCF receive locations publish WCF services.</span></span>  
  
 <span data-ttu-id="73236-110">BizTalk WCF 傳送配接器包括表示 WCF 預先定義繫結五個實體傳送配接器**BasicHttpBinding**， **WsHttpBinding**， **NetTcpBinding**，**NetNamedPipeBinding**，和**NetMsmqBinding**。</span><span class="sxs-lookup"><span data-stu-id="73236-110">The BizTalk WCF send adapters include five physical send adapters that represent the WCF predefined bindings **BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**, **NetNamedPipeBinding**, and **NetMsmqBinding**.</span></span> <span data-ttu-id="73236-111">BizTalk WCF 配接器也包含自訂配接器，可讓您自由設定傳送埠適用的 WCF 繫結和行為資訊。</span><span class="sxs-lookup"><span data-stu-id="73236-111">The BizTalk WCF adapters also include the custom adapters that enable you to freely configure WCF binding and behavior information for a send port.</span></span> <span data-ttu-id="73236-112">如需如何設定 WCF 傳送處理常式和傳送埠的詳細資訊，請參閱 < how to 主題中的每個 WCF 配接器[WCF 配接器](../core/wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="73236-112">For more information about how to configure a WCF send handler and send port, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73236-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="73236-113">In This Section</span></span>  
  
-   [<span data-ttu-id="73236-114">傳送配接器使用 WCF 與 WCF 服務時的考量</span><span class="sxs-lookup"><span data-stu-id="73236-114">Considerations When Consuming WCF Services with the WCF Send Adapters</span></span>](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md)  
  
-   [<span data-ttu-id="73236-115">SOAP 標頭與使用的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="73236-115">SOAP Headers with Consumed WCF Services</span></span>](../core/soap-headers-with-consumed-wcf-services.md)  
  
-   [<span data-ttu-id="73236-116">設定動態傳送埠使用 WCF 配接器內容屬性</span><span class="sxs-lookup"><span data-stu-id="73236-116">Configuring Dynamic Send Ports Using WCF Adapters Context Properties</span></span>](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)  
  
-   [<span data-ttu-id="73236-117">如何使用 BizTalk WCF 服務使用精靈來取用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="73236-117">How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service</span></span>](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)  
  
-   [<span data-ttu-id="73236-118">如何處理協調流程中的具型別的的錯誤合約</span><span class="sxs-lookup"><span data-stu-id="73236-118">How to Handle Typed Fault Contracts in Orchestrations</span></span>](../core/how-to-handle-typed-fault-contracts-in-orchestrations.md)  
  
-   [<span data-ttu-id="73236-119">指定的 SOAP 動作，wcf 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="73236-119">Specifying SOAP Actions for WCF Send Adapters</span></span>](../core/specifying-soap-actions-for-wcf-send-adapters.md)