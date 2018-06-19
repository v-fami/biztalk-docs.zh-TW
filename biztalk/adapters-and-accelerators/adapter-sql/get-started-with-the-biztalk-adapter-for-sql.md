---
title: 開始使用 BizTalk adapter for SQL |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c3b6e36-ddfb-4ede-adf5-b9762231224b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61a2ecd7ae8020865dff7b67fbc57388d1f15af6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222734"
---
# <a name="get-started-with-the-biztalk-adapter-for-sql"></a><span data-ttu-id="f372f-102">開始使用 BizTalk adapter for SQL</span><span class="sxs-lookup"><span data-stu-id="f372f-102">Get started with the BizTalk adapter for SQL</span></span>

  
 <span data-ttu-id="f372f-103">本節提供使用者熟悉 Microsoft 配接器、 必要條件和主題的總覽[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f372f-103">This section provides an overview of the adapter, prerequisites, and topics for users who are new to Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="f372f-104">其中也會討論的功能[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]以及可以使用配接器的 SQL Server 資料庫執行的不同作業。</span><span class="sxs-lookup"><span data-stu-id="f372f-104">It discusses the features of [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] and the different operations that can be performed on the SQL Server database by using the adapter.</span></span>  
  
 <span data-ttu-id="f372f-105">什麼是配接器？</span><span class="sxs-lookup"><span data-stu-id="f372f-105">What is an adapter?</span></span> <span data-ttu-id="f372f-106">配接器是可讓您傳送和接收訊息的特定業務 (LOB) 系統的軟體元件。</span><span class="sxs-lookup"><span data-stu-id="f372f-106">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="f372f-107">配接器的主要設計目的是協助交易夥伴之間的商務文件的交換。</span><span class="sxs-lookup"><span data-stu-id="f372f-107">The primary design goal of an adapter is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="f372f-108">因為每個商務系統可能會遵守特定的文件格式和通訊協定，配接器必須使用的傳遞機制符合普遍認可的標準和通訊協定，來為使用者提供統一的介面。</span><span class="sxs-lookup"><span data-stu-id="f372f-108">Because each business system may adhere to specific document formats and protocols, the adapter must use a delivery mechanism that conforms to commonly recognized standards and protocols to provide a uniform interface to the users.</span></span>  
  
 <span data-ttu-id="f372f-109">中的配接器[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]可以分成兩大類別：</span><span class="sxs-lookup"><span data-stu-id="f372f-109">The adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] can be divided into two broad categories:</span></span>  
  
-   <span data-ttu-id="f372f-110">**LOB 配接器**。</span><span class="sxs-lookup"><span data-stu-id="f372f-110">**LOB adapters**.</span></span> <span data-ttu-id="f372f-111">這類配接器提供的服務導向程式設計模型，以存取 LOB 系統，例如 SAP 或 Siebel 配接器。</span><span class="sxs-lookup"><span data-stu-id="f372f-111">Such adapters provide service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel.</span></span>  
  
-   <span data-ttu-id="f372f-112">**資料配接器**。</span><span class="sxs-lookup"><span data-stu-id="f372f-112">**Data adapters**.</span></span> <span data-ttu-id="f372f-113">這類配接器可提供服務導向程式設計模型，access 資料庫 — 比方說，Oracle 資料庫或 SQL Server 的配接器。</span><span class="sxs-lookup"><span data-stu-id="f372f-113">Such adapters provide service-oriented programming model to access databases—for example, adapters for the Oracle database or SQL Server.</span></span>  
  
 <span data-ttu-id="f372f-114">有五個配接器在[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f372f-114">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="f372f-115"> ([!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="f372f-115"> ([!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f372f-116">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]也會提供外部[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]作為個別的介面卡。</span><span class="sxs-lookup"><span data-stu-id="f372f-116">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is also available outside the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] as a separate adapter.</span></span>  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="f372f-117"> ([!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="f372f-117"> ([!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]).</span></span>  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="f372f-118"> ([!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="f372f-118"> ([!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]).</span></span>  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="f372f-119"> ([!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="f372f-119"> ([!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]).</span></span>  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="f372f-120"> ([!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="f372f-120"> ([!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f372f-121">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不適用於 64 位元平台。</span><span class="sxs-lookup"><span data-stu-id="f372f-121">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
 <span data-ttu-id="f372f-122">如果您不已經知道要如何在您的公司可以使用 SQL 配接器，建議您一開始會瀏覽功能，以及配接器功能中所述[了解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f372f-122">If you do not already know how you want to use the SQL adapter at your company, it is recommended that you start by exploring the features and functionality of the adapter described in [Understand BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f372f-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="f372f-123">In This Section</span></span>  
  
-   [<span data-ttu-id="f372f-124">瞭解 BizTalk Adapter for SQL Server</span><span class="sxs-lookup"><span data-stu-id="f372f-124">Understand BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)  
  
-   [<span data-ttu-id="f372f-125">SQL 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="f372f-125">SQL Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sql/sql-adapter-tutorials.md)  
  
-   [<span data-ttu-id="f372f-126">常見問題集</span><span class="sxs-lookup"><span data-stu-id="f372f-126">Frequently Asked Questions</span></span>](../../adapters-and-accelerators/adapter-sql/sql-adapter-faqs.md)