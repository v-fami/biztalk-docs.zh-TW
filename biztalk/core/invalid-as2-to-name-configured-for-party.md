---
title: 無效的 AS2-設定合作對象的名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a203e5f2-d1d9-433f-b2bb-d679bb8fea58
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84b97fc20ec6280557fdd050b25b17e2e068fc08
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970663"
---
# <a name="invalid-as2-to-name-configured-for-party"></a><span data-ttu-id="23df2-102">無效的 AS2-設定合作對象的名稱</span><span class="sxs-lookup"><span data-stu-id="23df2-102">Invalid AS2-To name configured for Party</span></span>
## <a name="details"></a><span data-ttu-id="23df2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="23df2-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="23df2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="23df2-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="23df2-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="23df2-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="23df2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="23df2-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="23df2-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="23df2-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="23df2-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="23df2-108"> EDI</span></span> |
|    <span data-ttu-id="23df2-109">元件</span><span class="sxs-lookup"><span data-stu-id="23df2-109">Component</span></span>    |                                       <span data-ttu-id="23df2-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="23df2-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="23df2-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="23df2-111">Symbolic Name</span></span>  |                            <span data-ttu-id="23df2-112">InvalidAS2ToNameConfiguredError</span><span class="sxs-lookup"><span data-stu-id="23df2-112">InvalidAS2ToNameConfiguredError</span></span>                             |
|  <span data-ttu-id="23df2-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="23df2-113">Message Text</span></span>   |               <span data-ttu-id="23df2-114">無效的 AS2-設定合作對象的名稱：{0}值： {1}</span><span class="sxs-lookup"><span data-stu-id="23df2-114">Invalid AS2-To name configured for Party: {0}   Value: {1}</span></span>               |
  
## <a name="explanation"></a><span data-ttu-id="23df2-115">說明</span><span class="sxs-lookup"><span data-stu-id="23df2-115">Explanation</span></span>  
 <span data-ttu-id="23df2-116">這個錯誤/警告/資訊事件表示，AS2 編碼器或解碼器無法處理 AS2 訊息因為值的 AS2-To 標頭設定的已識別的合作對象不符合 AS2 RFC 4130 中的規格。</span><span class="sxs-lookup"><span data-stu-id="23df2-116">This Error/Warning/Information event indicates that the AS2 encoder or decoder could not process the AS2 message because the value of the AS2-To header configured for the identified party did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="23df2-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="23df2-117">User Action</span></span>  
 <span data-ttu-id="23df2-118">若要解決這個錯誤，請確定 AS2-To 標頭設定為合作對象符合 AS2 RFC 4130 第 6.2 節的規格。</span><span class="sxs-lookup"><span data-stu-id="23df2-118">To resolve this error, make sure that the AS2-To header configured for the party conforms to the specifications in section 6.2 of AS2 RFC 4130.</span></span>