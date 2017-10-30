---
title: "開始使用 Oracle 資料庫配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, about
- data adapter
- LOB adapter
ms.assetid: ed5b3510-11c4-4b10-bf85-c4066f3f80df
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7aa93ae3f64f4f2f914a51508a3a8dee4e3be41
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-oracle-database-adapter"></a><span data-ttu-id="35fb9-102">開始使用 Oracle 資料庫配接器</span><span class="sxs-lookup"><span data-stu-id="35fb9-102">Get started with the Oracle Database adapter</span></span>
<span data-ttu-id="35fb9-103">本節提供使用者熟悉 Microsoft 配接器、 必要條件和主題的總覽[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="35fb9-103">This section provides an overview of the adapter, prerequisites, and topics for users who are new to Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="35fb9-104">其中也會討論的功能[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]以及可以使用配接器的 Oracle 資料庫執行的不同作業。</span><span class="sxs-lookup"><span data-stu-id="35fb9-104">It discusses the features of [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] and the different operations that can be performed on the Oracle database using the adapter.</span></span>  
  
 <span data-ttu-id="35fb9-105">什麼是配接器？</span><span class="sxs-lookup"><span data-stu-id="35fb9-105">What is an adapter?</span></span> <span data-ttu-id="35fb9-106">配接器是可讓您傳送和接收訊息的特定業務 (LOB) 系統的軟體元件。</span><span class="sxs-lookup"><span data-stu-id="35fb9-106">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="35fb9-107">配接器的主要設計目的是協助交易夥伴之間的商務文件的交換。</span><span class="sxs-lookup"><span data-stu-id="35fb9-107">The primary design goal of adapters is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="35fb9-108">因為每個商務系統可以遵守特定的文件格式和通訊協定，配接器會使用傳遞機制符合普遍認可的標準和通訊協定。</span><span class="sxs-lookup"><span data-stu-id="35fb9-108">Because each business system can adhere to specific document formats and protocols, the adapter uses a delivery mechanism that conforms to commonly recognized standards and protocols.</span></span>  
  
 <span data-ttu-id="35fb9-109">配接器可以分成兩大類別：</span><span class="sxs-lookup"><span data-stu-id="35fb9-109">The adapters can be divided into two broad categories:</span></span>  
  
-   <span data-ttu-id="35fb9-110">**LOB 配接器**。</span><span class="sxs-lookup"><span data-stu-id="35fb9-110">**LOB adapters**.</span></span> <span data-ttu-id="35fb9-111">這類配接器提供服務導向的程式設計模型存取部署 LOB 系統，例如 SAP 或 Siebel 配接器。</span><span class="sxs-lookup"><span data-stu-id="35fb9-111">Such adapters provide a service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel.</span></span>  
  
-   <span data-ttu-id="35fb9-112">**資料配接器**。</span><span class="sxs-lookup"><span data-stu-id="35fb9-112">**Data adapters**.</span></span> <span data-ttu-id="35fb9-113">這類配接器提供服務導向的程式設計模型來存取資料庫 — 比方說，針對 SQL Server 的 Oracle 資料庫配接器。</span><span class="sxs-lookup"><span data-stu-id="35fb9-113">Such adapters provide a service-oriented programming model to access databases—for example, an adapter for the Oracle database or SQL Server.</span></span>  
  
 <span data-ttu-id="35fb9-114">有五個配接器在[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="35fb9-114">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="35fb9-115"> ( [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="35fb9-115"> (the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="35fb9-116"> ( [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="35fb9-116"> (the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="35fb9-117"> ( [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="35fb9-117"> (the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="35fb9-118"> ( [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)])，包括[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="35fb9-118"> (the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]), including [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="35fb9-119"> ( [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)])，包括[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="35fb9-119"> (the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]), including [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35fb9-120">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不適用於 64 位元平台。</span><span class="sxs-lookup"><span data-stu-id="35fb9-120">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
 <span data-ttu-id="35fb9-121">如果您不已經知道您要使用的方式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在您的公司，建議您一開始會瀏覽功能，以及配接器功能中所述[瞭解 BizTalk Adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="35fb9-121">If you do not already know how you want to use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] at your company, it is recommended that you start by exploring the features and functionality of the adapter described in [Understanding the BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md).</span></span>  
  
