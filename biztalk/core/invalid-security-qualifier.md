---
title: "無效的安全性辨識符號 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dce36f4b-ab59-41c0-8b92-3020f6393db9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f4d16b4295bd8d01f93db964d4e45e8363205ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-security-qualifier"></a><span data-ttu-id="aec20-102">無效的安全性辨識符號</span><span class="sxs-lookup"><span data-stu-id="aec20-102">Invalid Security Qualifier</span></span>
## <a name="details"></a><span data-ttu-id="aec20-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aec20-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aec20-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aec20-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="aec20-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="aec20-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="aec20-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aec20-106">Event ID</span></span>|-|  
|<span data-ttu-id="aec20-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="aec20-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="aec20-108">EDI</span><span class="sxs-lookup"><span data-stu-id="aec20-108"> EDI</span></span>|  
|<span data-ttu-id="aec20-109">元件</span><span class="sxs-lookup"><span data-stu-id="aec20-109">Component</span></span>|<span data-ttu-id="aec20-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="aec20-110">EDI Engine</span></span>|  
|<span data-ttu-id="aec20-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aec20-111">Symbolic Name</span></span>|<span data-ttu-id="aec20-112">X12Ta1InvalidSecurityQualifierDescription</span><span class="sxs-lookup"><span data-stu-id="aec20-112">X12Ta1InvalidSecurityQualifierDescription</span></span>|  
|<span data-ttu-id="aec20-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aec20-113">Message Text</span></span>|<span data-ttu-id="aec20-114">無效的安全性辨識符號</span><span class="sxs-lookup"><span data-stu-id="aec20-114">Invalid Security Qualifier</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aec20-115">說明</span><span class="sxs-lookup"><span data-stu-id="aec20-115">Explanation</span></span>  
 <span data-ttu-id="aec20-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為安全性辨識符號中 ISA03 欄位或 [UNB6.2] 欄位中的收件者參考密碼辨識符號不符合中的值列舉服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立。</span><span class="sxs-lookup"><span data-stu-id="aec20-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Security Qualifier in the ISA03 field or the Recipient Reference Password Qualifier in the UNB6.2 field did not match a value in the enumeration established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aec20-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aec20-117">User Action</span></span>  
 <span data-ttu-id="aec20-118">若要解決這個錯誤，請確定 ISA03 欄位或 [UNB6.2] 欄位符合其中一個服務結構描述所建立的列舉值。</span><span class="sxs-lookup"><span data-stu-id="aec20-118">To resolve this error, make sure that the ISA03 field or the UNB6.2 field matches one of the values in the enumeration established by the service schema.</span></span> <span data-ttu-id="aec20-119">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="aec20-119">Have the interchange resent.</span></span>