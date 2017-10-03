---
title: "欄位的分隔符號，區段標記識別項後找不到 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f6f0a74-3560-4d6d-9893-85e8426e6b17
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 818a061cd723c0d8f8c58570c9e6df94a670942b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="field-separator-not-found-after-segment-tag-id"></a><span data-ttu-id="d1d56-102">欄位的分隔符號，區段標記識別項後找不到</span><span class="sxs-lookup"><span data-stu-id="d1d56-102">Field separator not found after segment tag id</span></span>
## <a name="details"></a><span data-ttu-id="d1d56-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d1d56-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1d56-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d1d56-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d1d56-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d1d56-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d1d56-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d1d56-106">Event ID</span></span>|-|  
|<span data-ttu-id="d1d56-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d1d56-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d1d56-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d1d56-108"> EDI</span></span>|  
|<span data-ttu-id="d1d56-109">元件</span><span class="sxs-lookup"><span data-stu-id="d1d56-109">Component</span></span>|<span data-ttu-id="d1d56-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d1d56-110">EDI Engine</span></span>|  
|<span data-ttu-id="d1d56-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d1d56-111">Symbolic Name</span></span>|<span data-ttu-id="d1d56-112">X12SeFsNotFoundAfterTagIdDescription</span><span class="sxs-lookup"><span data-stu-id="d1d56-112">X12SeFsNotFoundAfterTagIdDescription</span></span>|  
|<span data-ttu-id="d1d56-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d1d56-113">Message Text</span></span>|<span data-ttu-id="d1d56-114">欄位的分隔符號，區段標記識別項後找不到</span><span class="sxs-lookup"><span data-stu-id="d1d56-114">Field separator not found after segment tag id</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d1d56-115">說明</span><span class="sxs-lookup"><span data-stu-id="d1d56-115">Explanation</span></span>  
 <span data-ttu-id="d1d56-116">這個錯誤/警告/資訊事件表示，接收管線無法處理交換，因為交換所包含的區段時，它後面的資料元素分隔符號不具有區段識別項。</span><span class="sxs-lookup"><span data-stu-id="d1d56-116">This Error/Warning/Information event indicates that the receive pipeline could not process the interchange because the interchange contained a segment that had a segment identifier without a data element separator immediately following it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d1d56-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d1d56-117">User Action</span></span>  
 <span data-ttu-id="d1d56-118">若要解決這個錯誤，確定交換中的所有區段識別項有資料元素分隔符號緊接，則需要重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="d1d56-118">To resolve this error, ensure that all segment identifiers in the interchange have data element separators immediately following them, and then have the interchange resent.</span></span>