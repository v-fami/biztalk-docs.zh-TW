---
title: BizTalk Adapter for mySAP Business Suite 的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, limitations of
- IDOC, sending an IDOC to an SAP system
ms.assetid: 1ca1e0cf-7ae7-4a8b-8363-e5f3746e8e26
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f289d1f70005e8b4caa0e7c739522cc5590bca58
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973711"
---
# <a name="limitations-of-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="a87e8-102">BizTalk Adapter for mySAP Business Suite 的限制</span><span class="sxs-lookup"><span data-stu-id="a87e8-102">Limitations of BizTalk Adapter for mySAP Business Suite</span></span>

## <a name="limitations-list"></a><span data-ttu-id="a87e8-103">限制清單</span><span class="sxs-lookup"><span data-stu-id="a87e8-103">Limitations list</span></span>
<span data-ttu-id="a87e8-104">下列已知的限制[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a87e8-104">The following are known limitations of the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]:</span></span>  
  
- <span data-ttu-id="a87e8-105">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不是與 Microsoft BizTalk Adapter for mySAP Business Suite，配接器的舊版相容。</span><span class="sxs-lookup"><span data-stu-id="a87e8-105">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is not compatible with Microsoft BizTalk Adapter for mySAP Business Suite, the previous release of the adapter.</span></span> <span data-ttu-id="a87e8-106">這一版的配接器不支援傳送和接收有使用舊版配接器所產生的結構描述的訊息。</span><span class="sxs-lookup"><span data-stu-id="a87e8-106">This release of the adapter does not support sending and receiving messages having schemas generated using the earlier version of the adapter.</span></span>  
  
- <span data-ttu-id="a87e8-107">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援 Rfc 使用複雜的參數類型，包括 ITAB II （階層式） 的資料表類型。</span><span class="sxs-lookup"><span data-stu-id="a87e8-107">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support RFCs with complex parameter types, including ITAB II (hierarchical) table types.</span></span>  
  
- <span data-ttu-id="a87e8-108">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援 Rfc 擁有自訂的 ABAP 型別。</span><span class="sxs-lookup"><span data-stu-id="a87e8-108">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support RFCs having custom ABAP types.</span></span>  
  
- <span data-ttu-id="a87e8-109">因為處理基礎的用戶端程式庫，逾時問題而[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援命令，並連接逾時。</span><span class="sxs-lookup"><span data-stu-id="a87e8-109">Due to issues with timeout handling by the underlying client library, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support command and connection timeout.</span></span>  
  
- <span data-ttu-id="a87e8-110">如果您變更執行 BizTalk Server 主控件之電腦的系統時間，時間不會更新會自動在 BizTalk Server 主控件。</span><span class="sxs-lookup"><span data-stu-id="a87e8-110">If you change the system time of the computer running the BizTalk Server host, the time is not updated automatically in the BizTalk Server host.</span></span> <span data-ttu-id="a87e8-111">這可能會導致不正確的行為，使用 BizTalk Server 接收埠的輸入作業。</span><span class="sxs-lookup"><span data-stu-id="a87e8-111">This could lead to incorrect behavior of the inbound operations that use the receive port of BizTalk Server.</span></span> <span data-ttu-id="a87e8-112">因應措施，您必須重新啟動後已執行它的電腦的系統時間已接收埠，主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="a87e8-112">As a workaround, you must restart the host instance that has a receive port, after you have changed the system time of the computer running it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87e8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a87e8-113">See Also</span></span>  
 [<span data-ttu-id="a87e8-114">了解 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="a87e8-114">Understand BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)