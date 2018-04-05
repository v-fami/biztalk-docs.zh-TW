---
title: 開始使用 BizTalk Adapter for Siebel eBusiness Application |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, about
ms.assetid: 0867f95f-977f-48bf-8c46-70fd6e4df56b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba067d0479bbcdae6d04c3affdcb9ee60e564cc9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-biztalk-adapter-for-siebel-ebusiness-applications"></a><span data-ttu-id="265d2-102">開始使用 BizTalk Adapter for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="265d2-102">Get started with the BizTalk Adapter for Siebel eBusiness Applications</span></span>
<span data-ttu-id="265d2-103">本節提供使用者熟悉的 Microsoft 配接器、 必要條件和主題的總覽[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="265d2-103">This section provides an overview of the adapter, prerequisites, and topics for users who are new to the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="265d2-104">其中也會討論的功能[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]以及可對使用配接器的 Siebel 系統的不同作業。</span><span class="sxs-lookup"><span data-stu-id="265d2-104">It discusses the features of [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] and the different operations that can be performed on the Siebel system using the adapter.</span></span>  
  
 <span data-ttu-id="265d2-105">什麼是配接器？</span><span class="sxs-lookup"><span data-stu-id="265d2-105">What is an adapter?</span></span> <span data-ttu-id="265d2-106">配接器是可讓您傳送和接收訊息的特定業務 (LOB) 系統的軟體元件。</span><span class="sxs-lookup"><span data-stu-id="265d2-106">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="265d2-107">配接器的主要設計目的是協助交易夥伴之間的商務文件的交換。</span><span class="sxs-lookup"><span data-stu-id="265d2-107">The primary design goal of adapters is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="265d2-108">因為每個商務系統可能會遵守特定的文件格式和通訊協定，配接器必須使用的傳遞機制符合普遍認可的標準和通訊協定。</span><span class="sxs-lookup"><span data-stu-id="265d2-108">Because each business system may adhere to specific document formats and protocols, the adapter must use a delivery mechanism that conforms to commonly recognized standards and protocols.</span></span>  
  
 <span data-ttu-id="265d2-109">配接器可以分成兩大類別：</span><span class="sxs-lookup"><span data-stu-id="265d2-109">The adapters can be divided into two broad categories:</span></span>  
  
-   <span data-ttu-id="265d2-110">**LOB 配接器**。</span><span class="sxs-lookup"><span data-stu-id="265d2-110">**LOB adapters**.</span></span> <span data-ttu-id="265d2-111">這類配接器提供服務導向的程式設計模型存取部署 LOB 系統，例如 SAP 或 Siebel 配接器。</span><span class="sxs-lookup"><span data-stu-id="265d2-111">Such adapters provide a service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel.</span></span>  
  
-   <span data-ttu-id="265d2-112">**資料配接器**。</span><span class="sxs-lookup"><span data-stu-id="265d2-112">**Data adapters**.</span></span> <span data-ttu-id="265d2-113">這類配接器提供服務導向的程式設計模型來存取資料庫 — 比方說，針對 SQL Server 的 Oracle 資料庫配接器。</span><span class="sxs-lookup"><span data-stu-id="265d2-113">Such adapters provide a service-oriented programming model to access databases—for example, an adapter for the Oracle database or SQL Server.</span></span>  
  
 <span data-ttu-id="265d2-114">有五個配接器在[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="265d2-114">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="265d2-115"> ( [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="265d2-115"> (the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="265d2-116"> ( [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="265d2-116"> (the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="265d2-117"> ( [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="265d2-117"> (the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="265d2-118"> ( [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)])，包括[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="265d2-118"> (the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]), including [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="265d2-119"> ( [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)])，包括[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="265d2-119"> (the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]), including [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="265d2-120">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不適用於 64 位元平台。</span><span class="sxs-lookup"><span data-stu-id="265d2-120">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
 <span data-ttu-id="265d2-121">如果您不已經知道您要使用的方式[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在您的公司，建議您一開始會瀏覽功能，以及配接器功能中所述[概觀的 BizTalk 配接器 for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md).</span><span class="sxs-lookup"><span data-stu-id="265d2-121">If you do not already know how you want to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] at your company, it is recommended that you start by exploring the features and functionality of the adapter described in [Overview of BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="265d2-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="265d2-122">In This Section</span></span>  
  
-   [<span data-ttu-id="265d2-123">瞭解 BizTalk Adapter for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="265d2-123">Understand BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md) 
  
-   [<span data-ttu-id="265d2-124">Siebel 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="265d2-124">Siebel Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-siebel/siebel-adapter-tutorials.md)  
  
-   [<span data-ttu-id="265d2-125">社群資源</span><span class="sxs-lookup"><span data-stu-id="265d2-125">Community Resources</span></span>](http://msdn.microsoft.com/library/ff5ec978-8cdd-418a-a25e-fd3746b64d8b)  
  
-   [<span data-ttu-id="265d2-126">常見問題集</span><span class="sxs-lookup"><span data-stu-id="265d2-126">Frequently Asked Questions</span></span>](http://msdn.microsoft.com/library/66953c15-08c5-48ac-a4ff-a72a82174f15)