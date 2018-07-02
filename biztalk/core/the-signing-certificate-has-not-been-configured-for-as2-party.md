---
title: 簽署的憑證尚未設定 AS2 合作對象 |Microsoft Docs
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
ms.openlocfilehash: 4d26323670f0229377b304e5f51671de8ef10021
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967543"
---
# <a name="the-signing-certificate-has-not-been-configured-for-as2-party"></a><span data-ttu-id="696d6-102">簽署的憑證尚未設定 AS2 合作對象</span><span class="sxs-lookup"><span data-stu-id="696d6-102">The Signing Certificate has not been configured for AS2 party</span></span>
## <a name="details"></a><span data-ttu-id="696d6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="696d6-103">Details</span></span>  
  
|                 |                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------|
|  <span data-ttu-id="696d6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="696d6-104">Product Name</span></span>   |    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]     |
| <span data-ttu-id="696d6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="696d6-105">Product Version</span></span> |                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                 |
|    <span data-ttu-id="696d6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="696d6-106">Event ID</span></span>     |                                             -                                             |
|  <span data-ttu-id="696d6-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="696d6-107">Event Source</span></span>   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="696d6-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="696d6-108"> EDI</span></span>   |
|    <span data-ttu-id="696d6-109">元件</span><span class="sxs-lookup"><span data-stu-id="696d6-109">Component</span></span>    |                                        <span data-ttu-id="696d6-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="696d6-110">AS2 Engine</span></span>                                         |
|  <span data-ttu-id="696d6-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="696d6-111">Symbolic Name</span></span>  |                               <span data-ttu-id="696d6-112">SigningCertNotConfiguredError</span><span class="sxs-lookup"><span data-stu-id="696d6-112">SigningCertNotConfiguredError</span></span>                               |
|  <span data-ttu-id="696d6-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="696d6-113">Message Text</span></span>   | <span data-ttu-id="696d6-114">簽署的憑證尚未設定 AS2 合作對象。</span><span class="sxs-lookup"><span data-stu-id="696d6-114">The Signing Certificate has not been configured for AS2 party.</span></span>  <span data-ttu-id="696d6-115">AS2-從： {0} AS2-來： {1}</span><span class="sxs-lookup"><span data-stu-id="696d6-115">AS2-From: {0} AS2-To: {1}</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="696d6-116">說明</span><span class="sxs-lookup"><span data-stu-id="696d6-116">Explanation</span></span>  
 <span data-ttu-id="696d6-117">這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄訊息因為群組未設定簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="696d6-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the signing certificate was not configured for the group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="696d6-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="696d6-118">User Action</span></span>  
 <span data-ttu-id="696d6-119">若要解決這個錯誤，請透過下列方式設定簽署憑證：</span><span class="sxs-lookup"><span data-stu-id="696d6-119">To resolve this error, configure signing certificate by doing the following:</span></span>  
  
1.  <span data-ttu-id="696d6-120">開啟 [BizTalk Server 管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="696d6-120">Open the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="696d6-121">移至 [群組] 節點，然後按一下 [憑證] 節點。</span><span class="sxs-lookup"><span data-stu-id="696d6-121">Move to the Group node, and click the Certificate node.</span></span>  
  
3.  <span data-ttu-id="696d6-122">輸入一般名稱和憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="696d6-122">Enter the common name and thumbprint of the certificate.</span></span>