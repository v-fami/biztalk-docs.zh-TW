---
title: 不支援，因為 UNB1.1 中的編碼資訊不符合實際的編碼字元集 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 085ea8e3-e0d8-45bd-9985-6787b00e4d5a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41a6eafbb0e71de5f13e792361cdc0d1fc338088
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239902"
---
# <a name="character-set-not-supported-because-the-encoding-information-in-unb11-does-not-match-the-actual-encoding"></a><span data-ttu-id="fe033-102">因為 UNB1.1 中的編碼資訊不符合交換的實際編碼，不支援字元集</span><span class="sxs-lookup"><span data-stu-id="fe033-102">Character set not supported because the encoding information in UNB1.1 does not match the actual encoding</span></span>
## <a name="details"></a><span data-ttu-id="fe033-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fe033-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe033-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fe033-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="fe033-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="fe033-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="fe033-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fe033-106">Event ID</span></span>|-|  
|<span data-ttu-id="fe033-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="fe033-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="fe033-108">EDI</span><span class="sxs-lookup"><span data-stu-id="fe033-108"> EDI</span></span>|  
|<span data-ttu-id="fe033-109">元件</span><span class="sxs-lookup"><span data-stu-id="fe033-109">Component</span></span>|<span data-ttu-id="fe033-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="fe033-110">EDI Engine</span></span>|  
|<span data-ttu-id="fe033-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fe033-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="fe033-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fe033-112">Message Text</span></span>|<span data-ttu-id="fe033-113">不支援字元集。</span><span class="sxs-lookup"><span data-stu-id="fe033-113">Character set not supported.</span></span> <span data-ttu-id="fe033-114">這可能是因為 UNB1.1 中的編碼資訊不符合交換的實際編碼。</span><span class="sxs-lookup"><span data-stu-id="fe033-114">It could be due to the fact that encoding information in UNB1.1 does not match the actual encoding of the interchange.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fe033-115">說明</span><span class="sxs-lookup"><span data-stu-id="fe033-115">Explanation</span></span>  
 <span data-ttu-id="fe033-116">這個錯誤/警告/資訊事件表示，由於在內送 EDIFACT 交換中使用的字元和在交換之 [UNB1.1] 欄位中識別的字元集不符，因此 EDI 接收管線無法處理該交換。</span><span class="sxs-lookup"><span data-stu-id="fe033-116">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming EDIFACT interchange because the characters used in the interchange did not conform to the character set identified in field UNB1.1 of the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fe033-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fe033-117">User Action</span></span>  
 <span data-ttu-id="fe033-118">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="fe033-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="fe033-119">變更讓它們符合指定的字元集中欄位 UNB1.1 交換的交換中使用的字元。</span><span class="sxs-lookup"><span data-stu-id="fe033-119">Change the characters used in the interchange so they conform to the character set specified in field UNB1.1 of the interchange.</span></span>  
  
-   <span data-ttu-id="fe033-120">變更指定的字元集中的交換，UNB1.1 欄位以便交換中的所有字元都是組件的字元集。</span><span class="sxs-lookup"><span data-stu-id="fe033-120">Change the character set specified in field UNB1.1 of the interchange, so all characters in the interchange are part of the character set.</span></span>