---
title: 瀏覽、 搜尋，並取得中繼資料中 SAP 的 tRFC 作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tRFC operations
- tRFC operations, browsing
- searching, tRFC operations
- tRFC operations, searching
- browsing, tRFC operations
ms.assetid: cf4a16d1-7bbf-4dea-b54d-b5315fbcd552
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5124eb4b3a56df70ec55d157ee80a394d6bff83d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217166"
---
# <a name="browse-search-and-get-metadata-for-trfc-operations-in-sap"></a><span data-ttu-id="50e21-102">瀏覽、 搜尋和 tRFC 作業 SAP 中取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="50e21-102">Browse, search, and get metadata for tRFC operations in SAP</span></span>
<span data-ttu-id="50e21-103">tRFCs 並不是個別成品的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="50e21-103">tRFCs are not a separate artifact in an SAP system.</span></span> <span data-ttu-id="50e21-104">這些分類的不同節點所下[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]因為它們的中繼資料的特性是不同的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="50e21-104">These are categorized under a separate node by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] because their metadata characteristics are different from that of RFCs.</span></span> <span data-ttu-id="50e21-105">不過，瀏覽的經驗，搜尋和擷取中繼資料 tRFCs 是相同的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="50e21-105">However, the experience of browsing, searching, and retrieving metadata for tRFCs is identical to that of the RFCs.</span></span> <span data-ttu-id="50e21-106">請參閱[瀏覽、 搜尋和 sap RFC 作業的 get 中繼資料](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)有關使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]瀏覽，搜尋，然後從 SAP 系統擷取 tRFCs 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="50e21-106">Refer to [Browse, search, and get metadata for RFC operations in SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md) for information about using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to browse, search, and retrieve metadata for tRFCs from an SAP system.</span></span>  
  
 <span data-ttu-id="50e21-107">請注意，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現特殊作業**RfcConfirmTransID**下**TRFC**節點。</span><span class="sxs-lookup"><span data-stu-id="50e21-107">Note that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a special operation **RfcConfirmTransID** under the **TRFC** node.</span></span> <span data-ttu-id="50e21-108">SAP 配接器會認可對 SAP 伺服器的 tRFC 呼叫使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="50e21-108">The SAP adapter uses this operation to commit tRFC calls made to the SAP server.</span></span> <span data-ttu-id="50e21-109">如需有關這項作業的詳細資訊，請參閱[tRFCs SAP 中的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="50e21-109">For more information about this operation, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e21-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50e21-110">See Also</span></span>  
 [<span data-ttu-id="50e21-111">取得 Visual Studio 中的 SAP 作業的中繼資料</span><span class="sxs-lookup"><span data-stu-id="50e21-111">Get Metadata for SAP Operations in Visual Studio</span></span>](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)