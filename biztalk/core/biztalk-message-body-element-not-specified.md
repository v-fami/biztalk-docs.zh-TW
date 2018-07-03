---
title: 未指定 BizTalk 訊息內文元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af5d63c0-af96-4e34-828f-d29638cdf46d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 206cbea171b3453fed7e7db7d5c67d658fcccc10
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994543"
---
# <a name="biztalk-message-body-element-not-specified"></a><span data-ttu-id="cb410-102">未指定 BizTalk 訊息內文元素</span><span class="sxs-lookup"><span data-stu-id="cb410-102">BizTalk message body element not specified</span></span>
## <a name="details"></a><span data-ttu-id="cb410-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cb410-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="cb410-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cb410-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="cb410-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="cb410-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="cb410-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cb410-106">Event ID</span></span>     |                                         <span data-ttu-id="cb410-107">0</span><span class="sxs-lookup"><span data-stu-id="cb410-107">0</span></span>                                          |
|  <span data-ttu-id="cb410-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="cb410-108">Event Source</span></span>   |                                         <span data-ttu-id="cb410-109">0</span><span class="sxs-lookup"><span data-stu-id="cb410-109">0</span></span>                                          |
|    <span data-ttu-id="cb410-110">元件</span><span class="sxs-lookup"><span data-stu-id="cb410-110">Component</span></span>    |                                         <span data-ttu-id="cb410-111">0</span><span class="sxs-lookup"><span data-stu-id="cb410-111">0</span></span>                                          |
|  <span data-ttu-id="cb410-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cb410-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="cb410-113">0</span><span class="sxs-lookup"><span data-stu-id="cb410-113">0</span></span>                                          |
|  <span data-ttu-id="cb410-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cb410-114">Message Text</span></span>   |                     <span data-ttu-id="cb410-115">未指定 BizTalk 訊息內文元素</span><span class="sxs-lookup"><span data-stu-id="cb410-115">BizTalk message body element not specified</span></span>                     |
  
## <a name="explanation"></a><span data-ttu-id="cb410-116">說明</span><span class="sxs-lookup"><span data-stu-id="cb410-116">Explanation</span></span>  
 <span data-ttu-id="cb410-117">此錯誤表示使用了輸出 WCF 訊息的範本選項。</span><span class="sxs-lookup"><span data-stu-id="cb410-117">This error indicates the use of the template option for the outbound WCF message.</span></span> <span data-ttu-id="cb410-118">但範本運算式不包含 BizTalk 訊息內文元素。</span><span class="sxs-lookup"><span data-stu-id="cb410-118">However, the template expression doesn’t contain the BizTalk message body element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cb410-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cb410-119">User Action</span></span>  
 <span data-ttu-id="cb410-120">請確定範本運算式包含下列項目： \< **bts 訊息主體 xmlns ="<http://www.microsoft.com/schemas/bts2007>"編碼 ="[xml&#124;base64&#124;十六進位&#124;字串]"/**\>。</span><span class="sxs-lookup"><span data-stu-id="cb410-120">Ensure that the template expression contains the following element: \<**bts-msg-body xmlns="<http://www.microsoft.com/schemas/bts2007>" encoding="[xml&#124;base64&#124;hex&#124;string]"/**\>.</span></span>