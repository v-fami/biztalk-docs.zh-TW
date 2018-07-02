---
title: 開始使用 BizTalk Adapter for mySAP Business Suite |Microsoft Docs
description: 安裝自訂 Rfc、 了解配接器、 完成上逐步教學課程，以使用 mySAP 配接器的 BizTalk 配接器組件 (BAP) 中執行 SAP RFC 和 IDOC 工作
ms.custom: ''
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2013253-f911-4e35-a33a-b4a9bcb136aa
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02112b6974a537c9f66cc301014ae16bb4bf326f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967465"
---
# <a name="get-started-with-the-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="18257-103">開始使用 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="18257-103">Get started with the BizTalk Adapter for mySAP Business Suite</span></span>
<span data-ttu-id="18257-104">本節的是 Microsoft 的新手的使用者提供的配接器、 必要條件和主題概觀[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="18257-104">This section provides an overview of the adapter, prerequisites, and topics for users who are new to Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="18257-105">它討論的功能[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]以及可對使用配接器的 SAP 系統的不同作業。</span><span class="sxs-lookup"><span data-stu-id="18257-105">It discusses the features of [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] and the different operations that can be performed on the SAP system using the adapter.</span></span>  

## <a name="what-is-an-adapter"></a><span data-ttu-id="18257-106">何謂配接器？</span><span class="sxs-lookup"><span data-stu-id="18257-106">What is an adapter?</span></span> 
<span data-ttu-id="18257-107">配接器是一種軟體元件，可讓您傳送和接收訊息的營運 (LOB) 系統。</span><span class="sxs-lookup"><span data-stu-id="18257-107">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="18257-108">配接器的主要設計目的是協助交易夥伴之間的商務文件的交換。</span><span class="sxs-lookup"><span data-stu-id="18257-108">The primary design goal of adapters is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="18257-109">由於每個商務系統可能會遵守特定的文件格式和通訊協定，配接器必須使用傳遞機制符合普遍認可的標準和通訊協定，來為使用者提供統一的介面。</span><span class="sxs-lookup"><span data-stu-id="18257-109">Because each business system may adhere to specific document formats and protocols, the adapter must use a delivery mechanism that conforms to commonly recognized standards and protocols to provide a uniform interface to the users.</span></span>  
  
 <span data-ttu-id="18257-110">配接器可以分成兩大類：</span><span class="sxs-lookup"><span data-stu-id="18257-110">The adapters can be divided into two broad categories:</span></span>  
  
- <span data-ttu-id="18257-111">**LOB 配接器**。</span><span class="sxs-lookup"><span data-stu-id="18257-111">**LOB adapters**.</span></span> <span data-ttu-id="18257-112">這類配接器提供服務導向程式設計模型，以存取 LOB 系統，例如 SAP 或 Siebel 配接器。</span><span class="sxs-lookup"><span data-stu-id="18257-112">Such adapters provide service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel.</span></span>  
  
- <span data-ttu-id="18257-113">**資料配接器**。</span><span class="sxs-lookup"><span data-stu-id="18257-113">**Data adapters**.</span></span> <span data-ttu-id="18257-114">這類配接器提供服務導向程式設計模型，以存取資料庫 — 比方說，針對 SQL Server 的 Oracle 資料庫配接器。</span><span class="sxs-lookup"><span data-stu-id="18257-114">Such adapters provide service-oriented programming model to access databases—for example, an adapter for the Oracle database or SQL Server.</span></span>  
  
  <span data-ttu-id="18257-115">有五個配接器在[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="18257-115">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
- [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="18257-116"> ( [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="18257-116"> (the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span></span>  
  
- [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="18257-117"> ( [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="18257-117"> (the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span></span>  
  
- [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="18257-118"> ( [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="18257-118"> (the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span></span>  
  
- [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="18257-119"> ( [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)])，包括[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="18257-119"> (the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]), including [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span></span>  
  
- [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="18257-120"> ( [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)])，包括[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="18257-120"> (the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]), including [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="18257-121">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不適用於 64 位元平台。</span><span class="sxs-lookup"><span data-stu-id="18257-121">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
  <span data-ttu-id="18257-122">如果您沒有已經知道您要使用的方式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在您的公司，建議您開始探索功能，以及配接器功能中所述[了解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="18257-122">If you do not already know how you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] at your company, it is recommended that you start by exploring features and functionality of the adapter described in [Understand BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="18257-123">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="18257-123">Next steps</span></span>  
- [<span data-ttu-id="18257-124">安裝 Data Provider for SAP 的自訂 RFC</span><span class="sxs-lookup"><span data-stu-id="18257-124">Install Custom RFCs for the Data Provider for SAP</span></span>](install-custom-rfcs-for-the-data-provider-for-sap.md)
  
-   [<span data-ttu-id="18257-125">了解 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="18257-125">Understand BizTalk Adapter for mySAP Business Suite</span></span>](understand-biztalk-adapter-for-mysap-business-suite.md)  

- [<span data-ttu-id="18257-126">在 SAP 上完成 RFC 和 IDOC 工作</span><span class="sxs-lookup"><span data-stu-id="18257-126">Complete RFC and IDOC tasks on SAP</span></span>](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)
  
-   [<span data-ttu-id="18257-127">SAP 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="18257-127">SAP Adapter Tutorials</span></span>](sap-adapter-tutorials.md)  