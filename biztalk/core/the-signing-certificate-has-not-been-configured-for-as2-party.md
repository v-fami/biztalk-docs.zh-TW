---
title: 簽署的憑證尚未針對 AS2 合作對象設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82928a39-3acf-447b-a0e8-f7c25b6f38dc
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61802b5e86319d0fe73f11c22249b72af1441b5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279646"
---
# <a name="the-signing-certificate-has-not-been-configured-for-as2-party"></a><span data-ttu-id="43d3e-102">簽署的憑證尚未針對 AS2 合作對象設定</span><span class="sxs-lookup"><span data-stu-id="43d3e-102">The Signing Certificate has not been configured for AS2 party</span></span>
## <a name="details"></a><span data-ttu-id="43d3e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="43d3e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43d3e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="43d3e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="43d3e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="43d3e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="43d3e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="43d3e-106">Event ID</span></span>|-|  
|<span data-ttu-id="43d3e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="43d3e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="43d3e-108">EDI</span><span class="sxs-lookup"><span data-stu-id="43d3e-108"> EDI</span></span>|  
|<span data-ttu-id="43d3e-109">元件</span><span class="sxs-lookup"><span data-stu-id="43d3e-109">Component</span></span>|<span data-ttu-id="43d3e-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="43d3e-110">AS2 Engine</span></span>|  
|<span data-ttu-id="43d3e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="43d3e-111">Symbolic Name</span></span>|<span data-ttu-id="43d3e-112">SigningCertNotConfiguredError</span><span class="sxs-lookup"><span data-stu-id="43d3e-112">SigningCertNotConfiguredError</span></span>|  
|<span data-ttu-id="43d3e-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="43d3e-113">Message Text</span></span>|<span data-ttu-id="43d3e-114">尚未針對 AS2 合作對象設定簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="43d3e-114">The Signing Certificate has not been configured for AS2 party.</span></span>  <span data-ttu-id="43d3e-115">AS2-從： {0} AS2-以： {1}</span><span class="sxs-lookup"><span data-stu-id="43d3e-115">AS2-From: {0} AS2-To: {1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="43d3e-116">說明</span><span class="sxs-lookup"><span data-stu-id="43d3e-116">Explanation</span></span>  
 <span data-ttu-id="43d3e-117">這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄訊息因為未簽署的憑證設定群組。</span><span class="sxs-lookup"><span data-stu-id="43d3e-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the signing certificate was not configured for the group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="43d3e-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="43d3e-118">User Action</span></span>  
 <span data-ttu-id="43d3e-119">若要解決這個錯誤，請透過下列方式設定簽署憑證：</span><span class="sxs-lookup"><span data-stu-id="43d3e-119">To resolve this error, configure signing certificate by doing the following:</span></span>  
  
1.  <span data-ttu-id="43d3e-120">開啟 [BizTalk Server 管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="43d3e-120">Open the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="43d3e-121">移至 [群組] 節點，然後按一下 [憑證] 節點。</span><span class="sxs-lookup"><span data-stu-id="43d3e-121">Move to the Group node, and click the Certificate node.</span></span>  
  
3.  <span data-ttu-id="43d3e-122">輸入一般名稱和憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="43d3e-122">Enter the common name and thumbprint of the certificate.</span></span>