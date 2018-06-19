---
title: FIN 回應對帳疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, troubleshooting
- troubleshooting, FIN Response Reconciliation
ms.assetid: f62326aa-9a4e-4941-a9bb-20bde980f99e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a92812086f191d5777b387d9861b32a3147c1e96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207414"
---
# <a name="fin-response-reconciliation-troubleshooting"></a><span data-ttu-id="9885d-102">FIN 回應對帳疑難排解</span><span class="sxs-lookup"><span data-stu-id="9885d-102">FIN Response Reconciliation Troubleshooting</span></span>
## <a name="the-frr-bam-view-does-not-show-the-message-type-of-a-message"></a><span data-ttu-id="9885d-103">FRR BAM 檢視不會顯示一則訊息的訊息類型</span><span class="sxs-lookup"><span data-stu-id="9885d-103">The FRR BAM view does not show the message type of a message</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="9885d-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="9885d-104">Symptom</span></span>  
 <span data-ttu-id="9885d-105">MRSR 站台中 FRR BAM 檢視不會顯示一個或多個訊息的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="9885d-105">The FRR BAM view in MRSR site does not show the message type for one or more messages.</span></span> <span data-ttu-id="9885d-106">顯示的訊息或訊息的所有其他資料，且會顯示訊息類型的所有其他訊息類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9885d-106">All other data for the message or messages is shown, and the message type is shown for instances of all other message types.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="9885d-107">可能的原因</span><span class="sxs-lookup"><span data-stu-id="9885d-107">Possible Cause</span></span>  
 <span data-ttu-id="9885d-108">FRRMessageOut 活動不會記錄 F21 訊息 (Ack/NAKs) 的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="9885d-108">The FRRMessageOut activity does not record the message type for F21 messages (ACKs/NAKs).</span></span>  
  
### <a name="solution"></a><span data-ttu-id="9885d-109">方案</span><span class="sxs-lookup"><span data-stu-id="9885d-109">Solution</span></span>  
 <span data-ttu-id="9885d-110">如果您遇到這個問題，解譯為 F21 訊息 MRSR 站台中 FRR BAM 檢視中所列出的訊息類型沒有任何訊息。</span><span class="sxs-lookup"><span data-stu-id="9885d-110">If you encounter this problem, interpret any message that does not have a message type listed in the FRR BAM view in MRSR site as an F21 message.</span></span>  
  
## <a name="deploying-system-level-schemas-in-a-project-generates-an-error"></a><span data-ttu-id="9885d-111">部署系統層級專案中的結構描述會產生錯誤</span><span class="sxs-lookup"><span data-stu-id="9885d-111">Deploying system-level schemas in a project generates an error</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="9885d-112">徵兆</span><span class="sxs-lookup"><span data-stu-id="9885d-112">Symptom</span></span>  
 <span data-ttu-id="9885d-113">當您嘗試將部署系統層級中的結構描述 FrrSchemas.dll 專案中時，您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="9885d-113">When you attempt to deploy the system-level schemas in FrrSchemas.dll in a project, you receive an error.</span></span> <span data-ttu-id="9885d-114">如需這些結構描述的清單，請參閱[FIN 回應類型](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9885d-114">For a list of these schemas, see [FIN Response Types](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md).</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="9885d-115">可能的原因</span><span class="sxs-lookup"><span data-stu-id="9885d-115">Possible Cause</span></span>  
 <span data-ttu-id="9885d-116">系統層級中的結構描述 FrrSchemas.dll FrrSchemas.dll 中已部署。</span><span class="sxs-lookup"><span data-stu-id="9885d-116">The system-level schemas in FrrSchemas.dll are already deployed in FrrSchemas.dll.</span></span> <span data-ttu-id="9885d-117">嘗試將其部署一次產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9885d-117">Trying to deploy them again results in an error.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="9885d-118">方案</span><span class="sxs-lookup"><span data-stu-id="9885d-118">Solution</span></span>  
 <span data-ttu-id="9885d-119">沒有需要部署系統層級中的結構描述 FrrSchemas.dll。</span><span class="sxs-lookup"><span data-stu-id="9885d-119">There is no need to deploy the system-level schemas in FrrSchemas.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9885d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9885d-120">See Also</span></span>  
 [<span data-ttu-id="9885d-121">疑難排解： 問題與解決方式</span><span class="sxs-lookup"><span data-stu-id="9885d-121">Troubleshooting: Issues and Resolutions</span></span>](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)