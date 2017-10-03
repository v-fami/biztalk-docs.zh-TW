---
title: "OrchestrationEventStream |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7c63610-6344-4b71-8d65-3add7883bc79
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1fd0dc229c38b3a060c75a9c584259175d72fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="orchestrationeventstream"></a><span data-ttu-id="2e6b0-102">OrchestrationEventStream</span><span class="sxs-lookup"><span data-stu-id="2e6b0-102">OrchestrationEventStream</span></span>
<span data-ttu-id="2e6b0-103">如果您的應用程式是在安裝 BizTalk Server 的電腦上執行，而且您要追蹤屬於 BizTalk 協調流程一部分的項目，請使用 OrchestrationEventStream (OES) API。</span><span class="sxs-lookup"><span data-stu-id="2e6b0-103">You use the OrchestrationEventStream (OES) API when your application runs on a computer on which BizTalk Server is installed and you are tracking items that are part of BizTalk orchestration transactions.</span></span>  
  
 <span data-ttu-id="2e6b0-104">OES API 會先將追蹤資料儲存在 BizTalk MessageBox 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="2e6b0-104">The OES API stores tracking data first in the BizTalk MessageBox database.</span></span> <span data-ttu-id="2e6b0-105">然後再由 Tracking Data Decode Service (TDDS) 定期處理資料，並將資料保存到 BAM 主要匯入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="2e6b0-105">Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).</span></span>  
  
 <span data-ttu-id="2e6b0-106">OES API 位於 Microsoft.BizTalk.Bam.EventObservation 命名空間。</span><span class="sxs-lookup"><span data-stu-id="2e6b0-106">The OES API is found in the Microsoft.BizTalk.Bam.EventObservation namespace.</span></span> <span data-ttu-id="2e6b0-107">若要使用此 API，您必須將 Microsoft.Biztalk.BAM.Xlangs.dll 新增到您的專案。</span><span class="sxs-lookup"><span data-stu-id="2e6b0-107">To use the API you must add the Microsoft.Biztalk.BAM.Xlangs.dll to your project.</span></span>  
  
## <a name="oes-members"></a><span data-ttu-id="2e6b0-108">OES 成員</span><span class="sxs-lookup"><span data-stu-id="2e6b0-108">OES Members</span></span>  
 <span data-ttu-id="2e6b0-109">OES API 是由 [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) 類別衍生而來。</span><span class="sxs-lookup"><span data-stu-id="2e6b0-109">The OES API is derived from the [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) class.</span></span>  
  
 <span data-ttu-id="2e6b0-110">OES 會實作 EventStream 類別內的所有方法，但在行為上則有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="2e6b0-110">OES implements all of the methods within the EventStream class, but has the  following exception in behaviors:</span></span>  
  
 <span data-ttu-id="2e6b0-111">**公用靜態 void clear （);**</span><span class="sxs-lookup"><span data-stu-id="2e6b0-111">**public static void Clear();**</span></span>  
  
 <span data-ttu-id="2e6b0-112">無作業。</span><span class="sxs-lookup"><span data-stu-id="2e6b0-112">No operation.</span></span>  
  
 <span data-ttu-id="2e6b0-113">**公用靜態 void Flush();**</span><span class="sxs-lookup"><span data-stu-id="2e6b0-113">**public static void Flush();**</span></span>  
  
 <span data-ttu-id="2e6b0-114">無作業。</span><span class="sxs-lookup"><span data-stu-id="2e6b0-114">No operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e6b0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e6b0-115">See Also</span></span>  
 [<span data-ttu-id="2e6b0-116">EventStream 類別</span><span class="sxs-lookup"><span data-stu-id="2e6b0-116">EventStream Classes</span></span>](../core/eventstream-classes.md)