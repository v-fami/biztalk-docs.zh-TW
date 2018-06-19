---
title: 開始使用 BizTalk Adapter for Oracle E-business Suite |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 852d5855-c58a-4fa3-8efd-6afea9e527df
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84c149c18da6d08283d0969b89a4634581b0001a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216678"
---
# <a name="get-started-with-the-biztalk-adapter-for-oracle-e-business-suite"></a><span data-ttu-id="809f8-102">開始使用 BizTalk Adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="809f8-102">Get started with the BizTalk Adapter for Oracle E-Business Suite</span></span>
<span data-ttu-id="809f8-103">配接器、 必要條件和主題的 Microsoft BizTalk Adapter Pack 的新使用者的概觀。</span><span class="sxs-lookup"><span data-stu-id="809f8-103">Overview of the adapter, prerequisites, and topics for users who are new to Microsoft BizTalk Adapter Pack.</span></span> <span data-ttu-id="809f8-104">提供功能的相關資訊[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]以及可以執行的 Oracle 資料庫，使用配接器的不同作業。</span><span class="sxs-lookup"><span data-stu-id="809f8-104">Information is provided about the features of [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] and the different operations that can be performed on the Oracle database by using the adapter.</span></span>  
  
## <a name="what-is-an-adapter"></a><span data-ttu-id="809f8-105">什麼是配接器？</span><span class="sxs-lookup"><span data-stu-id="809f8-105">What is an adapter?</span></span>  
  
 <span data-ttu-id="809f8-106">配接器是可讓您傳送和接收訊息的特定業務 (LOB) 系統的軟體元件。</span><span class="sxs-lookup"><span data-stu-id="809f8-106">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="809f8-107">配接器的主要目標是交易夥伴之間的商務文件的交換。</span><span class="sxs-lookup"><span data-stu-id="809f8-107">The primary goal of an adapter is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="809f8-108">因為每個商務系統可能會遵守特定的文件格式和通訊協定，配接器必須使用的傳遞機制符合普遍認可的標準和通訊協定，來為使用者提供統一的介面。</span><span class="sxs-lookup"><span data-stu-id="809f8-108">Because each business system may adhere to specific document formats and protocols, the adapter must use a delivery mechanism that conforms to commonly recognized standards and protocols to provide a uniform interface to the users.</span></span>  
  
 <span data-ttu-id="809f8-109">中的配接器[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]可以分成兩大類別：</span><span class="sxs-lookup"><span data-stu-id="809f8-109">The adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] can be divided into two broad categories:</span></span>  
  
-   <span data-ttu-id="809f8-110">**LOB 配接器**: LOB 配接器提供服務導向的程式設計模型存取部署 LOB 系統，例如 SAP 或 Siebel 應用程式的介面卡。</span><span class="sxs-lookup"><span data-stu-id="809f8-110">**LOB adapters**: LOB adapters provide a service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel applications.</span></span>  
  
-   <span data-ttu-id="809f8-111">**資料配接器**： 資料配接器提供服務導向的程式設計模型來存取資料庫 — 比方說，Oracle 資料庫或 SQL Server 的配接器。</span><span class="sxs-lookup"><span data-stu-id="809f8-111">**Data adapters**: Data adapters provide a service-oriented programming model to access databases — for example, adapters for the Oracle database or SQL Server.</span></span>  
  
 <span data-ttu-id="809f8-112">有五個配接器在[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="809f8-112">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="809f8-113"> ([!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="809f8-113"> ([!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="809f8-114"> ([!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="809f8-114"> ([!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="809f8-115"> ([!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="809f8-115"> ([!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="809f8-116"> ([!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="809f8-116"> ([!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="809f8-117"> ([!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="809f8-117"> ([!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)])</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="809f8-118">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不適用於 64 位元平台。</span><span class="sxs-lookup"><span data-stu-id="809f8-118">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
 <span data-ttu-id="809f8-119">如果您是新手[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，則我們建議您一開始會瀏覽功能和配接器功能中所述[了解 BizTalk Adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="809f8-119">If you are new to the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], then we recommend you start by exploring the features and functionality of the adapter described in [Understand BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="809f8-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="809f8-120">In this section</span></span>  
  
-   [<span data-ttu-id="809f8-121">瞭解 BizTalk Adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="809f8-121">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)  
  
-   [<span data-ttu-id="809f8-122">教學課程： 將資料呈現從 SharePoint 網站上的 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="809f8-122">Tutorial: Presenting data from Oracle E-Business Suite on a SharePoint Site</span></span>](Tutorial:%20Presenting%20Data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)
  
- [<span data-ttu-id="809f8-123">Oracle EBS 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="809f8-123">Troubleshooting the Oracle EBS adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)