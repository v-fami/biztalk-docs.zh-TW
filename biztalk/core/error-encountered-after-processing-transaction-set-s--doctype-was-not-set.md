---
title: 在處理交易 Set(s) 因為沒有設定文件類型之後所發生的錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a323658c-77d8-4059-aa15-d88c08e5450d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 874b0229eecdd5fe9c046f69789c4708b9280031
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240262"
---
# <a name="error-encountered-after-processing-transaction-sets-because-doctype-was-not-set"></a><span data-ttu-id="33998-102">在處理交易 Set(s) 因為沒有設定文件類型之後所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="33998-102">Error encountered after processing Transaction Set(s) because DocType was not set</span></span>
## <a name="details"></a><span data-ttu-id="33998-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="33998-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="33998-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="33998-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="33998-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="33998-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="33998-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="33998-106">Event ID</span></span>|-|  
|<span data-ttu-id="33998-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="33998-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="33998-108">EDI</span><span class="sxs-lookup"><span data-stu-id="33998-108"> EDI</span></span>|  
|<span data-ttu-id="33998-109">元件</span><span class="sxs-lookup"><span data-stu-id="33998-109">Component</span></span>|<span data-ttu-id="33998-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="33998-110">EDI Engine</span></span>|  
|<span data-ttu-id="33998-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="33998-111">Symbolic Name</span></span>|<span data-ttu-id="33998-112">DocTypeNotSet</span><span class="sxs-lookup"><span data-stu-id="33998-112">DocTypeNotSet</span></span>|  
|<span data-ttu-id="33998-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="33998-113">Message Text</span></span>|<span data-ttu-id="33998-114">在處理 {0} 交易 Set(s) 之後發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="33998-114">Error encountered after processing {0} Transaction Set(s).</span></span> <span data-ttu-id="33998-115">未設定文件類型</span><span class="sxs-lookup"><span data-stu-id="33998-115">DocType was not set</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="33998-116">說明</span><span class="sxs-lookup"><span data-stu-id="33998-116">Explanation</span></span>  
 <span data-ttu-id="33998-117">這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交易設定，因為 ST01 (對於 X12 交換) 或 UNH2.1 （適用於 EDIFACT 交換） 未設定為交易集。</span><span class="sxs-lookup"><span data-stu-id="33998-117">This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming transaction set because ST01 (for an X12 interchange) or UNH2.1 (for an EDIFACT interchange) was not set for the transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="33998-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="33998-118">User Action</span></span>  
 <span data-ttu-id="33998-119">若要解決這個錯誤，確認的交易集發生錯誤的 ST01 或 UNH1 區段設定為有效的文件類型。</span><span class="sxs-lookup"><span data-stu-id="33998-119">To resolve this error, verify that the ST01 or UNH1 segment for the transaction set in error is set to a valid document type.</span></span>