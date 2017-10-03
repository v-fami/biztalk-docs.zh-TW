---
title: "限制 BizTalk adapter for mySAP Business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, limitations of
- IDOC, sending an IDOC to an SAP system
ms.assetid: 1ca1e0cf-7ae7-4a8b-8363-e5f3746e8e26
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d392178cd49918151f0ad86c73a5fcba712d6b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="03db3-102">BizTalk adapter for mySAP Business Suite 的限制</span><span class="sxs-lookup"><span data-stu-id="03db3-102">Limitations of BizTalk Adapter for mySAP Business Suite</span></span>

## <a name="limitations-list"></a><span data-ttu-id="03db3-103">限制清單</span><span class="sxs-lookup"><span data-stu-id="03db3-103">Limitations list</span></span>
<span data-ttu-id="03db3-104">下列已知的限制[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="03db3-104">The following are known limitations of the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]:</span></span>  
  
-   <span data-ttu-id="03db3-105">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不是與 Microsoft BizTalk Adapter for mySAP Business Suite，配接器之前的版本相容。</span><span class="sxs-lookup"><span data-stu-id="03db3-105">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is not compatible with Microsoft BizTalk Adapter for mySAP Business Suite, the previous release of the adapter.</span></span> <span data-ttu-id="03db3-106">這一版的配接器不支援傳送和接收訊息，需要使用舊版的配接器所產生的結構描述。</span><span class="sxs-lookup"><span data-stu-id="03db3-106">This release of the adapter does not support sending and receiving messages having schemas generated using the earlier version of the adapter.</span></span>  
  
-   <span data-ttu-id="03db3-107">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援具有複雜的參數類型，包括 ITAB II （階層式） 的資料表類型的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="03db3-107">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support RFCs with complex parameter types, including ITAB II (hierarchical) table types.</span></span>  
  
-   <span data-ttu-id="03db3-108">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援具有自訂 ABAP 類型的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="03db3-108">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support RFCs having custom ABAP types.</span></span>  
  
-   <span data-ttu-id="03db3-109">由於處理基礎的用戶端程式庫，逾時問題[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援命令，並連接逾時。</span><span class="sxs-lookup"><span data-stu-id="03db3-109">Due to issues with timeout handling by the underlying client library, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support command and connection timeout.</span></span>  
  
-   <span data-ttu-id="03db3-110">如果您變更執行 BizTalk Server 主控件之電腦的系統時間，時間是不會自動更新 BizTalk Server 主控件中。</span><span class="sxs-lookup"><span data-stu-id="03db3-110">If you change the system time of the computer running the BizTalk Server host, the time is not updated automatically in the BizTalk Server host.</span></span> <span data-ttu-id="03db3-111">這可能會導致不正確的行為，使用 BizTalk Server 接收埠的輸入作業。</span><span class="sxs-lookup"><span data-stu-id="03db3-111">This could lead to incorrect behavior of the inbound operations that use the receive port of BizTalk Server.</span></span> <span data-ttu-id="03db3-112">因應措施，您必須重新啟動後已變更其執行之電腦的系統時間有接收埠，主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="03db3-112">As a workaround, you must restart the host instance that has a receive port, after you have changed the system time of the computer running it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03db3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03db3-113">See Also</span></span>  
 [<span data-ttu-id="03db3-114">瞭解 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="03db3-114">Understand BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)