---
title: "疑難排解批次處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, troubleshooting
- troubleshooting, batching
ms.assetid: f47e1a16-47fd-4bd8-8dad-fcdba31a833e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94c8413a8022529e6ace56c50d5e6d75267a72e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-batching"></a><span data-ttu-id="f22ec-102">疑難排解批次處理</span><span class="sxs-lookup"><span data-stu-id="f22ec-102">Troubleshooting Batching</span></span>
<span data-ttu-id="f22ec-103">解決相關問題[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]批次處理。</span><span class="sxs-lookup"><span data-stu-id="f22ec-103">Addresses issues related to [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] batching.</span></span>  
  
## <a name="error-activating-batch"></a><span data-ttu-id="f22ec-104">啟動批次錯誤</span><span class="sxs-lookup"><span data-stu-id="f22ec-104">Error activating batch</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="f22ec-105">徵兆</span><span class="sxs-lookup"><span data-stu-id="f22ec-105">Symptom</span></span>  
 <span data-ttu-id="f22ec-106">無法啟動批次。</span><span class="sxs-lookup"><span data-stu-id="f22ec-106">Unable to activate a batch.</span></span> <span data-ttu-id="f22ec-107">您收到一般網路錯誤。</span><span class="sxs-lookup"><span data-stu-id="f22ec-107">You get a general network error.</span></span>  
  
<span data-ttu-id="f22ec-108">**可能的原因**:[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]已重新啟動，但[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管不是。</span><span class="sxs-lookup"><span data-stu-id="f22ec-108">**Possible Cause** : [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] was restarted, but [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer was not.</span></span>  
  
<span data-ttu-id="f22ec-109">**解析**： 重新啟動[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。</span><span class="sxs-lookup"><span data-stu-id="f22ec-109">**Resolution** : Restart [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="messages-are-not-batched-when-the-target-namespace-is-not-the-default"></a><span data-ttu-id="f22ec-110">目標命名空間不是預設值時，不會批次處理的訊息</span><span class="sxs-lookup"><span data-stu-id="f22ec-110">Messages are not batched when the target namespace is not the default</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="f22ec-111">徵兆</span><span class="sxs-lookup"><span data-stu-id="f22ec-111">Symptom</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f22ec-112">未批次處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="f22ec-112"> is not batching messages.</span></span>  
  
<span data-ttu-id="f22ec-113">**可能的原因**： 來源和目的合作對象不在相同的結構描述命名空間中。</span><span class="sxs-lookup"><span data-stu-id="f22ec-113">**Possible Cause** : Source and destination parties are not in the same schema namespace.</span></span>  
  
<span data-ttu-id="f22ec-114">**解析**： 來源和目的合作對象必須使用相同的結構描述命名空間，若需要驗證。</span><span class="sxs-lookup"><span data-stu-id="f22ec-114">**Resolution** : Source and destination parties must use the same schema namespace if validation is required.</span></span> <span data-ttu-id="f22ec-115">確認來源和目的合作對象都使用相同的結構描述命名空間。</span><span class="sxs-lookup"><span data-stu-id="f22ec-115">Ensure the source and destination parties are using the same schema namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f22ec-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f22ec-116">See Also</span></span>  
 [<span data-ttu-id="f22ec-117">HL7 中的疑難排解和已知問題</span><span class="sxs-lookup"><span data-stu-id="f22ec-117">Troubleshooting and known issues in HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)