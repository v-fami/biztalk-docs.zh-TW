---
title: 特殊作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, special operations surfaced by the SAP adapter
ms.assetid: 8725fe63-6ff4-49c8-b386-d4c67e2be440
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bada45064e588748b25947e08b104dc79838ee0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975983"
---
# <a name="special-operations"></a><span data-ttu-id="29f3c-102">特殊作業</span><span class="sxs-lookup"><span data-stu-id="29f3c-102">Special Operations</span></span>
<span data-ttu-id="29f3c-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會呈現數個特殊的作業。</span><span class="sxs-lookup"><span data-stu-id="29f3c-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces several special operations.</span></span> <span data-ttu-id="29f3c-104">這些作業不根據 SAP 系統的成品。</span><span class="sxs-lookup"><span data-stu-id="29f3c-104">These operations are not based on SAP system artifacts.</span></span> <span data-ttu-id="29f3c-105">它們會顯示為配接器用戶端應用程式提供功能。</span><span class="sxs-lookup"><span data-stu-id="29f3c-105">They are surfaced to provide functionality for adapter client applications.</span></span> <span data-ttu-id="29f3c-106">特殊的作業為：</span><span class="sxs-lookup"><span data-stu-id="29f3c-106">The special operations are:</span></span>  
  
- <span data-ttu-id="29f3c-107">**RfcGetAttributes**。</span><span class="sxs-lookup"><span data-stu-id="29f3c-107">**RfcGetAttributes**.</span></span> <span data-ttu-id="29f3c-108">此作業的 RFC 節點下的呈現，並公開 （expose） 的 RFC sdk 的功能。</span><span class="sxs-lookup"><span data-stu-id="29f3c-108">This operation is surfaced under the RFC node and exposes functionality of the RFC SDK.</span></span> <span data-ttu-id="29f3c-109">它提供下列 RFC 連線的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="29f3c-109">It provides the following information about the RFC connection:</span></span>  
  
  - <span data-ttu-id="29f3c-110">系統識別碼</span><span class="sxs-lookup"><span data-stu-id="29f3c-110">The system ID</span></span>  
  
  - <span data-ttu-id="29f3c-111">協力廠商程式碼頁面</span><span class="sxs-lookup"><span data-stu-id="29f3c-111">The partner code page</span></span>  
  
  - <span data-ttu-id="29f3c-112">語言</span><span class="sxs-lookup"><span data-stu-id="29f3c-112">The language</span></span>  
  
    <span data-ttu-id="29f3c-113">如需有關 RfcGetAttributes 作業，包括它的訊息結構描述的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="29f3c-113">For more information about the RfcGetAttributes operation including its message schema, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span></span>  
  
- <span data-ttu-id="29f3c-114">**RfcConfirmTransID**。</span><span class="sxs-lookup"><span data-stu-id="29f3c-114">**RfcConfirmTransID**.</span></span> <span data-ttu-id="29f3c-115">這項作業的 TRFC 節點下的呈現，並公開 RFC SDK 功能。</span><span class="sxs-lookup"><span data-stu-id="29f3c-115">This operation is surfaced under the TRFC node and exposes RFC SDK functionality.</span></span> <span data-ttu-id="29f3c-116">您可以使用這項作業來確認 SAP 系統上的 SAP 交易識別碼。</span><span class="sxs-lookup"><span data-stu-id="29f3c-116">You use this operation to confirm SAP transaction IDs on the SAP system.</span></span>  
  
   <span data-ttu-id="29f3c-117">如需有關如何使用 RfcConfirmTransID 作業和其訊息結構描述，請參閱[對 sap 的 Trfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="29f3c-117">For more information about how to use the RfcConfirmTransID operation and about its message schema, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span>  
  
- <span data-ttu-id="29f3c-118">**字串 SapAdapterUtilities.ConvertGuidToTid(Guid)**。</span><span class="sxs-lookup"><span data-stu-id="29f3c-118">**string SapAdapterUtilities.ConvertGuidToTid(Guid)**.</span></span> <span data-ttu-id="29f3c-119">這是 SAP 配接器組件所公開的公用方法。</span><span class="sxs-lookup"><span data-stu-id="29f3c-119">This is a public method exposed by the SAP adapter assembly.</span></span> <span data-ttu-id="29f3c-120">（不是由配接器顯示的作業。）它會傳回 SAP 交易識別碼 (TID) 對應至指定的 GUID。</span><span class="sxs-lookup"><span data-stu-id="29f3c-120">(It is not an operation surfaced by the adapter.) It returns the SAP transaction ID (TID) mapped to the specified GUID.</span></span>  
  
   <span data-ttu-id="29f3c-121">就內部而言，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]對應至 GUID 的 SAP 系統上的 SAP 交易識別碼 (TID) 識別的工作 (LUW) 邏輯單元。</span><span class="sxs-lookup"><span data-stu-id="29f3c-121">Internally, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] maps the SAP transaction ID (TID) that identifies a logical unit of work (LUW) on the SAP system to a GUID.</span></span> <span data-ttu-id="29f3c-122">此 GUID 會公開給配接器用戶端，以便它們可以認可 tRFC (LUW) 叫用 RfcConfirmTransID 作業，以確認其上的 SAP 系統的 TID。</span><span class="sxs-lookup"><span data-stu-id="29f3c-122">This GUID is exposed to adapter clients, so that they can commit a tRFC (LUW) by invoking the RfcConfirmTransID operation to confirm its TID on the SAP system.</span></span>  
  
   <span data-ttu-id="29f3c-123">不過，某些情況下，您可能需要與 tRFC 相關聯的 TID。</span><span class="sxs-lookup"><span data-stu-id="29f3c-123">However, for some scenarios, you may need the TID that is associated with a tRFC.</span></span> <span data-ttu-id="29f3c-124">例如，您可能想要識別 LUW 上 SAP 系統來疑難排解問題。</span><span class="sxs-lookup"><span data-stu-id="29f3c-124">For example, you may want to identify the LUW on the SAP system to troubleshoot an issue.</span></span> <span data-ttu-id="29f3c-125">針對這些案例，您可以呼叫**ConvertGuidToTid**。</span><span class="sxs-lookup"><span data-stu-id="29f3c-125">For these scenarios you can call **ConvertGuidToTid**.</span></span> <span data-ttu-id="29f3c-126">若要使用**ConvertGuidToTid**在您的程式碼中，您必須加入 SAP 配接器組件的參考至您的專案。</span><span class="sxs-lookup"><span data-stu-id="29f3c-126">To use **ConvertGuidToTid** in your code, you must add a reference to the SAP adapter assembly to your project.</span></span>  
  
   <span data-ttu-id="29f3c-127">如需有關如何叫用 Trfc 的詳細資訊，請參閱[對 sap 的 Trfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="29f3c-127">For more information about invoking tRFCs, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span> <span data-ttu-id="29f3c-128">下列範例示範如何叫用**ConvertGuidToTid**。</span><span class="sxs-lookup"><span data-stu-id="29f3c-128">The following example shows how to invoke **ConvertGuidToTid**.</span></span>  
  
  ```  
  // messageGuid is the GUID associated with a tRFC or IDOC  
  
  string tid = SapAdapterUtilities.ConvertGuidToTid(messageGuid);  
  ```  
  
## <a name="see-also"></a><span data-ttu-id="29f3c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29f3c-129">See Also</span></span>  
 [<span data-ttu-id="29f3c-130">訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="29f3c-130">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)