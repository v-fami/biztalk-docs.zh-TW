---
title: 無效的 AS2-若要設定合作對象名稱 |Microsoft 文件
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
ms.openlocfilehash: 9c06adc5a459f7dfd05508312494555fb2651114
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257366"
---
# <a name="invalid-as2-to-name-configured-for-party"></a><span data-ttu-id="5ae28-102">無效的 AS2-若要設定合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="5ae28-102">Invalid AS2-To name configured for Party</span></span>
## <a name="details"></a><span data-ttu-id="5ae28-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5ae28-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5ae28-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5ae28-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5ae28-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="5ae28-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5ae28-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5ae28-106">Event ID</span></span>|-|  
|<span data-ttu-id="5ae28-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="5ae28-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5ae28-108">EDI</span><span class="sxs-lookup"><span data-stu-id="5ae28-108"> EDI</span></span>|  
|<span data-ttu-id="5ae28-109">元件</span><span class="sxs-lookup"><span data-stu-id="5ae28-109">Component</span></span>|<span data-ttu-id="5ae28-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="5ae28-110">AS2 Engine</span></span>|  
|<span data-ttu-id="5ae28-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5ae28-111">Symbolic Name</span></span>|<span data-ttu-id="5ae28-112">InvalidAS2ToNameConfiguredError</span><span class="sxs-lookup"><span data-stu-id="5ae28-112">InvalidAS2ToNameConfiguredError</span></span>|  
|<span data-ttu-id="5ae28-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5ae28-113">Message Text</span></span>|<span data-ttu-id="5ae28-114">無效的 AS2-若要設定合作對象名稱： {0} 值： {1}</span><span class="sxs-lookup"><span data-stu-id="5ae28-114">Invalid AS2-To name configured for Party: {0}   Value: {1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5ae28-115">說明</span><span class="sxs-lookup"><span data-stu-id="5ae28-115">Explanation</span></span>  
 <span data-ttu-id="5ae28-116">這個錯誤/警告/資訊事件表示，AS2 編碼器或解碼器無法處理 AS2 訊息因為值的 AS2-To 標頭已設定為識別合作對象不符合 AS2 RFC 4130 中的規格。</span><span class="sxs-lookup"><span data-stu-id="5ae28-116">This Error/Warning/Information event indicates that the AS2 encoder or decoder could not process the AS2 message because the value of the AS2-To header configured for the identified party did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5ae28-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5ae28-117">User Action</span></span>  
 <span data-ttu-id="5ae28-118">若要解決這個錯誤，請確定 AS2-To 標頭已設定為合作對象符合 AS2 RFC 4130 第 6.2 節的規格。</span><span class="sxs-lookup"><span data-stu-id="5ae28-118">To resolve this error, make sure that the AS2-To header configured for the party conforms to the specifications in section 6.2 of AS2 RFC 4130.</span></span>