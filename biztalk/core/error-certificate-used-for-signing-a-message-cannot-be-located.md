---
title: 在本機憑證存放區中找不到用於簽章訊息的憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ff3c7a2-954c-4c62-a7b2-06f7a38d61b3
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: feb6a4cc1e5272a4a2c6760ca4585dd0dc10c031
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001359"
---
# <a name="the-certificate-used-for-signing-a-message-cannot-be-located-in-the-local-certificate-store"></a><span data-ttu-id="fcf75-102">在本機憑證存放區中找不到用於簽章訊息的憑證</span><span class="sxs-lookup"><span data-stu-id="fcf75-102">The certificate used for signing a message cannot be located in the local certificate store</span></span>
## <a name="details"></a><span data-ttu-id="fcf75-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fcf75-103">Details</span></span>  
  
|                 |                                                                                                                          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="fcf75-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fcf75-104">Product Name</span></span>   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                    |
| <span data-ttu-id="fcf75-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="fcf75-105">Product Version</span></span> |                                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                |
|    <span data-ttu-id="fcf75-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fcf75-106">Event ID</span></span>     |                                                            -                                                             |
|  <span data-ttu-id="fcf75-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="fcf75-107">Event Source</span></span>   |                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="fcf75-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="fcf75-108"> EDI</span></span>                  |
|    <span data-ttu-id="fcf75-109">元件</span><span class="sxs-lookup"><span data-stu-id="fcf75-109">Component</span></span>    |                                                        <span data-ttu-id="fcf75-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="fcf75-110">AS2 Engine</span></span>                                                        |
|  <span data-ttu-id="fcf75-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fcf75-111">Symbolic Name</span></span>  |                                                 <span data-ttu-id="fcf75-112">CertificateMissingError</span><span class="sxs-lookup"><span data-stu-id="fcf75-112">CertificateMissingError</span></span>                                                  |
|  <span data-ttu-id="fcf75-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fcf75-113">Message Text</span></span>   | <span data-ttu-id="fcf75-114">在本機憑證存放區中找不到訊息中簽章所用的憑證。</span><span class="sxs-lookup"><span data-stu-id="fcf75-114">The certificate used for signing a message cannot be located in the local certificate store.</span></span> <span data-ttu-id="fcf75-115">憑證指紋： {0}</span><span class="sxs-lookup"><span data-stu-id="fcf75-115">Certificate thumbprint: {0}</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="fcf75-116">說明</span><span class="sxs-lookup"><span data-stu-id="fcf75-116">Explanation</span></span>  
 <span data-ttu-id="fcf75-117">這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄訊息因為識別做為簽署憑證的憑證無法在所需的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="fcf75-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the certificate identified as the signing certificate was not in the required certificate store.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fcf75-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fcf75-118">User Action</span></span>  
 <span data-ttu-id="fcf75-119">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="fcf75-119">To resolve this error, do the following:</span></span>  
  
1.  <span data-ttu-id="fcf75-120">藉由開啟 BizTalk Server 管理主控台，以滑鼠右鍵按一下 [BizTalk 群組]，然後按一下 [憑證] 節點中識別的簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="fcf75-120">Identify the signing certificate by opening the BizTalk Server Administration Console, right-clicking the BizTalk Group, and then clicking the Certificate node.</span></span>  
  
2.  <span data-ttu-id="fcf75-121">開啟 MMC、 新增嵌入式管理單元的我的使用者帳戶，然後開啟憑證，個人和憑證 節點。</span><span class="sxs-lookup"><span data-stu-id="fcf75-121">Open MMC, add the snap-in for the My user account, and then open the Certificates, Personal, and Certificates node.</span></span>  
  
3.  <span data-ttu-id="fcf75-122">確定目前的使用者憑證存放區尋找指紋識別的錯誤訊息文字中包含該簽署憑證的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="fcf75-122">Make sure that the Current User certificate store contains the private key for that signing certificate by looking for the thumbprint identified in the error message text.</span></span>