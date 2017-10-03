---
title: "開始使用 BizTalk Adapter for mySAP Business Suite |Microsoft 文件"
description: "安裝自訂 Rfc、 了解配接器、 完成上逐步教學課程，可使用 mySAP 配接器的 BizTalk 配接器組件 (BAP) 中執行 SAP RFC 和 IDOC 工作"
ms.custom: 
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2013253-f911-4e35-a33a-b4a9bcb136aa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e5607a255f50bf5295d4ea22c9a680d86f38e5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="638d9-103">開始使用 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="638d9-103">Get started with the BizTalk Adapter for mySAP Business Suite</span></span>
<span data-ttu-id="638d9-104">本節提供使用者熟悉 Microsoft 配接器、 必要條件和主題的總覽[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="638d9-104">This section provides an overview of the adapter, prerequisites, and topics for users who are new to Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="638d9-105">其中也會討論的功能[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]以及可對使用配接器的 SAP 系統的不同作業。</span><span class="sxs-lookup"><span data-stu-id="638d9-105">It discusses the features of [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] and the different operations that can be performed on the SAP system using the adapter.</span></span>  

## <a name="what-is-an-adapter"></a><span data-ttu-id="638d9-106">什麼是配接器？</span><span class="sxs-lookup"><span data-stu-id="638d9-106">What is an adapter?</span></span> 
<span data-ttu-id="638d9-107">配接器是可讓您傳送和接收訊息的特定業務 (LOB) 系統的軟體元件。</span><span class="sxs-lookup"><span data-stu-id="638d9-107">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="638d9-108">配接器的主要設計目的是協助交易夥伴之間的商務文件的交換。</span><span class="sxs-lookup"><span data-stu-id="638d9-108">The primary design goal of adapters is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="638d9-109">因為每個商務系統可能會遵守特定的文件格式和通訊協定，配接器必須使用的傳遞機制符合普遍認可的標準和通訊協定，來為使用者提供統一的介面。</span><span class="sxs-lookup"><span data-stu-id="638d9-109">Because each business system may adhere to specific document formats and protocols, the adapter must use a delivery mechanism that conforms to commonly recognized standards and protocols to provide a uniform interface to the users.</span></span>  
  
 <span data-ttu-id="638d9-110">配接器可以分成兩大類別：</span><span class="sxs-lookup"><span data-stu-id="638d9-110">The adapters can be divided into two broad categories:</span></span>  
  
-   <span data-ttu-id="638d9-111">**LOB 配接器**。</span><span class="sxs-lookup"><span data-stu-id="638d9-111">**LOB adapters**.</span></span> <span data-ttu-id="638d9-112">這類配接器提供的服務導向程式設計模型，以存取 LOB 系統，例如 SAP 或 Siebel 配接器。</span><span class="sxs-lookup"><span data-stu-id="638d9-112">Such adapters provide service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel.</span></span>  
  
-   <span data-ttu-id="638d9-113">**資料配接器**。</span><span class="sxs-lookup"><span data-stu-id="638d9-113">**Data adapters**.</span></span> <span data-ttu-id="638d9-114">這類配接器可提供服務導向程式設計模型，access 資料庫 — 比方說，針對 SQL Server 的 Oracle 資料庫配接器。</span><span class="sxs-lookup"><span data-stu-id="638d9-114">Such adapters provide service-oriented programming model to access databases—for example, an adapter for the Oracle database or SQL Server.</span></span>  
  
 <span data-ttu-id="638d9-115">有五個配接器在[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="638d9-115">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="638d9-116">( [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="638d9-116"> (the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="638d9-117">( [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="638d9-117"> (the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="638d9-118">( [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="638d9-118"> (the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="638d9-119">( [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)])，包括[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="638d9-119"> (the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]), including [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="638d9-120">( [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)])，包括[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="638d9-120"> (the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]), including [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="638d9-121">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不適用於 64 位元平台。</span><span class="sxs-lookup"><span data-stu-id="638d9-121">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
 <span data-ttu-id="638d9-122">如果您不已經知道您要使用的方式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在您的公司，建議您一開始會瀏覽功能，以及配接器功能中所述[了解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="638d9-122">If you do not already know how you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] at your company, it is recommended that you start by exploring features and functionality of the adapter described in [Understand BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="638d9-123">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="638d9-123">Next steps</span></span>  
- [<span data-ttu-id="638d9-124">安裝適用於 SAP 的資料提供者的自訂 Rfc</span><span class="sxs-lookup"><span data-stu-id="638d9-124">Install Custom RFCs for the Data Provider for SAP</span></span>](install-custom-rfcs-for-the-data-provider-for-sap.md)
  
-   [<span data-ttu-id="638d9-125">瞭解 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="638d9-125">Understand BizTalk Adapter for mySAP Business Suite</span></span>](understand-biztalk-adapter-for-mysap-business-suite.md)  

- [<span data-ttu-id="638d9-126">完成上 SAP RFC 和 IDOC 工作</span><span class="sxs-lookup"><span data-stu-id="638d9-126">Complete RFC and IDOC tasks on SAP</span></span>](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)
  
-   [<span data-ttu-id="638d9-127">SAP 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="638d9-127">SAP Adapter Tutorials</span></span>](sap-adapter-tutorials.md)  